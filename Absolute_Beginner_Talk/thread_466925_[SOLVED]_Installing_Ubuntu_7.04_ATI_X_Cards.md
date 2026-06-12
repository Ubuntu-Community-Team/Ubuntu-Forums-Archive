---
title: "[SOLVED] Installing Ubuntu 7.04: ATI X**** Cards"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by For the Birds on 2007-06-07
I tried the instructions below and it did work ( I was getting a dark screen after booting into Ubuntu) but once logged into Ubuntu I enabled my ATI driver under Restricted Drivers so that I could install Beryl. Once I did this my wireless card no longer connected and after rebooting  a few times I got the dark screen once again.  Not sure what's going on.  Help will be much appreciated.  



> Many people are having problems installing Ubuntu 7.04 (Feisty Fawn) on machine with ATI X**** series video cards. This is caused by this bug that unfortunately could not fixed before the release of Ubuntu 7.04.

This quick guide will get Feisty installed and X.org 7.2 up and running.

Boot using PC (Intel x86) alternate install CD for Ubuntu or Kubuntu.
Start text mode installer and install Ubuntu/Kubuntu.
Finish Install and reboot.
Update package list and upgrade any packages needed.

Code:
sudo apt-get update
sudo apt-get dist-upgradeInstall fglrx closed source driver for ATI video cards.

Code:
sudo apt-get install xorg-driver-fglrxUpdate loaded modules.

Code:
sudo depmod -aConfigure /etc/X11/xorg.conf

Code:
sudo aticonfig --initial
sudo aticonfig --overlay-type=XvReboot

Ubuntu 7.04 should now boot into GDM/KDM.

---

### Post by Ek0nomik on 2007-06-07
Those instructions are, from what I understand, aimed at users who can't even install Feisty Fawn with the Live CD.

I was one of these users.  The Live CD not once was able to load, so I had to use the alternate installer instead.  Then, once I had Ubuntu installed I had to get to a terminal to execute those commands.

What is the "dark screen"?  Your monitor has a dark tint, or are you not able to see anything?

---

### Post by For the Birds on 2007-06-07
After installing Ubuntu and rebooting, I can see that it is loading Ubuntu but after a few seconds the screen goes black and I can no longer see what's on the screen.  I know it's running something because there is hard drive activity.

---

### Post by Ek0nomik on 2007-06-07
Are you able to boot into command line?

While Ubuntu is loading try hitting Ctrl+Alt+F1 to boot into command line.  Then try following those instructions.

---

### Post by wak_wak on 2007-06-30
To get Ubuntu/Kubuntu working with an ATI card with live CD/otherwise:

Boot, when it freezes Alt F1.

Type Sudo dpkg-reconfigure xserver-xorg

For the 1st part (graphics card) choose Vesa and when it comes to resolution: 1280x1024.

For pretty much e/g else choos default.

Then type startx.  That should work.

---

### Post by orbit1979 on 2007-06-30
I have had nothing but headaches over this issue as well. I have tried every suggestion made with no success. However, by accident, I found an easy way to fix the ATI problem (at least it worked on my machine.)
If your running fiesty, try this:
Click System --> Administration --> Restricted Drivers Manager ---> Click Enable ATI accelerated graphics driver --> Restart your computer.
I did this, and now I have 3D acceleration support. Every thing graphics related works fine now. Hope this helps.

---

### Post by newbie2 on 2007-07-03
[http://ubuntuforums.org/showthread.php?t=490937](http://ubuntuforums.org/showthread.php?t=490937)

---

### Post by lemz on 2007-08-28
> **wak_wak said:**
> To get Ubuntu/Kubuntu working with an ATI card with live CD/otherwise:

Boot, when it freezes Alt F1.

Type Sudo dpkg-reconfigure xserver-xorg

For the 1st part (graphics card) choose Vesa and when it comes to resolution: 1280x1024.

For pretty much e/g else choos default.

Then type startx.  That should work.

worked for me, thank you :) that confug wizard is very intimidating lol

---

