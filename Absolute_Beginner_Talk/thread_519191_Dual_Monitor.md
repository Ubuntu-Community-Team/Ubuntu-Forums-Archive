---
title: "Dual Monitor"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by nhandler on 2007-08-06
Well, the one piece of hardware I haven't gotten to work with Ubuntu in the year I've been running it is my second monitor. I have a* Dell Inspiron 6000* (Laptop) with an *Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller* graphics card. The second monitor is a *Samsung SyncMaster 151v*. I am attempting to set up an extended desktop. I have tried various guides in the past, but have been unable to set this up correctly. If anyone could help, it would be greatly appreciated.

---

### Post by dmjones500 on 2007-08-07
My friend set up my computer to use two Samsung SyncMaster 940Ts.

I'm not sure quite what he did, but I've attached my xorg.conf file (renamed to xorgconf.txt so I could upload it)  for you to ponder over.

Hopefully you can try merging parts of it with your existing xorg.conf file (after backing up) and see what happens??

Good luck!

Edit:  I should mention that this is a desktop machine with two monitors, not a laptop with an extra monitor, so there may be even more differences between my xorg.conf and what you would need for your setup!!

---

### Post by nhandler on 2007-08-10
Does anyone else know how to accomplish this? I'm not that confident about merging the two xorg.conf files, especially because I don't have the same setup.

---

### Post by bodhi.zazen on 2007-08-10
Laptop monitors: (see also Dual Monitors)
	Best: [http://ozlabs.org/~jk/docs/mergefb/](http://ozlabs.org/~jk/docs/mergefb/)
	xorg.conf: [http://www.linux-on-laptops.com/forum/showthread.php?p=1253](http://www.linux-on-laptops.com/forum/showthread.php?p=1253)


Dual monitors, Ubuntu thread:
		[http://ubuntuforums.org/showthread.php?&t=308673](http://ubuntuforums.org/showthread.php?&t=308673)

	Switch xorg.conf :
		[http://ubuntuforums.org/showthread.php?t=308673](http://ubuntuforums.org/showthread.php?t=308673)

see if one of those links help (sorry, it has been a while since I looked through them)

---

### Post by myk.dinis on 2007-08-11
Here is a working xorg.conf with i810 drivers for your chipset...

[http://www.baka.org/private/xproblem/i810-2screen-work/xorg.conf](http://www.baka.org/private/xproblem/i810-2screen-work/xorg.conf)

Now you need to change 2 things...1 change the layout... (instead of Above) you'll change it to either leftof or rightof...
And 2, add this...inside the server layout section for dual

SubSection "ServerFlags"
  option "Xinerama" "true"
EndSubSection


and a second Server Layout with the identifier being "Default Layout" and in that one leave out the second screen info so it looks like:

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "Screen0" 0 0
	InputDevice    "Keyboard0" "CoreKeyboard"
	InputDevice    "Synaptics Touchpad"
	InputDevice    "Mouse0"
        SubSection "ServerFlags"
                option "Xinerama" "false"
        EndSubSection
EndSection

What that means is that you'll have that layout all the time (hence "Default Layout") if you want the other one just switch the identifiers...
Those will be the two you can choose...

Now...this is IMPORTANT...If you want to choose the other layout you need to logout (back to the login screen) log in to a teminal session...no x...

Then you will type startx -- -layout dual
this will start x with the other layout...

This isn't the most elegant solution, I'm sure...But it should get you on the right track...
Also...you have to remember I am not an expert...Just trying to help...

remember you need te i810 drivers...they will run your card right...reference this article for more info.....
[http://lists.freedesktop.org/pipermail/xorg/2007-May/024411.html](http://lists.freedesktop.org/pipermail/xorg/2007-May/024411.html)

BTW, please PM me if you have success with this solution...thanks!

Myk

---

