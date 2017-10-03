# HTML injection at filtering proxy

## Install and build

1. Download and install the Go environment, as at https://golang.org/doc/install
2. Unpack modified version of *redwood* filtering server - *redwood.zip* - to desired location.
3. Get dependencies if needed with `go get ./...`
4. Execute `go build` to compile proxy binary.

## Configure

For selecting where to insert payload in HTML you can set additional flag in config: *injection-place*. If it set to 'head' - the payload will be inserted after first **&lt;HEAD&gt;** tag, otherwise - after first **&lt;BODY&gt;**.

## Run the proxy server

1. Create configuration files for redwood server in */etc/redwood* as usually.
2. Start the proxy server with `./redwood`
3. Check logs in files or at standard output

## Test it works

1. Open a browser and point HTTP proxy settings to the redwood ip:port, configured in */etc/redwood/redwood.conf*
2. In browser go to any http site to check HTML injection applied.
3. A red horizontal banner at the top of opened page will indicate the success. If you have disabled JavaScript in your browser the banner will not appear (because it uses JavaScript payload to render itself) and you have to view page source for injection checking.

## Customize the payload

You can find the payload HTML in **injection/payload.html** subfolder of redwood main folder. 
The payload simply inserted after selected tag in every HTTP response with Content-type containing '**html**', returned by the proxy.
Feel free to modify the payload on your own.


#### At the end

*Any related questions are welcome.
I am open for further cooperation in wide range of IT tasks.*

Best regards,
Alex C.
kazan1000@gmail.com



