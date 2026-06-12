---
title: "LAMP Server on Ubuntu Desktop 7.10 Connection Randomly Drops Out!"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by iSplicer on 2008-03-03
Hey all!

I recently got A LAMP stack running on my Ubuntu Desktop, and it is configured and working fine. SSH is working, and I am using it to access my server from my main PC. Apache is listening on port 88, and everything is working fine - everything loads fast, no problems.

Except one.

While I am enjoying my world of absolute Bliss lost in the world of Linux Webservers and all their glory, the connection just drops. Just like that. I am mainly hosting a phpBB forum on my server, I just cant load any pages for a few minutes. Later, it continues at top speed. This keeps repeating. My SSH terminal freezes from time to time also, as a result of these dropouts.

My server is set to have a static IP [192.168.0.100], and is connected to my Wireless router through a LAN cable. All ports are forwarded, because it works initially.

I would love to continue using Ubuntu for this purpose, if someone could assis me I would greatly appreciate it.

Thanks again!

---

### Post by Origin415 on 2008-03-04
When the connection doesnt work, post the output of ifconfig (if the server is headless, youll have to plug in a monitor). See if the server has internet access in general, ping google.com for instance.

If your desktop is also behind this router (put it there temporarily if not), does the desktop lose its internet connection randomly as well? When the server doesnt work, can you still access it directly by [http://192.168.0.100](http://192.168.0.100) instead of the outside ip address?

---

