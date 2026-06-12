---
title: "Installing ubuntu on 2 hardrives beside xp"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by umfufu on 2007-12-30
Hello everyone, 

Because i am a complete newbie tho this i would like tho ask some questions about installation of ubuntu on my computer with 2 HD (on one xp).
1. wich ubuntu do i need to install ? X86_64 or i 386 version, i tried both allready in live cd version (they both work).
2. What do i have to do to install ubuntu beside XP on the other HD? so ican use both for now.
3. when i start after booting: only save graphics mode works. All the other options d'ont work.
My configuration is as follows:

1. Intel pentium D CPU Ghz
2. 81801GR/GH SATA AHCI Controller
3. 2 Hard drives WDC WD2500JS-75N
4. NV41.1 Geforce 6800
5  Sound card creative labs X-Fi Xtreme music
6. Dell 24'' widescreen lcd 

And some other Stuff but i dont think you need this because everything seems tho work in save graphics mode except sound, in save mode monitor. but i wil try to fix that later.

Greetz

---

### Post by logos34 on 2007-12-30
Use x64 if you can.  The package list is vitually identical.

If you install ubuntu on the second hard disk, grub boot loader will be written by default to the MBR of the first disk (XP), overwriting the windows boot loader.  There shouldn't be a problem, and when you reboot you'll have a grub menu where you can choose either linux or windows.

First thing to do after rebooting into your new ubuntu installation is [fix the grpahics]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#NVidia_Driver").  System>admin>restricted drivers>enable nvidia

If X server fails to load and drops you at the console prompt, run interactive graphics tool

**sudo dpkg-reconfigure xserver-xorg**

choose 'vesa' driver.  You can accept the defaults for most of the rest. Hopefully that will get you to the desktop

---

### Post by eternicode on 2007-12-30
1) According to a post at [LinuxQuestions.org]("http://www.linuxquestions.org/questions/linux-software-2/i386-vs.-x8664-413527/"), x86_64 is for 64-bit processors, i386 for 32-bit.

2) Easiest way would be to make sure the second HDD is empty (move all data to your windows drive), then let Ubuntu (or whatever you want to install) use the entire second HDD.

3) causes for graphics issues pretty much depends on the graphics card you're using.  Since you're using NVidia, try logos34's suggestion.

---

