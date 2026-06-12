---
title: "Anonymous IP"
date: 2006-01-06
forum: Absolute Beginner Talk
---

### Post by Connollyir on 2006-01-06
Does anyone know of a good ip anonymization program or similar firewall suite for KUbuntu? I'm looking for something that would allow me to surf the web with others not seeing my ip or having a random ip every time my computer contacts a server for information. I am pretty fuzzy on the concepts, I mainly don't want anyone to be able to trace things back to my computer - sort of a security quirk of mine. 

Any help on what I should be doing if there aren't any programs for it is appreciated.

-Ian

---

### Post by matthew on 2006-01-06
I recommend reading this. It should do what you want.

[http://www.ubuntuforums.org/showthread.php?t=10825](http://www.ubuntuforums.org/showthread.php?t=10825)

---

### Post by Connollyir on 2006-01-06
[QUOTE=matthew]I recommend reading this. It should do what you want.

[http://www.ubuntuforums.org/showthread.php?t=10825](http://www.ubuntuforums.org/showthread.php?t=10825)[/QUOTE]

It says at the bottom of the post-install message that it is an experimental software and warns against relying on it for strong anonymity. Do you know of anything slightly more proven or commercial grade?

-Ian

---

### Post by Connollyir on 2006-01-07
Well I've got mild ADD (right) and I went ahead and installed it - it works pretty well except that I have to configure EVERY program I want to use the proxys - which is a royal pain and not as secure as I would like (if I am wrong in this please correct me). I would rather have a program that did it automatically for all ports and all connections, which allowed me to specify which programs would NOT  use it's protection. Also I don't think certain programs (bit tornado being what I just tried) don't give you the option to specify where the connections are coming from, and if I need to manually set up these programs like I believe I may, then this solution will not work for me.

Any ideas?


-Ian

---

### Post by newuser111 on 2006-01-07
you usually do have to manually configure programs to use proxies both in windows and linux, I have never heard of any program for linux but there is SocksCap for windows that uses socks proxies to route all internet traffic of a program through a socks proxy, i dont know if there is something similar for linux

---

### Post by cwaldbieser on 2006-01-07
[QUOTE=Connollyir]Well I've got mild ADD (right) and I went ahead and installed it - it works pretty well except that I have to configure EVERY program I want to use the proxys - which is a royal pain and not as secure as I would like (if I am wrong in this please correct me). I would rather have a program that did it automatically for all ports and all connections, which allowed me to specify which programs would NOT  use it's protection. Also I don't think certain programs (bit tornado being what I just tried) don't give you the option to specify where the connections are coming from, and if I need to manually set up these programs like I believe I may, then this solution will not work for me.

Any ideas?


-Ian[/QUOTE]

What you want to do is run Privoxy as a transparent proxy.  However, from the FAQ:
> 
3.18. Can Privoxy run as a "transparent" proxy?

No, Privoxy currently does not have this ability, though it is planned for a future release. Transparent proxies require special handling of the request headers beyond what Privoxy is now capable of.

Chaining Privoxy behind another proxy that has this ability should work though. See the forwarding chapter in the user manual. As a transparent proxy to be used for chaining we recommend Transproxy ([http://www.transproxy.nlc.net.au/)](http://www.transproxy.nlc.net.au/)).


Many apps respect the HTTP_PROXY and FTP_PROXY environment variables for those protocols.  For others, you will need to do manual configuration.

---

### Post by Connollyir on 2006-01-07
[QUOTE=cwaldbieser]What you want to do is run Privoxy as a transparent proxy.  However, from the FAQ:


Many apps respect the HTTP_PROXY and FTP_PROXY environment variables for those protocols.  For others, you will need to do manual configuration.[/QUOTE]

In your quote, it said that privoxy can be chained behind a transparent proxy which would provide the capabilities that I need. What are my options for a transparent proxy with Ubuntu?

---

### Post by cwaldbieser on 2006-01-08
[QUOTE=Connollyir]In your quote, it said that privoxy can be chained behind a transparent proxy which would provide the capabilities that I need. What are my options for a transparent proxy with Ubuntu?[/QUOTE]
I am not exactly an expert with regards to transparent proxies, but I believe this HOWTO will explain what a transparent proxy is:
[http://www.tldp.org/HOWTO/TransparentProxy.html]("http://www.tldp.org/HOWTO/TransparentProxy.html")

The section that should interest you the most is
[http://www.tldp.org/HOWTO/TransparentProxy-6.html]("http://www.tldp.org/HOWTO/TransparentProxy-6.html")
This section explains how you would proxy to a remote machine.  You basically want to do this (the anonymizer is the remote proxy).

Basically, it involves setting up some "iptables" commands.  iptables is the comand line interface to your firewall.  If you need some help understanding it, I can try to help.

---

### Post by Connollyir on 2006-01-08
[QUOTE=cwaldbieser]I am not exactly an expert with regards to transparent proxies, but I believe this HOWTO will explain what a transparent proxy is:
[http://www.tldp.org/HOWTO/TransparentProxy.html]("http://www.tldp.org/HOWTO/TransparentProxy.html")

The section that should interest you the most is
[http://www.tldp.org/HOWTO/TransparentProxy-6.html]("http://www.tldp.org/HOWTO/TransparentProxy-6.html")
This section explains how you would proxy to a remote machine.  You basically want to do this (the anonymizer is the remote proxy).

Basically, it involves setting up some "iptables" commands.  iptables is the comand line interface to your firewall.  If you need some help understanding it, I can try to help.[/QUOTE]

So essentially it looks like I need to setup a seperate box running as a proxy server to keep the government - or anyone else for that matter - from seeing what I'm doing on the net? The way I understand it, this box would access the web through a list of proxy servers that I designate and through this it would hide my ip address? How secure is this method and could a dedicated person eventually get my ip and in turn my isp and more pertinent info? How much is this going to slow down my connection and are there faster alternatives to what I want (essentially surfing the web anonymously as previously stated and downloading various files and data which are not copywrighted)?

Also as a side question - if I set this proxy box up would I be able to run an FTP server from it as well? The reason I ask is because I have a dedicated FTP server that gives out media on my personal network and I would still want to be able to access it while running as the proxy.

Thanks

-Ian

---

### Post by cwaldbieser on 2006-01-08
[QUOTE=Connollyir]So essentially it looks like I need to setup a seperate box running as a proxy server to keep the government - or anyone else for that matter - from seeing what I'm doing on the net? The way I understand it, this box would access the web through a list of proxy servers that I designate and through this it would hide my ip address? How secure is this method and could a dedicated person eventually get my ip and in turn my isp and more pertinent info? How much is this going to slow down my connection and are there faster alternatives to what I want (essentially surfing the web anonymously as previously stated and downloading various files and data which are not copywrighted)?

Also as a side question - if I set this proxy box up would I be able to run an FTP server from it as well? The reason I ask is because I have a dedicated FTP server that gives out media on my personal network and I would still want to be able to access it while running as the proxy.

Thanks

-Ian[/QUOTE]

Actually, you don't need a seperate box-- it just seems like that is the typical situation because you get the most benefit out of transparent proxying if you have a lot of PCs behind a gateway that need to use the proxy.

Imagine you have 100 PC that need Intenet access in your oganization, and you want to configure them all to use a a Squid web-proxy.

Now you could go around to every PC and set the web proxy settings to point to the Squid proxy server.  Or you can just configure your Internet gateway to do the transparent proxying for you.

Now in your case, the proxy server is not a machine on your local network-- when you manually set your proxy settings they point to some remote host that does the IP anonymizing.  You could just as easily (in theory) configure your Ubuntu system to redirect all outgoing traffic to the proxy server.  In practice, I have never actually tried this, but it does mostly make sense to me.

It is no more or less private than manually setting your proxies.  The main difference is that when you set a proxy in an application like Firefox you are working at a higher OSI layer than if you set the proxy via iptables or ip routing policies.

I think you could set up a second machine to act as a gateway and an FTP server, but I don't know if that is necessarily the best layout.  That is a little beyond my current level of expertise.

The simplest way I can think to explain how it works is with an web browsing example:
You want to browse [http://www.google.com/index.html](http://www.google.com/index.html), so you type it into your browser.  Normally, your browser sends an HTTP request to the [www.google.com](www.google.com) host.  The HTTP request is represented as a bunch of TCP/IP packets that have a source IP address of your host, and a destination IP address of the [www.google.com](www.google.com) host.  When the google host receives the packets, it reassembles them into the HTTP request, and passes it on to the web server software.  The web server understands the HTTP message and sees the user-agent (your browser) requested an HTTP GET for the page index.html.  It sends an HTTP response back to your host.  The HTTP response is broken down into TCP/IP packets with source IP addresses of the [www.google.com](www.google.com) host, and destination addresses of your host.  Your host reassembles the packets into the HTTP response and passes it to your browser.  Your browser renders the response.

Now with the transparent proxy setup, a new wrinkle is added.  We start out the same.  he HTTP request is represented as a bunch of TCP/IP packets that have a source IP address of your host, and a destination IP address of the [www.google.com](www.google.com) host.  However, you have rigged your machine in such a way as to manipulate the normal packet routing flow.  Your host's internal routing machinery will modify the packet destinations so they go to the anonymizing proxy server.  When the proxy host receives the packets, it reassembles them into the HTTP request and passes it to the proxy software.  The proxy software recognizes the HTTP request wants a page from [www.google.com](www.google.com), so it resends the request, disassembling it into TCP/IP packets.  The packets have a destination IP address of the [www.google.com](www.google.com) host.  Further, the packets have a source IP address of the proxy.

When the google host receives the packets, it reassembles them into the HTTP request, and passes it on to the web server software.  The web server understands the HTTP message and sees the user-agent (your browser) requested an HTTP GET for the page index.html.  It sends an HTTP response back to the proxy host.  The HTTP response is broken down into TCP/IP packets with source IP addresses of the [www.google.com](www.google.com) host, and destination addresses of the proxy host.  The proxy receives the packets, reassembles them, and passes them to the proxy software.  The proxy software passes the request back to your host and then promptly forgets your IP address.  The request is again disassembled-reassembled and your browser gets the response.

There is really a lot of addressing and re-addressing going on at two different levels, so it is a little confusing to explain how it works any simpler.  I hope that makes some sense.

---

### Post by Connollyir on 2006-01-09
[QUOTE=cwaldbieser]Actually, you don't need a seperate box-- it just seems like that is the typical situation because you get the most benefit out of transparent proxying if you have a lot of PCs behind a gateway that need to use the proxy.

Imagine you have 100 PC that need Intenet access in your oganization, and you want to configure them all to use a a Squid web-proxy.

Now you could go around to every PC and set the web proxy settings to point to the Squid proxy server.  Or you can just configure your Internet gateway to do the transparent proxying for you.

Now in your case, the proxy server is not a machine on your local network-- when you manually set your proxy settings they point to some remote host that does the IP anonymizing.  You could just as easily (in theory) configure your Ubuntu system to redirect all outgoing traffic to the proxy server.  In practice, I have never actually tried this, but it does mostly make sense to me.

It is no more or less private than manually setting your proxies.  The main difference is that when you set a proxy in an application like Firefox you are working at a higher OSI layer than if you set the proxy via iptables or ip routing policies.

I think you could set up a second machine to act as a gateway and an FTP server, but I don't know if that is necessarily the best layout.  That is a little beyond my current level of expertise.

The simplest way I can think to explain how it works is with an web browsing example:
You want to browse [http://www.google.com/index.html](http://www.google.com/index.html), so you type it into your browser.  Normally, your browser sends an HTTP request to the [www.google.com](www.google.com) host.  The HTTP request is represented as a bunch of TCP/IP packets that have a source IP address of your host, and a destination IP address of the [www.google.com](www.google.com) host.  When the google host receives the packets, it reassembles them into the HTTP request, and passes it on to the web server software.  The web server understands the HTTP message and sees the user-agent (your browser) requested an HTTP GET for the page index.html.  It sends an HTTP response back to your host.  The HTTP response is broken down into TCP/IP packets with source IP addresses of the [www.google.com](www.google.com) host, and destination addresses of your host.  Your host reassembles the packets into the HTTP response and passes it to your browser.  Your browser renders the response.

Now with the transparent proxy setup, a new wrinkle is added.  We start out the same.  he HTTP request is represented as a bunch of TCP/IP packets that have a source IP address of your host, and a destination IP address of the [www.google.com](www.google.com) host.  However, you have rigged your machine in such a way as to manipulate the normal packet routing flow.  Your host's internal routing machinery will modify the packet destinations so they go to the anonymizing proxy server.  When the proxy host receives the packets, it reassembles them into the HTTP request and passes it to the proxy software.  The proxy software recognizes the HTTP request wants a page from [www.google.com](www.google.com), so it resends the request, disassembling it into TCP/IP packets.  The packets have a destination IP address of the [www.google.com](www.google.com) host.  Further, the packets have a source IP address of the proxy.

When the google host receives the packets, it reassembles them into the HTTP request, and passes it on to the web server software.  The web server understands the HTTP message and sees the user-agent (your browser) requested an HTTP GET for the page index.html.  It sends an HTTP response back to the proxy host.  The HTTP response is broken down into TCP/IP packets with source IP addresses of the [www.google.com](www.google.com) host, and destination addresses of the proxy host.  The proxy receives the packets, reassembles them, and passes them to the proxy software.  The proxy software passes the request back to your host and then promptly forgets your IP address.  The request is again disassembled-reassembled and your browser gets the response.

There is really a lot of addressing and re-addressing going on at two different levels, so it is a little confusing to explain how it works any simpler.  I hope that makes some sense.[/QUOTE]

Well thats good news - I can do this on my current machine. I really didn't want to have to try and fund another box since my budget is strained enough as it is (college student).

I understant the concepts of transparent proxies well enough, I am just unsure of how to implement them through my software and hardware.

Now the question is how do I set up iptables in Ubuntu and configure it to redirect to a proxy? I read the howtos that you posted earlier, and maybe perhaps I (very possibly) may have missed something, but I have some questions for how to do this in Ubuntu. Firstly, I need to install squid on my machine and then configure iptables which should create the transparency environment I redirect traffic through correct? Or do I not need squid at all and I should just use iptables? Secondly, do I need to do something special to get Ubuntu to run through this setup or will iptables do it for me (like is manual web browser configuration necissary because many of my applications seemingly have no way to configure them to run through a proxy (or perhaps thats just a gui thing and I can do it manually through the conf file?))? 

Oh and you said that the proxy "forgets" my ip after it handles my information, but is there a log of my ip created on the proxy that sticks? As in could somone find it after I had been there and track the data I asked for?

I don't imagine there a wiki or howto that is slightly more verbose or designed with Debian/Ubuntu in mind? Because that would be sweet, if improbable.

Thanks

-Ian

---

### Post by cwaldbieser on 2006-01-09
[QUOTE=Connollyir]Well thats good news - I can do this on my current machine. I really didn't want to have to try and fund another box since my budget is strained enough as it is (college student).

I understant the concepts of transparent proxies well enough, I am just unsure of how to implement them through my software and hardware.

Now the question is how do I set up iptables in Ubuntu and configure it to redirect to a proxy? I read the howtos that you posted earlier, and maybe perhaps I (very possibly) may have missed something, but I have some questions for how to do this in Ubuntu. Firstly, I need to install squid on my machine and then configure iptables which should create the transparency environment I redirect traffic through correct? Or do I not need squid at all and I should just use iptables? Secondly, do I need to do something special to get Ubuntu to run through this setup or will iptables do it for me (like is manual web browser configuration necissary because many of my applications seemingly have no way to configure them to run through a proxy (or perhaps thats just a gui thing and I can do it manually through the conf file?))? 

Oh and you said that the proxy "forgets" my ip after it handles my information, but is there a log of my ip created on the proxy that sticks? As in could somone find it after I had been there and track the data I asked for?

I don't imagine there a wiki or howto that is slightly more verbose or designed with Debian/Ubuntu in mind? Because that would be sweet, if improbable.

Thanks

-Ian[/QUOTE]

You don't need squid-- that is just a common proxy situation used in the examples.  The proxy you want to use is whatever you have been manually setting your web browser proxy to.  

Concerning the anonimity provided, I am not exactly sure how Tor and Privoxy work--  I beileve they each play different roles.  From my understanding, Tor is the IP anonymizer, and it forwards your traffic on to the Tor servers.  So if those servers could record your IP address for later use, I guess it could be used to find out who you are.  You would have to talk to someone with more in depth knowledge of the actual software.

As far as getting the iptables stuff to run, you should just create a startup script to run the commands to add the rules to your firewall.  It could be as simple as this:
```

#!/bin/bash

sudo iptables -t nat -A POSTROUTING -o eth0 -p tcp --dport 80 -j REDIRECT --to-port 8118

```
That says, "For any packet that is going to leave your computer on network interface eth0 and is bound for port 80 (web traffic), redirect it to the local machine, port 8118 (the Privoxy port).

(After reading the Privoxy example a little more closely, it looks like the proxy runs locally on your host and forwards it to the Tor server-- yet another inderection!)

Anyway, you can add similar rules for other types of traffic, and forward them to the Tor port.  To run the script at startup, you can put it in /etc/init.d, and then use the "update-rc.d" command to add it as one of the system services.

---

### Post by j-strap2 on 2006-01-14
privoxy just filters the HTTP traffic - it blocks most ads and some of the dodgy active content coming to your browser; it also filters the headers that your browser sends out, such as the referring website. Privoxy is highly configurable.

tor is an anonymising proxy chain - your connection is encrypted locally and forwarded randomly between several nodes in the tor network before being decrypted and exiting at the 'exit node'. The remote web server cannot see your web address and it would be difficult for anyone to trace the connection.

---

### Post by Connollyir on 2006-01-15
[QUOTE=cwaldbieser]You don't need squid-- that is just a common proxy situation used in the examples.  The proxy you want to use is whatever you have been manually setting your web browser proxy to.  

Concerning the anonimity provided, I am not exactly sure how Tor and Privoxy work--  I beileve they each play different roles.  From my understanding, Tor is the IP anonymizer, and it forwards your traffic on to the Tor servers.  So if those servers could record your IP address for later use, I guess it could be used to find out who you are.  You would have to talk to someone with more in depth knowledge of the actual software.

As far as getting the iptables stuff to run, you should just create a startup script to run the commands to add the rules to your firewall.  It could be as simple as this:
```

#!/bin/bash

sudo iptables -t nat -A POSTROUTING -o eth0 -p tcp --dport 80 -j REDIRECT --to-port 8118

```
That says, "For any packet that is going to leave your computer on network interface eth0 and is bound for port 80 (web traffic), redirect it to the local machine, port 8118 (the Privoxy port).

(After reading the Privoxy example a little more closely, it looks like the proxy runs locally on your host and forwards it to the Tor server-- yet another inderection!)

Anyway, you can add similar rules for other types of traffic, and forward them to the Tor port.  To run the script at startup, you can put it in /etc/init.d, and then use the "update-rc.d" command to add it as one of the system services.[/QUOTE]

Ok this is simple. But how would I find out what ports are designated for what? You just told me that port 80 is designated for web traffic - does this include Bit Tornado, Limewire and Gaim? I imagine there are seperate ports for that but in order to forward traffic from them I need to know what they are.

-Ian

---

### Post by Connollyir on 2006-01-15
[QUOTE=j-strap2]privoxy just filters the HTTP traffic - it blocks most ads and some of the dodgy active content coming to your browser; it also filters the headers that your browser sends out, such as the referring website. Privoxy is highly configurable.

tor is an anonymising proxy chain - your connection is encrypted locally and forwarded randomly between several nodes in the tor network before being decrypted and exiting at the 'exit node'. The remote web server cannot see your web address and it would be difficult for anyone to trace the connection.[/QUOTE]

You seem pretty confident in your knowledge of privoxy and tor. If you don't mind me asking, what is your experience with them? I am trying to get reliable information about them together so I don't get myself in trouble and only a few people have spoken up on the subject:D .

---

### Post by cwaldbieser on 2006-01-15
[QUOTE=Connollyir]Ok this is simple. But how would I find out what ports are designated for what? You just told me that port 80 is designated for web traffic - does this include Bit Tornado, Limewire and Gaim? I imagine there are seperate ports for that but in order to forward traffic from them I need to know what they are.

-Ian[/QUOTE]
Well for common ports (ftp, http, https), most are listed in /etc/services.  For particular applications that use their own protocols, I would just Google for "<appname> port".  Also, sometimes the docs for the app will tell you what ports you need to open for your firewall.

---

### Post by j-strap2 on 2006-01-15
Connollyir: TOR is still considered to be in the testing phase by the developers. 

It works pretty well although it is slow because the data has to be routed through a series of servers and then out through an exit node. Exit nodes are provided by generous users who have available bandwidth and the balls to take any flack arising from misuse of the TOR network.

TOR does a good job of encrypting the traffic from your PC to the TOR network. If set up properly, your ISP sees only encrypted traffic - it can't see where you are surfing. TOR also disguises the final connection to the web server so that it cannot trace the connection back to you. It is this last part that someone may work out how to crack. The TOR team are pretty good and I reckon it would take a lot of resources to crack the network, but you never know.

You need to use privoxy with TOR because most applications don't connect directly to TOR properly (TOR uses the SOCKS proxy protocol). Unless you use privoxy as well, your web browser will route traffic through TOR but at the same time will leak DNS requests. Hence, your ISP will see the TOR encrypted traffic together with DNS requests for whatever sites you are visiting.

There are a couple of threads on the forums on setting up TOR and privoxy.

---

