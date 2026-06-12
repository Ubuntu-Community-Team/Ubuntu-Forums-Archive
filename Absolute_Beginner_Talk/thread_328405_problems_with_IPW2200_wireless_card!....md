---
title: "problems with IPW2200 wireless card!..."
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by makiroll on 2006-12-30
ok, firstly, this may seem silly but it doesnt actually relate to Ubuntu Directly. In fact, Ubuntu is one of the very few distributions that I've had this problem, but let me begin.

ok, so, I have a Intel Celeron Centrino PRO/Wireless 2200b/g and, most distributions do not have native support for such a device. so far I have only been able to install the firmware on Fedora Core 6. I have found that (K / X )Ubuntu 6.06+ & linuxconsole support it out of the box, but for FC6 I had to place the extracted tar files into the /lib/firmware directory.

however, I cant get it to work on Debian, BeatrIX,DamnSmallLinux, etc.

I have found multiple 'firmware' directories on various distros, but none of thee others apart from FC6 will recognise the Firmware files with:


[FONT="Courier New"]rmmod ipw2200
modprobe ipw2200
iwconfig
[/FONT]

am I hopeless or is there something in general that i'm really missing? Thanks,
Maki ^_^

---

### Post by Vorian on 2006-12-30
What do you get when you 

iwlist eht1 scanning?

If you get something, just

sudo dhclient eth1

---

