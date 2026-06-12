---
title: "Need help seting the screen resolution"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by dinbach on 2006-10-21
Hi,

I've been trying to set the screen resolution on my laptop to 1600x1200. Although this mode is listed in the /etc/X11/xorg.conf file, there is no such option from the System->Preferences->ScreenResolution menu. It was working in Breezy but not in Dapper.
Any ideas?

Thanks

---

### Post by CatKiller on 2006-10-21
> Any ideas?You could find out the refresh ranges of your monitor and add them into the Monitor section of your xorg.conf.

---

### Post by aznboi on 2006-10-22
i did this and it worked for me on my desktop:

```
sudo dpkg-reconfigure xserver-xorg
```

do that and it should autodetect some hardware for you and after a bit ask you the resolution modes u want available, after you finish it, press:

```
CTRL + ALT + BACKSPACE
``` to restart xorg.

---

### Post by nousefreak on 2006-12-03
i used sudo dpkg-reconfigure xserver-xorg but it didn't detect my video hardware, 

I am using a Acer aspire 5000

can somebody help me!

---

### Post by ReaderRat on 2006-12-03
[**HowTo Resolution & Refresh**](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by nousefreak on 2006-12-05
i tryed to change this all
but it doesn't help

i wasn't able to find the right driver for SiS760GX 

i did find another one : "sis_drv.o-410"

can anyone tell me how i need to install this driver 
(and uninstall if the system crashes :p)

---

### Post by tony584 on 2007-03-25
any luck? i also have this problem with my acer aspire 5000.
some clear cut instructions would be amazing. if i can figure it out
i'll post instructions.

---

### Post by FNGtyler on 2007-03-31
i also have a acer aspire 5000 same issue

---

### Post by nousefreak on 2008-03-13
I trew my acer out of the window, and I'm never bying one again!!

---

