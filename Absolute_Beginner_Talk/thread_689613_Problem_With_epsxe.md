---
title: "Problem With epsxe"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by Crumpets and Jam on 2008-02-06
I have installed *epsxe* using this [guide]("http://ubuntuforums.org/showthread.php?t=612021"). When I try to run a game from the CD drive, I get this error message. This is what I am seeing in the terminal.

```
john@JohnUbuntuDesktop:~$ epsxe
 * Running ePSXe emulator version 1.6.0. 
 * Memory handlers init. 
 * ePSXe: PSX BIOS loaded [/usr/local/games/epsxe/bios/SCPH1001.BIN]. 
 * Init internal cdrom ... ok
 * First/Last track: 1 1
 * Track 1:  (DATA) - Start 0: (00,02,00) 
 * PAL cdrom detected. 
 * Init gpu[0][libgpuPeteXGL2.so.2.0.8] 
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Error: couldn't get fbconfig
/usr/local/bin/epsxe: line 6:  7250 Segmentation fault      (core dumped) ./epsxe
john@JohnUbuntuDesktop:~$
```

epsxe shuts down and nothing happens. Anyone know whats going on? Thanks.

---

### Post by Crumpets and Jam on 2008-02-07
Sorry to bump this up but does anyone know how I could get this working?

---

### Post by Crumpets and Jam on 2008-02-08
Please? Anybody?

---

### Post by Crumpets and Jam on 2008-02-13
Anyone at all?

---

### Post by Crumpets and Jam on 2008-02-17
*sob*

---

### Post by disturbedite on 2008-02-17
i'd recommend switching to pSX.  its a better emulator imo.  there is an ubuntu [repo]("http://packages.dfreer.org/") maintained with pSX in it, so you don't have to install it "manually" or compile it.
but unfortunately the repo is down atm...

---

### Post by spiderbatdad on 2008-02-17
could be you are missing some clibs. I'm not sure of all the causes of a seg fault. I believe it can be due to not having c libs compatible to the ones the program was written in. There is another thread here:[http://ubuntuforums.org/showthread.php?t=159987](http://ubuntuforums.org/showthread.php?t=159987) maybe it will help you. There may be a graphics card incompatibility.  Surely you have installed "build-essential."

---

### Post by Crumpets and Jam on 2008-02-18
Thanks for the help. I will try pSX when the repo is back online then.

If anyone else can help, please post.

---

### Post by disturbedite on 2008-02-19
in the meantime, you can grab a precompiled binary of pSX from the [pSX website]("http://psxemulator.gazaxian.com/"), if you want...

---

