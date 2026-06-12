---
title: "how to install cdemu or daemon tools"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by kahram.yoon on 2007-11-22
How do I install cdemu and/or daemon tools?  I need these for mounting images.

---

### Post by minisubwoofer on 2007-11-22
hello there,
 no need for daemon tools
quickest way to do that is open up a console and type

```

sudo mkdir /media/iso
sudo mount -o loop -t iso9660 "<path to iso image>" /media/iso
```

this will only work for iso images though


to unmount
```

sudo  umount /media/iso

```

---

### Post by kahram.yoon on 2007-11-22
well thats helpful but i would like to have cdemu or daemon tools so i can mount other images as well and so i dont have to type that into console every time....

---

### Post by minisubwoofer on 2007-11-22
A frontend for that command
```
sudo apt-get install gmountiso
```

otherwise, might not be the best solution but a quick google brings this up
[http://onlyubuntu.blogspot.com/2007/06/mount-and-unmount-isomdfnrg-images.html](http://onlyubuntu.blogspot.com/2007/06/mount-and-unmount-isomdfnrg-images.html)
give those a try
tell us how it goes

edit: probably should have made it a long google instead

latest version is here

[http://www.acetoneteam.org/download.html](http://www.acetoneteam.org/download.html)

---

### Post by Dirty Ole on 2007-11-22
Use a program called [acetoneiso]("http://www.acetoneteam.org/central.html").

It natively supports iso, nrg, mdf, bin, img. The site has a deb package for gutsy, so installing is not an issue either.

---

### Post by kahram.yoon on 2007-11-22
I got the installation to work so thank you for the help.

---

### Post by oscarc on 2008-02-09
Hi, I wanted to try acetoneISO, but som required packages were of "unauthenticated nature". Anyone got any comments on that? Is it ok to install them anyway? 

I can say I tried cdEmu, but got stuck because of:

~$ cdemu 0 /media/sda1/skiva.cue
ERROR: Failed to connect to CDEmu daemon: org.freedesktop.DBus.Error.ServiceUnknown: The name net.sf.cdemu.CDEMUD_Daemon was not provided by any .service files
ERROR: Failed to connect to daemon!

If anyone knows what I have done wrong I would be grateful. I installed five packages for cdemu, but I have not done any coding, as I have seen on other places was the case with this program. 

Regards
Oscar

---

### Post by mad_max0204 on 2008-02-09
I just installed AcetoineISO on my gusty and everything works fine. Just folow the instructions from their site and u can do it in 5 steps. I didnt use deb package since its for 32bit system and I have 64bit installed so I used src.

Regards

---

### Post by emeraldknight1977 on 2008-03-24
> **minisubwoofer said:**
> hello there,
 no need for daemon tools
quickest way to do that is open up a console and type

```

sudo mkdir /media/iso
sudo mount -o loop -t iso9660 "<path to iso image>" /media/iso
```

this will only work for iso images though


to unmount
```

sudo  umount /media/iso

```

I've tried this and it works

Phill

---

### Post by Trail on 2008-03-24
I second acetoneiso. Very good, no problems thus far.

---

