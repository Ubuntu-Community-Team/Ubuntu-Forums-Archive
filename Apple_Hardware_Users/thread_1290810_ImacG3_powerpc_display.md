---
title: "ImacG3 powerpc display"
date: 2009-10-13
forum: Apple Hardware Users
---

### Post by ccrtechline on 2009-10-13
Just installed 9.04 on a gray/white imac G3 ppc. This is a DV slot loader after may2001 model. (though DVD drive had to be replaced and now downsized to a CD drive)

the initial install was painless.:)
After applying updates the problem with gnome went away.

But now I can't figure out how to change the display resolution. It seems that the imac is stuck in 800x600 mode.

Would like to have the 1072x798and even theater mode.

The imac specs are

ppc cpu - at least 300 Mhz
ati rage128 pro agp 2x
100 G IDE HDD

:confused: Need help.

Thanks

---

### Post by guybrush.d on 2009-10-15
Hi, ccrtechline

I have an ibook clamshell indigo 366Mhz too!, but so far i'm not sure you can get 1024x768 on clamshell lcd, if u browse the forums you will find a way to get it but when i treid on mine, it didn't work, so i know for sure clamshell lcd is 800x600 max you can check if your model supports 1024x768 over apple web site. If so you should just add the line in the screen subsection of /etc/X11/xorg.conf:

...
Subsection Display
...
Modes 24 "1024x768" "800x600" "640x840"
...
...

Hope helped you CIAO!:P

---

### Post by oswaldkelso on 2009-10-15
HOWTO: Choose the resolution YOU want in xorg.conf

[http://forums.debian.net/viewtopic.php?f=16&t=26577&](http://forums.debian.net/viewtopic.php?f=16&t=26577&)

---

