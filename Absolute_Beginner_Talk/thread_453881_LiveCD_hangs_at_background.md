---
title: "LiveCD hangs at background"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by PedroDaGr8 on 2007-05-24
Hello,
I asked this question in the IRC channel and no one was able to help so I am going to ask it here. I am trying to run ubuntu from the liveCD. I have checked the MD5 hash and it came out correct, burnt it to 5 CDs so far hoping it was just that, they all checked out using the integrity check. Now the problem. When I choose to Run/install Ubuntu, the system starts loading all of its various things, but a recurring error message comes up about the wireless card not being able to send an SSID. It then shows the desktop background (the orangish-brown wallpaper), but nothing more. No menus load and all HD and CD drive access stops. If I enter Alt-F1 verbose mode, the same exact error is there. Here are all the pertinent stats I can think of about my computer:
Toshiba Satellite A105-S361
Intel Pentium M 2.00Ghz
1024MB DDR2 ram
Wireless Card is an Intel 2200BG Centrino (to be exact the sticker at the bottom says it is WM3B2200BG).

I would appreciate any assistance with this problem. THanks.

Also, this is my first time trying to get used to linux. I have used unix a lot in the past but just mainly basic stuff like running my quantum mechanical calculations or using VI etc.

---

### Post by ayenack on 2007-05-24
I'd say your best bet is to try the alternate CD. I've had problems in the past with live CD's not installing. Do you enable wireless networking (System>Administration>Networking) with the live CD and if so can you get on the net? What network card are you using?
You might also try turning your wireless card off, this may work. Then install and turn it back on and configure it when the system is up and running. This card should work right out of the box with no issues it's supported in Ubuntu.

ayenack.

---

### Post by Dzenhax on 2007-05-24
Try this advice:

[http://ubuntuforums.org/showthread.php?t=453536](http://ubuntuforums.org/showthread.php?t=453536)

If you can run the live CD fine, then it may be the way xorg.conf was configured at install.  I had that happen once (I was using the alternate install) and this is how I fixed it.

You can get a command prompt by pressing ctrl-alt-f2 or 3 or 4 or 5 .. f7 is the graphical that you can't get to come up.

---

