---
title: "Blu-Ray drive, disappeared after GRUB reinstalled"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by computergeek13 on 2007-09-27
Ok, last week I got my system running Vista on the first partition, and Linux on the 2nd partition. Grub was the bootloader.

It works fine, however the Blu Ray drive disappeared when i installed ubuntu both in VISTA and ubuntu.

When i was working on some stuff for school in VISTA, i put a CD in the drive and it wouldnt load. I checked the device manager and the entry for cd/dvd drive was completely gone .

(2 days before linux was installed it was there and working)

So i figured a driver i installed was bad or something, so i reinstalled VISTA - and obviously it overwrote the MBR and grub was gone.

So i couldnt boot to the linux OS. yet.

I reloaded all the drivers for VISTA, installed my apps i needed for school (from CD drive) and then the next day worked on getting the dual boot back. Via Grub.

I loaded Ubuntu live cd up - started up a terminal, setup (hdo) to reinstall grub.
Works fine - rebooted into ubuntu fine.

Rebooted into vista - and the DVD drive is gone again.

I have a brand new Sony FZ-190 (loaded) with the matshushita blu ray drive.

I have no idea whats causing this or how to fix it.  

I tried to load a cd in ubuntu and it didnt work either.

anyone any help or advice? 

I have tried searching but cannot find any info on this error.

---

### Post by computergeek13 on 2007-09-28
has no one seen this error before?

---

### Post by computergeek13 on 2007-09-28
ok, ive found another similar instance of what i am experiencing. Yet i have no idea how to fix it.

Can one of you elder users interpret what steps i ought to take to repair?

[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/55955](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/55955)

here is the link to the guy who lost his CD drives. Those are my exact symptoms yet i have no idea how to repair grub.!

thanks in advance. sorry for the all the chatter

---

### Post by computergeek13 on 2007-09-28
perhaps someone could tell me how to remove the 2nd entry in GRUB for the older kernel?

---

### Post by Eddie Wilson on 2007-09-28
> **computergeek13 said:**
> perhaps someone could tell me how to remove the 2nd entry in GRUB for the older kernel?

Good Day,
In order to remove an entry in grub you have to comment out the line using # at the start of the line. Just do a sudo gedit in your /boot/grub/ directory and edit out the line in the menu.list, or it may be menu.lst, I can't really remember now and I'm at work so I can't get to my machine. Its pretty easy to edit the menu list to make it say anything you want also. Maybe that will help you out some.
Eddie

---

### Post by Eddie Wilson on 2007-09-28
Forgot to mention that you can delete the lines if you really want to. I just comment out what I don't need.
Eddie

---

### Post by computergeek13 on 2007-10-01
well i was finally able to comment out the lines, and they disappeared from the grub menu during restart. But my Drive is still missing. If i put a CD in it and try to read contents, nothing.

But if i put a bootable disc in and restart it detects it, until grub takes over and launches an OS, then i cant use the drive at all.

Anyone able to help with this it is rather frustrating.

For the record before linux updated the drive worked fine. After update it no longer works.

---

### Post by computergeek13 on 2007-10-02
can anyone recommend another forum or point me in a direction where i can attempt to solve this. its rather frustrating not being able to use a cd drive.

thanks

---

### Post by computergeek13 on 2007-10-03
please

---

### Post by nulldev1ce on 2007-10-03
have you taken a look here?

[http://www.sorgonet.com/linux/grubrestore/](http://www.sorgonet.com/linux/grubrestore/)

good luck!

---

