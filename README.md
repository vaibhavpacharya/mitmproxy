# Monitor iOS/Android Network Calls using mitmproxy

## How Mitmproxy works

![Mitmproxy logo](https://miro.medium.com/max/1400/1*zOts8iuiXAzPkMHD1fA1gw.jpeg)

Mitmproxy sits in the middle of connection(classic man in the middle) between your phone/computer and the internet.
We are going to look at the flow of traffic between our favorite app and the internet on large.
App sends information to Mitmproxy and then tell Mitmproxy to send all information to the internet at large, which will then send back information and on and on. Your phone and computer send information to a router which in turn directs it to the company’s servers or mobile app you are trying to interact with. Mitmproxy decrypts SSL encrypted or HTTPS traffic for you to see. The traffic is sent in packets. Mitmproxy unencrypts it for us by installing a certificate on your phone or computer such that is sends Mitmproxy the information which is easy to understand from a user’s perspective.


## Installation

For folks using a mac machine, it’s a delight to set up mitmproxy and get it up and running.
Mitmproxy can be installed easily using Homebrew.
If you don’t have homebrew set up open the terminal and paste the following :

```sh
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

Wait for the installation to be completed.
Install mitmproxy using :

```sh
brew install mitmproxy
```

Once the above step is done type mitmproxy in terminal window

![Terminal logo](https://miro.medium.com/max/1400/1*1SLJU-4_9XWE3mH0g6FgCw.png)

On a Mac Machine Go to **System Preference → Network**. On the left side, you can find which network is working wifi or you are connected to a wired network. It is recommended that you use wifi. Unplug the ethernet if you are connected to a wired network.

Click on **Advance** and click on **TCP/IP** tab. Check out the image for reference.

![Terminal logo](https://miro.medium.com/max/800/1*ABEDRBOLX6xPy9v4FglIVA.jpeg)

You’ll need the highlighted IPv4 address.

**Setting up your iPhone**

1. First, we need to send iPhone’s information to your computer.
2. Go to Settings → Wi-Fi and click on the blue “i” next to the name of the network your iPhone is connected to then scroll Down to HTTP PROXY
3. Tap on Configure Proxy and Select manual. Use the Ipv4 address as server address and port as 8080(mitm proxy works on 8080 as default)


![Terminal logo](https://miro.medium.com/max/562/1*xbqLNcyK6srXTR0oE0zDcQ.jpeg)

4. Start mitmproxy on your Mac's terminal. On your iPhone launch safari and in address bar type address mitm.it

![Terminal logo](https://miro.medium.com/max/562/1*wbDYSQAObL9b0EQRKGyEAw.jpeg)

5. Select Apple and install the certificate. To verify go to Settings → General → Profile (iOS 11) and Settings → General → Device Management on iOS 9 and above devices.

We are almost there, to finish Navigate to Settings → General → About → Certificate Trust Settings. (iOS 10 and above devices). Turn on the toggle button to trust the mitm root certificate.
Horray! we are all good and ready to roll !.

![Terminal logo](https://miro.medium.com/max/1400/1*Lr71EXYwdzKBGKJET5HZIg.png)

You should see something like this on your computer while browsing your favorite app which should show HTTP and HTTPS packets. No HTTPS means you have problems with your certificate installation and no packets at all could indicate a problem with your network settings.

**Setting up your Android Phone.**


1. For Android, you’ll have to navigate to Settings → WiFi. Long press on network name and tap on Modify network.(Depends upon the device you are using)

![Terminal logo](https://miro.medium.com/max/500/1*IDNWJBjsTNS3j34tOpo_dw.jpeg)

2. Next step is to change the Proxy Settings. Tap on Show Advance options and you’ll find Host Name, Port. Use the same information as we did when setting up the iPhone.
3. Open your favorite browser(Chrome) on your Android and address bar type address mitm.it. This is similar to what we did on Safari while setting up the iPhone.
4. Open the certificate, as a security measure Android OS prompts you to set up a pin/pattern if not set before. Refer to screenshot. You might want to save it with a name. In my case, i saved it with mitm.

![Terminal logo](https://miro.medium.com/max/500/1*W5-Ifya7feZ7DL-CDxkDCw.jpeg)

Now you should now be able to see traffic starting to appear in your terminal. I am using Box app in my case to monitor http traffic.

Few Pointers :
If you hit ENTER on any request, you can see more information such as request and response headers.
You can use TAB to switch between Request, Response and Detail tabs.
Hit q to go back to the request list.


## License

MIT

**Free Software, Hell Yeah!**
