---
title: "Asus Zenbook UX32A - Touchpad doesn't work"
date: 2012-09-30
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Bozoo on 2012-09-30
Hello, 

I installed Quantal version on my  UX32A but my touchpad doesn't work. 
Do you have some idea why ? 

Thank's

```

Kernel : 3.5.0.16.generic
Name="ETPS/2 Elantech Touchpad".

In usr/share/X11/xorg.conf.d i have some files : 
10-evdef.conf 
11-evdev.quirks.conf
11-edev.trackpoint.conf
50.wacom.conf


```

---

### Post by Bozoo on 2012-10-01
Some infos about the touchpad : 
Name="ETPS/2 Elantech Touchpad".

In usr/share/X11/xorg.conf.d i have some files : 
10-evdef.conf 
11-evdev.quirks.conf
11-edev.trackpoint.conf
50.wacom.conf

Before the update i used : 52-asus-zenbook-synaptics.conf ... but right now i just desactivate because with or without this files it's the same problem. 

I tryed to put a wacom tablet, same stuff it's not recognized but on an old computer with ubuntu it's work. 

So if you have some idea, will be great ;)

---

### Post by Bozoo on 2012-10-01
I just install the kernel 3.6 RC_7 the problem is still here

johan@johan-laptop:~$ uname -a
Linux johan-laptop 3.6.0-030600rc7-generic #201209232235 SMP Mon Sep 24 02:43:01 UTC 2012 i686 i686 i686 GNU/Linux

---

### Post by sigmatht on 2012-10-01
Kernel's 3.4.0 and 3.6.0 both work flawlessly for me (minus the right click still being disabled).  I imagine something went wrong in the upgrade.  

I'd try:

  sudo apt-get install xserver-xorg-input-synaptics
  synclient TouchpadOff=0

---

### Post by Bozoo on 2012-10-02
> **sigmatht said:**
> Kernel's 3.4.0 and 3.6.0 both work flawlessly for me (minus the right click still being disabled).  I imagine something went wrong in the upgrade.  

I'd try:

  sudo apt-get install xserver-xorg-input-synaptics
  synclient TouchpadOff=0


Thanks a lot sigmath i just install the package xserver-xorg-input-synaptics and it's work ! 
:smile:

---

### Post by sigmatht on 2012-10-02
No problem.  If its solved.. please mark the thread as solved.

---

