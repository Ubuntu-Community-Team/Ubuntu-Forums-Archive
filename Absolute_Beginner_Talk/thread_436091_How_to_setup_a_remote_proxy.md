---
title: "How to setup a remote proxy?"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by threadhead on 2007-05-07
I'm not sure I have the term 'remote proxy' correct, but what I need to do is allow someone from outside my LAN tunnel through my Edgy box to get back on the internet.

My wife's work is instituting a pretty strick internet policy that would eliminate her ability to check her gmail account (and whatnot). So I was thinking I could setup some sort of proxy on my Edgy so that she could surf through it, with an ecnrypted session. There is NO possibility that she can install any VPN software (or any software for that matter) so her only access would have to be using IE. With the connection between her browser and the proxy, there should be little to no chance they could monitor her activity.

I'm sure I not using the terms correctly, but I think you get the idea of what I would like to do.

How do I do it?

---

### Post by tbg58 on 2007-05-07
Actually there are a number of ways you could do this.  A couple of them are:
Set up squid proxy or 
Set up your box as a tor router.

There's a good article on setting up squid proxy here:
[http://www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html](http://www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html)

Tor is here [http://tor.eff.org/index.html.en](http://tor.eff.org/index.html.en)

In order to do this what you will have to do is port forward an incoming port on your router to the proxy port.  You will almost certainly have to use 80, 8080, 81 or 443 as those ports are likely to be open on the firewall where your wife works.  Once you know which open port to use (determined by trial and error from her side) then you forward that port to the incoming port on the proxy server, and tell the proxy server to forward packets out to the port of the requesting http packet.  

Squid is actually set up to be a proxy server from an inside net to an outside one -- TOR is designed to do exactly what you want.

Have a look at the docs on the EFF site linked above and Google TOR for more info.

Hope this helps!
Good luck!
Rob in TN

---

