---
title: "64-bit Display Drivers for NVidia"
date: 2008-10-29
forum: BSD
---

### Post by sgtbug on 2008-10-29
Hi guys

Have been trying my hand on FreeBSD lately. I went to the NVidia website, and they apparently do not have the 64-bit drivers for BSD. Do they even exist?

Anyone know where I can find them? Or do I need to keep using 'nv'?


Thanks and Regards

---

### Post by mips on 2008-10-30
> **coolaks said:**
> Hi guys

Have been trying my hand on FreeBSD lately. I went to the NVidia website, and they apparently do not have the 64-bit drivers for BSD. Do they even exist?

Anyone know where I can find them? Or do I need to keep using 'nv'?


Thanks and Regards

There are no 64bit 'nvidia' drivers for FreeBSD, only 32bit. You have to use 'nv'.

---

### Post by LateNiteTV on 2008-11-03
or you can install the 32bit version of freebsd and enable smp. then use the nvidia 3d accelerated 32bit version of the nvidia driver. works for me.

---

### Post by sgtbug on 2008-11-13
i tried the 32 bit drivers.. they suck.. really!

now removing FreeBSD and going back to my Ubuntu 64 bit server..

---

### Post by sgtbug on 2008-11-13
i tried the 32 bit drivers.. they suck.. really!

now removing FreeBSD and going back to my Ubuntu 64 bit server..

---

### Post by mips on 2008-11-14
> **coolaks said:**
> 
now removing FreeBSD and going back to my Ubuntu 64 bit server..

Why do you need 3d gfx or any gfx at all on a server?

---

### Post by LateNiteTV on 2008-11-14
i was wondering the same thing...

---

### Post by zeiz on 2008-11-16
I'm trying FreeBSD for more than a year and now installed 7.1-Beta2x64. And, yes: there is no 64 driver for Nvidia. 
Well, no problem if nv can give me right resolution: I need 1680x1050x24 and I currently have seems 1024x768, I don't know actually because resolution applet shows nothing. I read that a guy got 1900x1200 with nv though he didn't tell how. I went to /etc/X11 to configure xorg.conf and ...didn't find any file there! Ok, I created it according to the handbook and lost gui: fatal error: no screens found. Renaming xorg.conf brings Gnome back with that resolution.
Did anybody have the same problem?

---

### Post by LateNiteTV on 2008-11-17
> **zeiz said:**
> I'm trying FreeBSD for more than a year and now installed 7.1-Beta2x64. And, yes: there is no 64 driver for Nvidia. 
Well, no problem if nv can give me right resolution: I need 1680x1050x24 and I currently have seems 1024x768, I don't know actually because resolution applet shows nothing. I read that a guy got 1900x1200 with nv though he didn't tell how. I went to /etc/X11 to configure xorg.conf and ...didn't find any file there! Ok, I created it according to the handbook and lost gui: fatal error: no screens found. Renaming xorg.conf brings Gnome back with that resolution.
Did anybody have the same problem?

delete the xorg.conf file and just run "startx". see what happens. these days, xorg can pretty much configure itself. try running startx without an xorg.conf file. 
if that doesnt work, then run xorgconfig and specify your correct horiz sync and vert refresh.

---

### Post by Sunnz on 2008-11-18
You can also run X -configure which would generate a X.conf.new file automatically at its best effort. Always worked for me, you may want to give it a try.

---

