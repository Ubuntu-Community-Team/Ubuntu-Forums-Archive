---
title: "Crystal Audio CS4237 not working."
date: 2005-08-11
forum: Absolute Beginner Talk
---

### Post by Seb Spiers on 2005-08-11
It is listed in the Device Manager as "On Board Device" but I dont appear to be able to get any sound.  Will it simply be a case of installing the driver?  

I have the following in the device/advanced properties;
```
Vendor: Unknown
Device: Unknown
Status: Status
Bus Type: Unknown
Device: Unknown
Capabilities: linux.sysinfo

bios.description	string	Crystal Audio CS4237
bios.on_board_device_information	string	true
bios.status	string	Enabled
bios.type	string	Sound
info.bus	string	unknown
info.capabilities	string	linux.sysinfo
info.parent	string	/org/freedesktop/Hal/devices/BIOS
info.product	string	On Board Device
```
Advice is greatly appreciated :)

---

### Post by Seb Spiers on 2005-08-12
shamless bump  [-X

---

### Post by poofyhairguy on 2005-08-12
Thanks for bumping. This was a good Google challenge. I have an answer...but its a little nerdy. Ask what you can't understand. You need this file:

[http://www.hyunju.com/cwb-bin/CrazyWWWBoard.exe?db=linux&mode=download&num=10&file=Stlinux.zip](http://www.hyunju.com/cwb-bin/CrazyWWWBoard.exe?db=linux&mode=download&num=10&file=Stlinux.zip)

then do this:

[http://64.233.161.104/search?q=cache:LYygApv2ig8J:www.hoontech.com/download/sound/driver_14.htm+&hl=en&client=firefox-a](http://64.233.161.104/search?q=cache:LYygApv2ig8J:www.hoontech.com/download/sound/driver_14.htm+&hl=en&client=firefox-a)

---

### Post by Seb Spiers on 2005-08-12
>  2. move cs4237.tgz file to /usr/src/linux/drivers/sound/I dont appear to have a "linux" directory.

---

### Post by Seb Spiers on 2005-08-21
[QUOTE=Seb Spiers]I dont appear to have a "linux" directory.[/QUOTE]
 shameless bump #2

---

### Post by wvslkr on 2005-08-21
You may want to look at this   [http://www.thinkwiki.org/wiki/CS4237](http://www.thinkwiki.org/wiki/CS4237)     These drivers are included in the kernel.  Do a sudo modprobe to see if one of them will work.

There is an old souncard how to in the Wiki I believe,  should help you set up.

Hope it helps :)

---

### Post by Seb Spiers on 2005-08-22
[QUOTE=wvslkr]You may want to look at this   [http://www.thinkwiki.org/wiki/CS4237](http://www.thinkwiki.org/wiki/CS4237)     These drivers are included in the kernel.  Do a sudo modprobe to see if one of them will work.

There is an old souncard how to in the Wiki I believe,  should help you set up.

Hope it helps :)[/QUOTE]
 will try this, ta.

---

