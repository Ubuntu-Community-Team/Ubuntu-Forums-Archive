---
title: "Name resolution doesn't work in Firefox - Ping / Synaptic / etc. OK"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by paulozzzz on 2007-02-21
People,

   I have a new Ubuntu intallation.  The network card was correctly detected, but when I type "http://www.google.com" the message "Looking up host..." appears in the status bar for a long time before the connection error screen appears.  The odd thing is that when I type "ping www.google.com" it correctly resolves the name into an IP address, Synaptic is also able to resolve names when it downloads the packages.  When I copy and paste the IP address into the address bar of the browser the page loads.

How do I have name resolution working with my internet browser (Firefox)?

:confused:

---

### Post by mahy on 2007-02-21
does it work with any other web browser?

---

### Post by paulozzzz on 2007-02-21
> **mahy said:**
> does it work with any other web browser?

I don't have another browser.  But I tried **wget http:/www.google.com/index.html** and it resolved the name, but after a long while.  Maybe the timeout setting in Firefox is less than the wget command's.

This is now a slow name resolution problem.  I have Firefox in Windows and it doesn't take that long.  I'm confused.

---

### Post by mahy on 2007-02-21
It could be the case that IPv6 is enabled. You have to disable it in Firefox. Go to about:config, put number "6" into the filter and doubleclick network.dns.disableIPv6 to set it to 'true'. Let me know if it helped.

---

### Post by paulozzzz on 2007-02-21
> **mahy said:**
> It could be the case that IPv6 is enabled. You have to disable it in Firefox. Go to about:config, put number "6" into the filter and doubleclick network.dns.disableIPv6 to set it to 'true'. Let me know if it helped.

Yay! Thanks very much!  Name resolution is now lightning fast!

:guitar:

---

### Post by naurus on 2007-03-07
> **mahy said:**
> It could be the case that IPv6 is enabled. You have to disable it in Firefox. Go to about:config, put number "6" into the filter and doubleclick network.dns.disableIPv6 to set it to 'true'. Let me know if it helped.

Dude! this should be posted somewhere, and if it is already, where is it?

---

