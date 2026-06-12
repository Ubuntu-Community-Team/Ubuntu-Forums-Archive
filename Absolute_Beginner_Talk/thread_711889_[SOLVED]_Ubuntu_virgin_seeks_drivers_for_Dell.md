---
title: "[SOLVED] Ubuntu virgin seeks drivers for Dell"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by Nitro Fan on 2008-03-01
Hi All,
My first post I have had a taste of Linux with my Eee PC (which was converted to Win XP) but want to continue my Linux education by installing Ubuntu on my Dell Latitude D610.

Are all the drivers for this machine available for Ubuntu? especialy the touch pad.
Any tips for a clean install?
Any pitfalls to avaoid?

Thanks in expectation.

---

### Post by PeterJS on 2008-03-01
All of the linux drivers except for wireless* (except for Intel) and some (ATI and Nvidia) graphics**. Are included in the kernel itself so you won't need to hunt them down seperately. What wireless and graphics card does it have?

*This is in part due to FCC regulations, but largely hardware manufactures refusing to release their specs and interfaces

**ATI and Nvidia provide their own drivers. ATI has recently moved to using open drivers so eventually theirs will be merged in to the main kernel with all the other drivers.

As for tips, backup your data, no partition resizing is ever perfect, it's pretty safe these days, but problem crop up often enough that people still warn about them, you don't want to be the unlucky guy that is this months remember to backup first story. If you're setting up a dual boot, defrag, defrag, defrag, and then defrag again first to maximize the free space and minimize the chance of errors resizing your partitions. Linux is not windows, things are different, be prepared for that, there are folks that'll be glad to help, but you're going to need to put some effort in to learning how things work.

---

### Post by Nitro Fan on 2008-03-01
Hi PeterJS
Thank you for your reply,
I am planning on doing a fresh Ubuntu only install, I am downloading the distro now! does it give the option to format the HDD?

here is some of my Hardware below


Wireless Adaptor: Intel(R) PRO/Wireless 2915ABG network Connection

Bluetooth: Dell Wireless350 Bluetooth Module

Sound Sigma Tel C-Majour Audio

Display Adaptor: Mobile Intel(R) 915GM/GMS,910GML Express Chipset Family

DVD/CD TSSTcorp DVD+-RW TS-L532B

---

### Post by PeterJS on 2008-03-01
Oh you lucky man you, intel trough and through. No having to jump through any funny driver hoops, consider me jealous. If you're planning on wiping windows away completely the installer will be more than happy to do that for you and format the drive for you.

---

### Post by damn66 on 2008-03-01
> **Nitro Fan said:**
> Hi PeterJS
Thank you for your reply,
I am planning on doing a fresh Ubuntu only install, I am downloading the distro now! does it give the option to format the HDD?

here is some of my Hardware below


Wireless Adaptor: Intel(R) PRO/Wireless 2915ABG network Connection

Bluetooth: Dell Wireless350 Bluetooth Module

Sound Sigma Tel C-Majour Audio

Display Adaptor: Mobile Intel(R) 915GM/GMS,910GML Express Chipset Family

DVD/CD TSSTcorp DVD+-RW TS-L532B

i'm running Hardy Heron Alpha 5 on XPS M1210..have abt the same config as yrs except mine NVIDIA graphic card..runs flawlessly..

---

### Post by samicom on 2008-03-01
I just got xubuntu up and running on a d610. it was thoroughly painless. 

the touchpad works just fine, and i was sure to begin with a clean slate. well thats stretching it. I had to reformat a hard drive and reinstall everything, I took the opportunity to leave some of the hard-drive space unpartioned for xubuntu, which i had been eyeing for awhile. it was more opportunistic really. you ought to be in tip top shape. i almost didn't believe how easy it was to get this a dual boot up and running, and after just a few hours, i am considering making a permanent switch.

---

### Post by Nitro Fan on 2008-03-01
Thanks guys 
This box should be fully ubunu'ed up when I make my next post
TTFN

---

### Post by Nitro Fan on 2008-03-01
its done! 

Posted from an Ubuntu machine

---

