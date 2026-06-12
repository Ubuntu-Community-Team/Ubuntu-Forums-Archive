---
title: "NetworkManager problem"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by fcapria on 2007-02-28
I've recently loaded Dapper onto an old Sony PCG-650 laptop. I was unable to get a Xircom XE 2000 10/100 PCMCIA card working, but I was able to get a Netgear MA104 wireless card working. 

Typing the terminal commands in this post: [http://ubuntuforums.org/showthread.php?p=1330934](http://ubuntuforums.org/showthread.php?p=1330934) works perfectly, but using Network Manager always fails. It sees the network, but never acquires the network key. The wireless router is an old Netgear ME102. I type in the same info, but it never connects. I've tried "128-bit pass phrase" and 128/64 bit hex. (I suspect the router uses 40-bit encryption, but couldn't ascertain that online.)

I've also tried to connect to the 802.11g network here -- SSID unpublished, no password. That also fails. 

Thanks for any help,
Frank

---

### Post by cwmaxson on 2007-02-28
Use this, it's better:

[http://compwiz18.blackhole.cx/wicd/wb/](http://compwiz18.blackhole.cx/wicd/wb/)

I had the same problem until this guy made the greatest piece ever.

Cheers!

---

### Post by fcapria on 2007-03-05
Thanks, I'll try it. I ended up upgrading the machine to Edgy and things started working... mostly. Had to disable IPV6 and ditch the old Netgear ME-102 Wireless Router. For some reason it wouldn't do better than dial-up speeds. The newer 3Com I'm using now works fine.

---

