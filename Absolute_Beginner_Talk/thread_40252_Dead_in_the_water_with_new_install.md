---
title: "Dead in the water with new install"
date: 2005-06-08
forum: Absolute Beginner Talk
---

### Post by dweeb on 2005-06-08
Howdy!

I am confused.  Several weeks ago I constructed a spare computer with parts I had laying around and easily loaded ubuntu.  I played with it long enough to decide to add it to my main rig (WinXp, AMD64).

But I am stumped.  I have downloaded the 64 bit version, as well as the live cd.  Checksum with Fastsum (tested OK), burned the ISO image with two utilities (click n'burn, and ISO recorder plug-in). None of the above disks will get past the opening screen where it asks you to F1, type server, or enter (no blinking cursor, nothing).  The same thing happens with the original 32 bit disk that I used to install ubuntu on the above mentioned build!!

Arrrrggggg!  I have tried this from reboot status as well as cold boot. Seems to me something in my hardware setup is throwing a roadblock into my install.  Any suggestions?  I have listed here my setup:

Gigabyte GA-K8NSNXP-939, AMD3500+ 939
Ballistix PC 3200, 2x512 (all on stock clocks) WindowsXPro
Lian-Li V1000, TaganPS 480W
Zalman7000Alcu HSF Tyan9800Pro
Western Digital 74GB RaptorSATA
Western Digital 80Gb IDE HD
Plextor16X cd/rw, Asus CD
M-audio Revo5.1 /  Klipsch2.1promedia
Logitech MX-700 Hamster,
Dual Samsung 172X's (sweet)

Thanks for the assist.  BTW, I plan on installing ubuntu as a dual boot on the IDE hard drive, will have the installation disk partition for me???

dweeb (uber-noob)

---

### Post by dweeb on 2005-06-08
Could my ATI card be a problem/

Footnote; Knoppix  will load...

dwb

---

### Post by kleeman on 2005-06-08
If Knoppix loads it sounds like a (Ubuntu) kernel issue with your hardware. Try hitting F1 on boot and passing a whole bunch of options as suggested by the cd and see if any work (i.e. get past the freeze).....

---

### Post by dweeb on 2005-06-08
F1 doesn't function either. The opening screen pops up, then that is the end of the process.  I have to reboot to end the aborted install.

 Does the SATA drive possibly  interfer with ubuntu? That is the drive that I have windows on; my desire is to put ubuntu on the IDE drive, but I suspect that both have to be activated in order to configure a dual boot routine.

dweeb

---

### Post by dweeb on 2005-06-08
Just downloaded from the British site, slowed the burn down to 4x; same results.  Nothin.

I LOVE UBUNTU AND WANT IT TO BOOT!!!

sorry...

dweeb

---

### Post by meat on 2005-06-08
I had a problem installing Ubuntu with SATA drives, but I got a little farther than you before it would hang.  Here is what I did to fix the SATA issue.

[link](http://www.ubuntuforums.org/showthread.php?t=40142)

---

### Post by dweeb on 2005-06-08
Thanks for the tip, Meat.  My BIOS doesn't have any options that match the Dell setup.  I tried a few changes, but still no boot.

Hmmmmmm.

dwb

---

