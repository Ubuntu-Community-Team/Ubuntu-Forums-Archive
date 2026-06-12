---
title: "Difficulties with installing 7.10"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by woscafrench on 2007-10-20
So I'm doing a fresh install, and booting up first it would freeze up because of problems with APIC, so I had to disable it. But after doing that, it gets a little futher when booting up, but then my monitor tells me the signal is "out of range", I'm guessing there's problems with my graphics card?,So I try recovery mode, but that also freezes up, the last thing I'm told is there's been an abnormal exit of /sbin/modprobe, although I've no idea if that's the actual problem 

What's annoying about this, is how there seem to be several different things all going wrong at once.

---

### Post by chalex on 2007-10-20
It would be helpful if you posted what your hardware is.  e.g. What video card do you have?

---

### Post by Pumalite on 2007-10-20
Try Alternate CD.

---

### Post by FredB on 2007-10-20
> **Pumalite said:**
> Try Alternate CD.

Indeed. I only used once live cd installer. Since Edgy, alternate only. Faster, geekier, better ;)

---

### Post by woscafrench on 2007-10-20
My graphics card is an NVIDEA GeForce 7300LE and my processor is an AMD64 Athlon X2 4200+

I did use the alternate CD for this. I tried the Live CD first, but I couldn't get anywhere because I was encountering similar problems

---

### Post by Pumalite on 2007-10-20
Ctrl+Alt+F1 to get command line
sudo dpkg-reconfigure xserver-xorg
Choose 'vesa' as the driver
Once IN the system, install appropriate driver

---

### Post by woscafrench on 2007-10-21
I'm sorry, I wish I could change the thread title (I don't think i can anyway) but the problem I have at the moment is booting, not installing. I was a little confused when I wrote the title; I had been having installation problems too but those somehow I just mananged to get out of.

> **Pumalite said:**
> Ctrl+Alt+F1 to get command line
sudo dpkg-reconfigure xserver-xorg
Choose 'vesa' as the driver
Once IN the system, install appropriate driver

Where exactly am I able to do that? 

I was trying to get into the command line while it was booting up (when the monitor starts saying "out of range") and all of a sudden everything comes back and it starts to boot normally, well, the resolution was all wrong, but it was a start. Then after I logged in for the first time, I was told i could install a proprietary driver for my graphics card, which I did because clearly I'm not a true believer of the free software movement. But I had to restart. And then the same problems kept happening. 

If I were to guess what was going on, I would say that the graphics card wasn't the issue. The problem is whatever is causing an abnormal exit of /sbin/modprobe, and it makes the computer freeze while its signal is out of range. I was getting this while I was trying to install too.

---

