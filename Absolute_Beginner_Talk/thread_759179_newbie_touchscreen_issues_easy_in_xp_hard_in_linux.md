---
title: "newbie touchscreen issues easy in xp hard in linux"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by deembee on 2008-04-18
Hi I have a problem I thought I'd try linux out and have installed ubuntu but i can't seem to make my touchscreen work. Its a generic one from ebay and works a treat in xp.

 I have looked at how too's but they all assume a level of knowledge greater than i have. i can work most things out (i have a technical background) and have never had too much of a problem getting things to work in windows. I've allways found the how too's in xp easy to follow but some of the guides i have looked at on the web are written by obvious linux geeks
 [http://www.linux-tutorial.info/index.php](http://www.linux-tutorial.info/index.php)  [http://tzilla.is-a-geek.com/articles/egalax/](http://tzilla.is-a-geek.com/articles/egalax/) 
 but with no real skill in writing a guide for the common person. 

Anyway I would really like to use linux and find for general computing its fine but when someone wants to add somthing its still too hard. In windows all i have to do is double click the driver file and its done; is there some way i can do a similar thing in linux?

I really want to to use it on an old pc, 2gigceleron 512ram, that i want to turn into a touchscreen music player with all my collection in FLAC. 

if someone could help me out with this and point me in a direction for good linux tutes that would be great

---

### Post by Kinst on 2008-04-18
What's the touchscreen called and which guide are you using? I could try to translate a guide for you?

---

### Post by deembee on 2008-04-18
[http://www.b-billion.com/index.php3?function=list&id=76](http://www.b-billion.com/index.php3?function=list&id=76)

the files i have are called TouchKit-1.08.1227-32b-k26.tar.gz

---

### Post by Kinst on 2008-04-19
Okay...I'm no expert. But try copying this into a terminal when the screen's plugged in and see if one of the things that pops up is your monitor. If it doesn't pop up then ubuntu's not recognizing it in the first place.

```
cat /proc/bus/input/devices
```

And then at some point you'll have to edit the file /etc/X11/xorg.conf (but always always  **always** back up xorg.conf first), and put something like this in it:

```
Section "InputDevice"
Identifier "touchscreen0"
Driver "~~~~~~~~~~~~***driver name?***~~~~~~~~~~~~~~"
Option "Device" "/dev/input/event0"
Option "DeviceName" "touchscreen"
Option "SendCoreEvents"
EndSection
```

If you see like a guide for your specific monitor or something maybe I can help more? :(

---

### Post by prshah on 2008-04-19
> **deembee said:**
> [http://www.b-billion.com/index.php3?function=list&id=76](http://www.b-billion.com/index.php3?function=list&id=76)

the files i have are called TouchKit-1.08.1227-32b-k26.tar.gz

The touchscreen input seems to be through USB... does lsusb show anything relevant? how about ```
dmesg | tail -20
``` after plugging in the USB?

---

