---
title: "Bittorrent on Restricted Ports"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by dchang on 2006-11-17
Hey, 

I need to run Ktorrent on a restricted internet. Im on a campus with a fast connection, but many of my ports are blocked. 

I am certain that the following ports are open:
21, 22, 80, 443, 8080.

I know that the following are blocked:
20, 23, 24, 53, 110, 1080, 3128, 6969, 6881-6999, 8000 and assuming that all other ports not listed are also blocked.

Is it possible to route all my bittorrent traffic through one of my open ports (such as port 80)?

---

### Post by Scorchin on 2007-01-12
Anybody have any idea on how to do this? As my university also blocks the use of BitTorrent, leading to downloads of around 1-2kb/s for when i download files such as new ubuntu distro's.

---

### Post by eminn3m on 2007-02-01
You would have to go about it through a proxy.
**[SIZE="5"]Can I use BitTorrent with a proxy server?[/SIZE]**(taken from [http://btfaq.com/serve/cache/26.html](http://btfaq.com/serve/cache/26.html))


"First, note that there are two types of connections that the BitTorrent program must make:

    * Outbound HTTP connections to the tracker, usually on port 6969.
    * Inbound and outbound connections to the peer machines, usually on port 6881 and up.

A web proxy can only be used for the first type of connection, since the second type is not HTTP. Theoretically, you could use the HTTP CONNECT command to tunnel them through an HTTP proxy, but this would require additional code support in the client. There is a possible workaround for this scenario, however; see the final point below.

That having been said, here is how to configure an HTTP proxy for the tracker connections:

    * If the proxy does not require authorization, the system-wide proxy configuration should work. For Windows, open the Control Panel select Internet Options, click on the Connections tab, select your connection and click Settings... (or Lan Settings... if you have a direct connection.) Make sure the Use a proxy server option is selected and enter the proxy's address and port.
    * If your proxy requires basic authorization, set the http_proxy environment variable to [http://username:password@hostname:port](http://username:password@hostname:port), where username and password are your login and password, and hostname:port is the address and port of the proxy server. If you don't know how to set environment variables, there are instructions for Windows on this page by Mike Ravkine (krypt).
    * If your proxy requires NTLM authorization (a Microsoft-proprietary scheme), you may have to use a third party program. Fortunately there is a utility called NTLM Authorization Proxy Server. It is a program you run on your local machine that acts as a proxy for your proxy. In other words, it takes the (unauthenticated) proxy requests from the application (BitTorrent) and forwards them on to your organization's proxy, adding the necessary NTLM authorization. It is written in Python and available as source, so you must install Python on your computer before running it. Refer to the home page for more information.
    * If you are in a firewalled environment where NO outbound connections are allowed except those through an HTTP proxy, you will have difficulty using BitTorrent. One method which might work is as follows: The desproxy program can serve as a SOCKS 4 or 5 server than tunnels requests through the proxy server. Then use SocksCap to "socksify" (intercept the network calls and redirect them to the SOCKS server) the BitTorrent program. See below for a few notes about SocksCap. Note: If you get this method to work, please report your steps and results so that I can improve this part of the FAQ. Thanks."

Hope this works

---

### Post by Pugwash on 2007-02-01
I use the web proxy on our uni network for bittorrent, its worked quite well so far.

---

