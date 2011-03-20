# connect_json

Support for parsing JSON requests and sending JSON responses in [Connect](http://senchalabs.github.com/connect/)

## Example

server.mv

    import connect, connect_json
    connect()
      .use(connect_json)
      .use(^(req, res) {
        response = { hello: 'world' }
        if (req.message)
          response.message = req.message
        res.endJSON response
      })
      .listen 3000

We start the server and send a POST request with curl:

    $ move server.mv &
    $ curl -d '{"foo":"bar"}' -H 'Content-type: application/json' localhost:3000
    {"hello":"world","message":{"foo":"bar"}}


## MIT license

Copyright (c) 2011 Rasmus Andersson <http://rsms.me/>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
