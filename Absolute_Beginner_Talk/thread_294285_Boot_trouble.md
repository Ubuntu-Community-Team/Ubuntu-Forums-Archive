---
title: "Boot trouble"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by TangerineSkyy on 2006-11-06
Hey all,

Just made the switch last saturday and I couldn't be happier!

Just one thing- When I try to boot up my PC in the morning, sometimes after the ubuntu splash page, I get a blank page. My monitor eventually goes into standby mode and it just sits there unresponsive.

I THINK it has to do with either my usb flash drive, ipod, or external hdd. Would either of these pose a risk when I try to boot up (sort of like leaving a floppy in the drive and trying to boot up)?

Thanks.

-skyy

---

### Post by taurus on 2006-11-06
Can you get to a console with <Ctrl><Alt>F2 (holding those three keys down at the same time)?  If you can, log in and paste your /etc/X11/xorg.conf here...

```
more /etc/X11/xorg.conf
```
What video card do you have in your machine anyway?

---

### Post by TangerineSkyy on 2006-11-06
I'm in school right now, but I'll try when I get home. 

Running intel integrated graphics.

EDIT: Please note that I said sometimes... I have gotten it to work after playing with my usb devices, but it could just be a fluke.

---

### Post by taurus on 2006-11-06
If you want to know exactly which model, just run 

```
lspci
```

---

