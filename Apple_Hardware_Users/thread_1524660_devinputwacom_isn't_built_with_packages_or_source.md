---
title: "/dev/input/wacom isn't built with packages or source"
date: 2010-07-05
forum: Apple Hardware Users
---

### Post by Bq32 on 2010-07-05
On Ubuntu 9.04 "Jaunty" (I know that there are newer versions, but I have problems with updating to new versions), I have tried installing Linux-wacom several ways-- using xserver-xorg-input-wacom, wacom-tools, compiling from source-- and every time, I get a wacom_drv.so and other components but no /dev/input/wacom. Am I missing a step that gives me the wacom module, or am I just compiling wrong?

When compiling from source, I use:
```
$ ./configure
<configure information here>
$ make && make install
```

And often, it complains about not finding something with the kernel, so it doesn't build "kernel modules" (and yet make and make install run fine). I'm not sure if this is the reason, the architecture being PowerPC, or if this is an already solved problem. My tablet does work in Windows, however.

Is there any way I can get my tablet to work in Ubuntu?

I have a PowerMac G4 "AGP", with 450MHz and 1GB RAM, and have a Wacom Bambo Pen tablet (bought just last year).

---

### Post by linuxopjemac on 2010-07-05
There is a search bar in this forum.
[http://ubuntuforums.org/showthread.php?t=1259831](http://ubuntuforums.org/showthread.php?t=1259831)

---

### Post by Favux on 2010-07-05
Hi Bq32,

Is the ppc install a 64-bit install?  What version of linuxwacom are you trying to install?

---

