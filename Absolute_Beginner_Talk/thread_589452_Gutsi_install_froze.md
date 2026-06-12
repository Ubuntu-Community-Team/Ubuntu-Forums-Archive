---
title: "Gutsi install froze"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by melkor83 on 2007-10-24
Hi, i'm new to Linux

I was trying to install Ubuntu 7.10, I downloaded the AMD 64 image, i burned it and i was trying to do a fresh install following the guide... After selecting Start or Installa Ubuntu i got this


Kernel alive
Kernel direct mapping tables up to 100000000  @ 8000-d000

and my laptop froze.

I tried with CD, DVD, i burned them low speed to avoid errors, but nothing works...It can stay hours without changes

Please help me

regards, Melkor

My laptop has a AMD turion 64 MT30 processor

---

### Post by realvz on 2007-10-24
try  hitting F6 for the advanced options line at the installer boot screen, removing the splash option and adding noapic.

---

### Post by orange2k on 2007-10-24
Disappearing usplash is a known problem. But you should be able to get to the login screen eventually...
Try waiting a few minutes...

---

### Post by melkor83 on 2007-10-24
nothing. it froze at the same point.
Yesterday i waited literarily hours, and nothing, so it's not a waiting solving problem

---

### Post by realvz on 2007-10-24
can you try safe mode from the live cs boot options?

---

### Post by melkor83 on 2007-10-24
nothing again.

i tried also safe mode without splash and adding noapic

---

### Post by realvz on 2007-10-24
hate to say this..but can you try the alternate CD?

---

### Post by melkor83 on 2007-10-24
what should i do? Where i can download the alternate cd?

ty for helping me

---

### Post by realvz on 2007-10-24
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

there is checkbox just below the start download button...check it if u need alt cd

---

### Post by melkor83 on 2007-10-24
I did it...when i start install in text mode it gives to me a I/O error, Error reading boot CD
with a reboot button. everything i do at the boot page

---

### Post by ByteJuggler on 2007-10-24
Hmm OK, on the boot menu, there should be an option "Check CD for defects".  Please run that first to check the CD was downloaded and burned successfully, and can be read back successfully.  If it fails, you need to establish whether the original ISO file is corrupt or whether the burned CD's is somehow not readable on your laptop.  But first check if the CD's you've burned is OK and we can go from there.  :-)

---

### Post by melkor83 on 2007-10-24
even if i make Check CD for defects i got the same error and i have to reboot

---

### Post by melkor83 on 2007-10-24
I solve the alternate cd problem and i start the text installation but it freeze at the same point of graphical installation...i don't know what to do

---

### Post by orange2k on 2007-10-24
> **melkor83 said:**
> I solve the alternate cd problem and i start the text installation but it freeze at the same point of graphical installation...i don't know what to do

This may be hardware related - have you tried memtest to see if your RAM is working?

---

### Post by melkor83 on 2007-10-24
i tried and it is working

---

### Post by ByteJuggler on 2007-10-24
Please, check the md5 hash value for you CD's ISO image.  The proper MD5 values are [here]("http://no.releases.ubuntu.com/releases/7.10/MD5SUMS") The one for Gutsy 64-bit is:
ubuntu-7.10-desktop-amd64.iso: 61c87943a92bc7bf519da4e2555d6e86 

If the check media option fails, that suggests that your laptop's drive is having problems reading the disc (to the point of not even allowing the simple cd check to run) or that the CD's aren't being burned properly hence also causing read problems.  

Do you have access to another AMD64 machine?  If so, can you please try booting and doing a CD check on there.  If not AMD64, you could download the I386 CD ISO and try that instead (and check it from the machine you're posting from.)  It won't be the end of the world if you install the I386 version instead of the AMD64 version.

---

