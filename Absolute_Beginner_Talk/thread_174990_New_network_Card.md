---
title: "New network Card"
date: 2006-05-12
forum: Absolute Beginner Talk
---

### Post by DaemonLee on 2006-05-12
Hi, I have a new 10/100 Network Card from D-LINK and Ubuntu doesn't have drivers for it. 

Is there a way to convert the Windows Drivers to work with Linux or am I SOL?

The Card Model number is; 

DFE-530TX+ by D-LINK.

---

### Post by ZiLOG_Z80 on 2006-05-12
NdisWrapper is software designed primarily to allow you to use windows drivers for wireless network cards, though it does work for other drivers incliding ethernet. Maybe you could have some luck with that

[http://ndiswrapper.sourceforge.net/]("http://ndiswrapper.sourceforge.net/")

---

### Post by DaemonLee on 2006-05-12
[img]http://daemonlee.com/Screenshot.png[/img]

I just found this folder but I don't understand what the instructions are stating that I should do; 

here's a link. [http://daemonlee.com/linux.txt](http://daemonlee.com/linux.txt)

---

### Post by Stinger on 2006-05-12
I think your card is supported but try looking here:
[http://support.dlink.com/faq/view.asp?prod_id=487&question=General%20Linux]("http://support.dlink.com/faq/view.asp?prod_id=487&question=General%20Linux")

Under the paragraph **Desktop Adapters**.

It should be either the via-rhine or the rtl8139 chip on your card which is supported in linux.
Hope it helps:-D

---

### Post by skippy81 on 2006-05-12
DaemonLee, as noted by the above poster the linux kernel includes the drivers you need.  The are allready compiled so you dont need to fiddle around with the makefile.

There are a few different drivers which you can try.  Since these drivers take the form of kernel modules you can enable them with the modprobe command (which inserts a module into the kernel after checking it is compatible).

Open a terminal.  Try 

> modprobe via-rhine

then fiddle with you network settings, do a search and look up the various ifconfig comands.  If via-rhine driver doesnt work then you could also try:

> modproble 8139cp and > modprobe 8139too as a last resort. The via-rhine driver should be all you need though.

---

