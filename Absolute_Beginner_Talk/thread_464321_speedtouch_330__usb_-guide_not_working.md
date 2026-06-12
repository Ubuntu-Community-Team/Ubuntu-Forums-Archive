---
title: "speedtouch 330  usb -guide not working ?"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by Colin Lenton on 2007-06-04
I have read a guide to getting spreed touch 330 to work.  the guide is at  [http://www.linux-usb.org/SpeedTouch/ubuntu/index.html.It](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html.It) gives the following command to find out which firmware... awk'/406/ {print $5 }' /proc/bus/usb/devices.
does it mean to type this in windows DOS (because  the modem works in xp ) because when I do I get a message saying that "awk" is not a valid command. 
I tried typing the command in  ubuntu  and it didn't do anything. Where should i type this, and how do i use the firmware extractor also described in the guide because my computer  ( in windows xp ) does not know with what programme to open the firmware extractor.

I am as is plainly evident to you an absolute novice to linux. I am keen to learn but need help!!
Does anyone know of any local (Derby, England) groups where i could actually talk to someone, as I don't know if Email communication will be sufficient.

---

### Post by jgrabham on 2007-06-04
I have that modem - my advice - give up!

Get a modem that connects through an RJ45

---

### Post by Colin Lenton on 2007-06-04
thanks for the advice!
do you use an ethernet card and a router, then?  did your set up cost l;ots, and was it easy to set up?

---

### Post by StevenHarper on 2007-06-04
> **Colin Lenton said:**
> I have read a guide to getting spreed touch 330 to work.  the guide is at  [http://www.linux-usb.org/SpeedTouch/ubuntu/index.html.It](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html.It) gives the following command to find out which firmware... awk'/406/ {print $5 }' /proc/bus/usb/devices.
does it mean to type this in windows DOS (because  the modem works in xp ) because when I do I get a message saying that "awk" is not a valid command. 
I tried typing the command in  ubuntu  and it didn't do anything. Where should i type this, and how do i use the firmware extractor also described in the guide because my computer  ( in windows xp ) does not know with what programme to open the firmware extractor.

I am as is plainly evident to you an absolute novice to linux. I am keen to learn but need help!!
Does anyone know of any local (Derby, England) groups where i could actually talk to someone, as I don't know if Email communication will be sufficient.

Hi I have made a USB Modem Manager that works with Speedtouch modems on Ubuntu 6.04, 6.10 and 7.10

It even works of a live CD, just download and doubleclick the deb file

Here is my Forum entry

[http://ubuntuforums.org/showthread.php?t=445701](http://ubuntuforums.org/showthread.php?t=445701)


You can read about it here

[http://www.squeezedonkey.com/wiki/linux/index.php](http://www.squeezedonkey.com/wiki/linux/index.php)

and download it here

Please give it a try

Steve

---

