---
title: "Help!  What does this mean and how do I fix it??"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by ilovelinux on 2007-08-07
Hi,  When my computer starts up(I run Ubuntu and only Linux Op System) this message come up....

error 18: selected cylinder exceeds maximum supported by BIOS


i then have to manually select a mode for the computer to fully boot up!!  Any tips, suggestions???

Thank you, :-)

---

### Post by steven8 on 2007-08-07
This happened to me the second time I tried to boot up OpenSuse.  I corrected it by overwriting the install with Kubuntu, then Ubuntu, and I've never had the problem again.  I don't know why the first boot with OpenSuse went okay, then borked on the second boot.

---

### Post by init1 on 2007-08-07
> **ilovelinux said:**
> Hi,  When my computer starts up(I run Ubuntu and only Linux Op System) this message come up....

error 18: selected cylinder exceeds maximum supported by BIOS


i then have to manually select a mode for the computer to fully boot up!!  Any tips, suggestions???

Thank you, :-)
Might be a bad partiton table. Would you mind losing everything on your HD?

---

### Post by kavon89 on 2007-08-07
I'm totally guessing here: Maybe we should take the message literally and look into that first, before wiping the drive.

> error 18: selected cylinder exceeds maximum supported by BIOS

Maybe your BIOS can't handle large cylinders? I'm not exactly sure what a cylinder in the hard drive is, but I plan to Google later. :P  Maybe it's a new hard drive with an old BIOS? :/ It seems like a bad partition and a fresh formatting could fix it, but I always like to try the least destructive fix first... since no one has an exact fix and it's cause yet.

---

### Post by anewguy on 2007-08-08
How large is the drive you are booting Linux from?  Some older PC's have a BIOS that doesn't "see" beyond "x" number of gigabytes on a hard drive, so it is possible that depending on your PC and the size of your hard disk it may be too much for your BIOS to handle.  Did you ever use this complete drive with Windows?  What version?  What is brand/model of your PC?  How big is your disk drive?   The answers to those questions might allow us to do more research and give you a better answer or even a fix.  Thanks!:)

---

