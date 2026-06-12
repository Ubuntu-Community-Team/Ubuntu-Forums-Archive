---
title: "Forward all connections to local proxy"
date: 2008-08-02
forum: Arch and derivatives
---

### Post by Dr Small on 2008-08-02
Greetings there,
I just setup a Squid Cache / Proxy Server and think it is great so far, as it has sped up my connection and I like it. I have Firefox configured to use the proxy server, but I would like to setup my network connection to forward all of my outgoing connections through the proxy server. Is this possible?

I don't want to setup each application to use the proxy server, but have them all transparently pass through the proxy server, just by network connection. If anyone has any information on this, I'll get started reading. I couldn't find anything useful on the Arch Wiki, though.

Dr Small

---

### Post by mips on 2008-08-03
[http://wiki.archlinux.org/index.php/NAT%27ing_firewall_-_Share_your_broadband_connection](http://wiki.archlinux.org/index.php/NAT%27ing_firewall_-_Share_your_broadband_connection)
[http://wiki.archlinux.org/index.php/NAT%27ing_firewall_-_Adding_advanced_features](http://wiki.archlinux.org/index.php/NAT%27ing_firewall_-_Adding_advanced_features)

Keep in mind that what can be done to http traffic can just as easily be applied to ALL traffic.

---

### Post by Dr Small on 2008-08-03
Thanks for those links, mips.

So, I have Squid setup on my Server (running Ubuntu), and I need to setup Squid and Shorewall on my Arch box, and do as directed under the 'Transparency' subtitle on the wiki. Correct?

---

### Post by mips on 2008-08-03
I have not used squid/proxy before but logic dictates that you will only install this on your server. The other machines will use this box as a router/firewall/proxy/cache device.

Your desktop will use this server without any additional configs except for specifying it as the default gateway. You will have to change you addressing structure a bit.

Have a look at this, [http://ubuntuforums.org/showthread.php?t=111972](http://ubuntuforums.org/showthread.php?t=111972) you would basically just build on that for proxy&cache.

---

### Post by Dr Small on 2008-08-03
I am slowly getting somewhere, but it isn't quite working yet. In my /etc/shorewall/rules I have:
```

DNAT	fw		lan:192.168.0.70:3128		tcp	80	

```

My LAN IP is 192.168.0.16
My Server IP running Squid is 192.168.0.70
The port that Squid is listening on is 3128

I then ran:
```
sudo shorewall start
```

Shorewall started, I went to Firefox, attempted to load UbuntuForums and got a "Invalid Request" error from Squid. So, it is forwarding my connection, but is messing it up somehow and Squid is giving me an error, now.

Squid Says:
```
The following error was encountered:

    * Invalid Request 

Some aspect of the HTTP Request is invalid. Possible problems:

    * Missing or unknown request method
    * Missing URL
    * Missing HTTP Identifier (HTTP/1.0)
    * Request is too large
    * Content-Length missing for POST or PUT requests
    * Illegal character in hostname; underscores are not allowed 
```

---

### Post by Dr Small on 2008-08-04
I'm scratching this idea. It would have been simple had my server been between the modem and the router, acting as a firewall and I had Shorewall anhd Squid on the same system, but what I am attempting seems to difficult, and I never could get it to work properly.

So rather than leaving this Thread [UnSOLVED], I'll just end it.

Dr Small

---

