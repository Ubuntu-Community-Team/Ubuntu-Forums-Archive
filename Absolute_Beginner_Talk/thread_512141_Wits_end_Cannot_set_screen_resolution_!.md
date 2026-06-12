---
title: "Wits end Cannot set screen resolution !"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by techuser on 2007-07-28
I don't know about you but I cannot stand working on a desktop that is less than 1280x1024. The programs I use need so much space to display that to see anything that is the minimum resolution.
I REALLY need help. 
My system was fine : 7.04 fiesty running Beryl everything booting. everything running. The screen resolution was perfect.
I decided to play with Compiz-Fusion. I found one thread and followed the install instructions. (Not too bright on this side of the screen) The install went well enough but afterwards no handles to move windows and no buttons.  Again I did searches and found suggestions - after following those No keyboard or mouse reaction. The mouse moved but could activate nothing. Keyboard commands were useless.
I rebooted to my PCLinux install and hit the forums again. Got some tips and started uninstalling the files recommended.
Bottom line is I cannot seem to get the Nvidia Ti 200 driver for my Samsung Syncmaster to properly install to the state they were before this mess.
When I go to screenresolution in preferences only 800x600 is the highest value. In the .config file the proper values are there. The .config file shows nvidia legacy drivers as default.
The system boots and has restricted drivers manager showing nvidia accelerated drivers as active. The desktop effect will not run. 
I am sooooo frustrated but I know I must have been on the right track at least a dozen times. I really need some advice on how to step by step get the correct screen resolution. Get beryl back running.

Thanks for any who take on  this challenge
:popcorn:

---

### Post by p_quarles on 2007-07-28
All those warnings about Beryl and Compiz Fusion not being for beginners are basically saying: Go ahead and play with this, but if it breaks your system, be prepared to reinstall from scratch. 

If you want advice on how to fix it, you should go to the appropriate forum (Desktop Effects & Customization). My advice, though, is to backup your data as well as you can, and reinstall. 

Also, please read this sticky:
[http://ubuntuforums.org/showthread.php?t=349732](http://ubuntuforums.org/showthread.php?t=349732)

---

### Post by hammad1337 on 2007-07-28
> I don't know about you but I cannot stand working on a desktop that is less than 1280x1024.
Please do not "bite the hand that feeds you". Even I don't like working in uber-low screen resolution.

try this:
```
sudo dpkg-reconfigure xserver-xorg
```
or try restoring your /etc/X11/xorg.conf file to a backup. The backup will be in the same path with a name like xorg.conf.123456789

Hope this helps...

---

### Post by techuser on 2007-07-29
I use the sudu dpkg-reconfigure xserver-xor
In the selections I use the nvidia option and make sure the only screen size marked is 1280x1024 with 24 bit
After all that when I boot I still get 800x600
Go figure

---

### Post by Jan Eppo Jonker on 2007-07-29
There might be a clue in /var/log/Xorg.0.log

---

### Post by Myglaren on 2007-11-18
> **Jan Eppo Jonker said:**
> There might be a clue in /var/log/Xorg.0.log

Just installed Gutsy on this ancient Duron machine, Nvidia Riva TNT card. the Xorg.0.log says that anything higher that 800x680 is out of range but it was fine with Dapper?

Dual boot with XP and there is no problem there.

---

### Post by Myglaren on 2007-11-18
Fixed - from another thread, went to System, Screens & Graphics, it had a Generic Plug & Play monitor selected.  Changed that to the correct one (AOC 7vlr) rebooted the X server and all is well again.
Actually is is so small now I can barely see it, may have to tweak it a bit.

Got a nice Nvidia splash screen on reboot, that has never happened before.

---

