---
title: "Ubuntu won't connect to new airport base station"
date: 2007-08-22
forum: Apple Intel Users
---

### Post by macaholic on 2007-08-22
I just got my new airport extreme base station and everything works fine on osx and I set it up w/ wpa2 aes. Unfortunately ubuntu won't connect to it anymore. Yes I know the driver works because it connected to my old router (wrt54g) just fine. Have tried plain old wpa and that doesen't work either. It can see all the networks, but won't connect to mine.
Any help/input on this matter would be greatly appreciated.

---

### Post by macaholic on 2007-08-23
Has anyone had this problem besides me? I've tried renaming the network and changing the security and everything, but it just won't connect.

---

### Post by pxwpxw on 2007-08-24
Given that the current system worked for the old router. and it works from OSX, and that you have tried with open security settings, there may be some other configuration carried over from the wrt54g, that is now wrong for the Airport Extreme base. e.g. channnel, rate, essid etc. 
Check the osx airport manager settings, and in ubuntu look at 
```

 cat /etc/network/interfaces
 iwconfig
 ifconfig

```
Do a full restart after configuration changes.

---

### Post by macaholic on 2007-08-24
Already tried that and changed every possible setting on the airport and made sure the were the same w/ my config. What I think the problem is, is that the driver I'm using (ndiswrapper) doesn't seem to support 802.11n, even though it is a n-card, and for some reason that is causing the problem. I also had the airport setup to accept 802.11g as well, so it SHOULDN'T be a problem but that is the only thing I can think of. I think more people have this problem and don't know it and that in the coming months when more people switch to 802.11n either by default or choice then this issue will get more prominent and it will get resolved. Until then it seems as if I will be stuck using my crappy wrt54g for a while longer. :(
Thx anyway though.

---

### Post by russell.h on 2007-08-24
The airport extreme base stations aren't so great. I paid for one and am regretting it. The only 2 features it offers over models half the price are the print server and the file server. The file server is unusably slow (tell me why I can only transfer at 1 megabyte per second on an 802.11n connection to a usb 2 hard drive....). The print server is nice, but I could have just bought a networked printer.

Plus there is the fact the stupid thing has quit working right - it won't function at all in bridge mode (I already have a good router, all I need is an access point), and the configuration utility can only rarely find the router (I have to restart the computer and the router several times to fix it).

It was nice while it was working, but with all of its problems, coupled with the fact that I bought it just a few weeks before they added gigabit LAN (you know your router is messed up when the wireless connection is faster than the wired one) I'm about to go crazy.

---

### Post by pxwpxw on 2007-08-24
> **macaholic said:**
> Already tried that and changed every possible setting on the airport and made sure the were the same w/ my config. What I think the problem is, is that the driver I'm using (ndiswrapper) doesn't seem to support 802.11n, even though it is a n-card, and for some reason that is causing the problem. I also had the airport setup to accept 802.11g as well, so it SHOULDN'T be a problem but that is the only thing I can think of. I think more people have this problem and don't know it and that in the coming months when more people switch to 802.11n either by default or choice then this issue will get more prominent and it will get resolved. Until then it seems as if I will be stuck using my crappy wrt54g for a while longer. :(
Thx anyway though.

Just wondering what is the wireless chip for the Mac Pro (your signature)
```

 lspci -v

```
There is possibly a more suitable driver  than ndiswrapper is using.

---

### Post by cyberdork33 on 2007-08-24
> **macaholic said:**
> Until then it seems as if I will be stuck using my crappy wrt54g for a while longer.

WRT54Gs are _FAR_ from crappy routers.

There may be various modes on the router (I have never used an Apple router). Try disabling n connections altogether, and if that fixes it, then you can be sure that was the issue. i don't think it is ndiswrapper as mine connects to a WRT300N just fine (at G speed).

---

