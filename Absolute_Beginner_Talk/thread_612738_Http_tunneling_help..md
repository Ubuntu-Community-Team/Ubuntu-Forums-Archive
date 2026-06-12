---
title: "Http tunneling help."
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by gardara on 2007-11-14
I am on a network that has proxy and all ports closed except port 80.

I want to be able to connect to ssh, irc, etc.

I have read that http tunneling is what I need. I have found some windows solutions for http tunneling (example: [http://www.http-tunnel.com/html/](http://www.http-tunnel.com/html/)) but I haven't found anything working for linux.

The closest I have got is proxychains. [http://proxychains.sourceforge.net/](http://proxychains.sourceforge.net/)

I guess proxychains can work but I can't seem to find any servers that I can use with proxychains and I can't find out how I can set up my own server to use with proxychains.

So basically my question is, how can I set up a proxy server for proxychains or is there any other solution available other than proxychains?


Hope someone can help me. Thanks.

---

### Post by ^rooker on 2007-12-13
You probably won't need my answer anymore, but maybe someone else might trip over this thread some day.

First of all:
I don't really like the idea of tunneling things over HTTP, because it's being abused these days to get around lazy IT people who're not doing their job - or who don't know what they're doing. 

This leads to more fascist Cisco routers which actually do a sanity checking on HTTP packets and filter out things like that. Believe me, most of them already do.
I don't like where this is going... 

However, here are some things that have helped me in the past:


1) For HTTP tunneling, **you *always* need an external server** that does the actual connection for you. It's like a satellite, because you can only talk to a specially prepared server listening on port 80 for tunneling requests.

If you don't trust that server, I wouldn't send sensitive information over it (like checking emails, etc...)


2) Since you need an external server anyway, you could simply "bend" your SSH server to also listen on port 443 or 80 (using iptables). Then enable port forwarding in /etc/ssh/sshd_config (I prefer 443, since most routers can't check the encrypted traffic, so they don't figure out that it ain't HTTPS).

In 99% of all firewalling cases you can connect to your SSH server and use default SSH tunneling to connect anywhere (google for "ssh port forwarding" to get infos about how to use it, and what's possible).

The great thing about that is that you can do reverse tunnels! This means that someone can connect to *you* even if you're behind a firewall. I've used this to do remote support for customers.

I'm using this for a few years now, and I love it! If you want a GUI to configure the tunnels, you can use "PuTTY" (runs on Windows and Linux). From the shell, you can just use "ssh -L port_in:host_out:port_out" for outgoing connections or "ssh -R port_in:localhost:port_out" for incoming connections.

---

### Post by Dr Small on 2007-12-13
Use the method:
```
ssh -D 2007 user@remotehost
```

The port number, "2007" can be anything that is not restricted, such as 21, 22, 25, 80, 443, etc. You must have a "remotehost" that has an internet connection and port 22 forwarded on your router (if you have one) and port 22 open on your firewall (for incoming SSH requests.)

You would use the above format from work (for example) and setup your browser to use SOCKS host, on "localhost", port "2007". Then use the proxy in your web browser and everything must pass through your "remotehost", which would then serve as a proxy.

Dr Small

---

