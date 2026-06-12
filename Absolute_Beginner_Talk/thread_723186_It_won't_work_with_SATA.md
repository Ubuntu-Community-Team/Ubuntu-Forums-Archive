---
title: "It won't work with SATA"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by Hanyo on 2008-03-13
I have tried to install 7.10 on my pc.  I have both SATA and IDE hard drives and CD\DVD drives. I have had to use my IDE CD drive to install from and IDE H/D to install to.  When ever I try to use the SATA's to install from, to or both it crashes.  

When I try to Install to the SATA H/D  I get lines of code streaming up the monitor.  When I try to install from the SATA DVD, It hangs for a few minutes and states the installer failed.  I have tried several CD's, burned from different burners, using different burning software.

I plugged my SATA in as a secondary H/D and setup in the BIOS for it not to boot from the drive.  Ubuntu hung before it could reach the logon screen. 

I am perplexed.  Any ideas?

Thank you in advance for your time and help.

Hanyo

---

### Post by MegaJim on 2008-03-13
This hardware compatibility section of the wiki might have something you can use to figure it out [https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

---

### Post by rklauco on 2008-03-13
I have installed my Ubuntu to my SATA 500GB Samsung from PATA DVD RW drive with no problem.
Also, I did install the Ubuntu from SATA DVD drive to PATA HDD, SATA HDD and there were no problems.
The only problems I had was installing to SATA drive connected using USB housing.
No other issues.
So maybe, there is a possibility of wrong HW (I hate to offer this as the only option...).

---

### Post by handydan918 on 2008-03-13
I'm not too sure about the current Ubuntu kernel, but I know a lot of current kernels are having big issues (along with grub!) with mixed IDE/SATA environments. 
For sure, keep checking and googling to see if any body knows of a fix, but sometimes the combination of the two drive types just doesn't work. 
There are some workarounds I remember hearing of, like disconnecting the SATA (or vice versa) and installing to the IDE only, then reconnecting the other drives and using them for /home and storage, etc. this usually takes some manual editing of /etc/fstab, and I don't know if that's what you want.

---

### Post by 1875 on 2008-03-13
Have you checked in your BIOS to see if you can set your SATA controller to IDE compatability mode or something similar ?

---

