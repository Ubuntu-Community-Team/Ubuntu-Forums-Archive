---
title: "[SOLVED] networking for real newbies"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by ubername on 2007-03-18
Hi,

I have a network which (hopefully) consists of my main PC (Ubuntu 6.10) , a very old PC which is now Debian something (I don't know how to check Debian version, but linux kernel is 2.6 something), a Win XP SP2 Laptop (wireless) , and sometimes a Win98SE laptop (wireless).

My main aim is to get my two linux machines at least seeing each other (I can work out the permissions about which files, folders etc.  later, I hope). They are connected (Ethernet wires) through a router which also is a wireless access port if that helps.

Bizarrely, when I started this post, I could see this (ubuntu) machine and the WinXP laptop from the Debian machine, but when I went back to the Debian machine to verify the exact details for this post, it now shows nothing in the 'Windows Network' space after clicking on 'computer' 'network' 'windows network'

Same thing happens from this machine. It detects 'Windows Network' but clicking on it gives no results (i.e. an empty list)

Firewalls have been the cause of some similar problems when I was playing in windows land. Could this be the cause?

I am so very new to Linux it could be anything however. All help gratefully received.

TIA

---

### Post by dstew on 2007-03-18
Yes, it could be a firewall problem. Best is to enable the firewall of the router, and disable the firewall software on the Windows machine.

---

### Post by HereInOz on 2007-03-18
Also there will be a firewall on the Linux machines that could be causing you trouble.

If you know how to configure IPtables, then have a look at that, if not, install Firestarter and that will give you a GUI to configure your linux firewalls.

---

