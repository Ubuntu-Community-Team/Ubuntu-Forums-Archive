---
title: "Total Noob questions."
date: 2006-03-10
forum: Absolute Beginner Talk
---

### Post by TheBigGeeUK on 2006-03-10
Apologies for probably being so thick! lol

I know wireless USB adapters are a bit of a pain to install, even for more experienced Linux users, but having a wired connection just isn't practical for me, so I'm having to try! lol

How do I know whether my Ubuntu 5.10 installation recognises my wireless usb adapter??

Gee

---

### Post by dermotti on 2006-03-10
You could always download a live CD and find out without touching your harddrive

---

### Post by TheBigGeeUK on 2006-03-10
Apologies, I should of stated that I've already installed Ubuntu! My bad!

Gee

---

### Post by dermotti on 2006-03-10
If you type:   ifconfig      

from command line, do you get an ip address?

---

### Post by DAXP on 2006-03-10
Wait, are we talking about normal wireless keyboards and mouses, or something I'm not aware of? I'm currently using a wireless keyboard and mouse, old gyration ones, and I've had no trouble. And I don't know much about Linux.. >_>

Anyway, to answer your question, just plug it in and try. Search the net (Google's good) for drivers if that doesn't work.


Ah. I think I know what you are talking about now. No clue about that. I was hoping I had finally found someone I could help. =(

---

### Post by TheBigGeeUK on 2006-03-10
No I dont' get an IP address.

I just get stuff reference my 'eth0' (my onboad lan?) and lo (loopback somm't?)

Just to clarify this a USB Adapter (Safecom swmulz-5400) to connect to my wireless router  (D-Link DSL-G604T) downstairs, hence I don't want to trapse a wire all around the house. If I owned the house then I would! lol

Gee

---

### Post by TheBigGeeUK on 2006-03-11
I'm trying to install a driver for my Safecom SWMULZ-5400 USB Wireless adapter that came on the disk with it. I've managed to edit the Makefile with the correct kernel details and such like, but when I run Make I get:

```
/usr/src/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:9714: error: dereferencing pointer to incomplete type
/usr/src/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:9714: error: ‘MAC_Mode’ undeclared (first use in this function)
/usr/src/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:9715: error: dereferencing pointer to incomplete type
make[4]: *** [/usr/src/ZD1211LnxDrv_2_2_0_0/src/zd1205.o] Error 1
make[3]: *** [_module_/usr/src/ZD1211LnxDrv_2_2_0_0] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/usr/src/ZD1211LnxDrv_2_2_0_0'
make[1]: *** [both] Error 2
make[1]: Leaving directory `/usr/src/ZD1211LnxDrv_2_2_0_0'
make: *** [all] Error 2

```

What's going wrong?

Also do you need to mount USB Wireless adapters? 

Some please help. I'd really like to be able to get this to connect to the net via the USB Adapter.

Gee

---

