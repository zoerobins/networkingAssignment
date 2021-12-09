# Advanced Networking - HTTP Assignment (Option 1)

### Assignment brief

(a) Write a small web server which takes URLs of the form "http://hostname:port/{add,subtract,multiply,divide}/x/y" and prints the result as a single text/plain result.  So the URL http://hostname:port/add/5/7 will return a response like:

`HTTP/1.1 200 OK`  
`Content-Type: text/plain`

`12`

Any invalid URL should return an appropriate error code.

(b) Extend your code to instead of taking a URL containing the expression, instead take JSON via a POST operation.  For example:
`{  
  "operation": "add",  
  "arguments": [ 4, 6 ]  
}`
should return:  

`HTTP/1.1 200 OK`  
`Content-Type: application/json`

`{
  "result": 10
}`  

using JSON as a the response as well.  Again, it should return appropriate error codes if the input is invalid.   
  

### Implemented solution & language

This solution is implemented using Python's HTTPServer and BaseHTTPRequestHandler libraries. I chose to use Python to implement this due to the useful libraries provided and as I have strong experience of programming in Python.   

The solution is comprised of one class, 'handler', and three methods, '_set_headers', 'do_GET' and 'do_POST'.   

`_set_headers()` is used to set the headers for the HTTP response, including the response code and content type.  

`do_GET()` breaks down the URL input into it's components (the operation and arguments) and checks if these are valid/acceptable inputs before calculating the result. If an error occurs, the HTTP response code is set to 400 for a bad request. This method then outputs the response within the browser including the response code, content type and calculation result if this was successfully calculated.  

`do_POST()` checks that the input received is in the JSON format and breaks this input down into it's components, checking that they are valid/acceptable before calculating the result. If an error occurs, the HTTP response code is set to 400 for a bad request. This method then outputs the response in JSON format including the response code, content type and calculation result if this was successfully calculated.
  

### Learning points

As a result of completing this assignment I have learnt how to implement a basic HTTP server using Python and how to handle incoming HTTP requests in a variety of forms (i.e. from a URL and from JSON). Having never used Python to create a HTTP server before this was a good learning experience and something which will be useful in future work. In addition, working with JSON formats for the first time required me to carry out some research into how best to handle this kind of input.


### Running the program

Part (a) is run by first running the Python script and using a web browser to enter the URL. The HTTP response is then displayed in the web page in the browser.  

Part (b) is run by first running the Python script and then using a command line to enter the JSON input which is taken via the POST expression. The HTTP JSON response is then displayed in the command line.  

