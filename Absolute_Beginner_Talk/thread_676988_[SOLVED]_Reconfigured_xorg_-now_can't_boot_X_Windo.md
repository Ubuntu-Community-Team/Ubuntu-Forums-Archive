---
title: "[SOLVED] Reconfigured xorg -now can't boot X Window"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by _Azrael_ on 2008-01-24
**update: please forgive the long post - I'm trying to cover all angles

This post is my last resort before reinstall. I just updated *all* packages on my new Gutsy so I'd rather avoid reinstall if possible.

_Relevant system details:_  -Intel core2 e6400  (ergo Gutsy_amd64)   -Palit nVidia GeForce 7600GT (drivers used: nvidia-glx-new.100.14_amd64) -gnome desktop

_Problem origin:_
To enable desktop effects I installed the nvidia drivers above. I was then limited to 1024x768 resolution. I tried[FONT="Courier New"][COLOR="Blue"] dpkg-reconfigure -phigh xserver-xorg[/COLOR][/FONT] to get a higher resolution. The first time I did it, I messed up and didn't select the resolution I wanted. Gutsy booted fine after that for the last time...:( After using [COLOR="Blue"]*dpkg*[/COLOR] again I cannot boot back into X Window (safe mode works).

_Symptoms:_
-On bootup in verbose the system hangs after the point: [COLOR="Blue"][FONT="Courier New"]running local boot scripts (/etc/rc.local)...[OK][/FONT][/COLOR]
-When [COLOR="Blue"]xorg.conf[/COLOR] is set with the nvidia drivers, their logo is displayed in a loop a few times -then the system hangs. When [COLOR="Blue"]xorg.conf[/COLOR] is set with [COLOR="Blue"]nv[/COLOR] the loop still occurs, just without the logo (the screen flickers a few times before hanging).
-Pressing ctrl+alt+del at the hang in safe mode displays [COLOR="Blue"][FONT="Courier New"]stopping GNOMEDisplay manager[/FONT][/COLOR] and the reboot is quick. Ctr+alt+del at the hang from a normal boot seems to take much longer to reboot with no display of any kind.

_Attempted solutions (which failed miserably):_
-tried to setup xorg.conf with the command [COLOR="Blue"][FONT="Courier New"]nvidia-xconfig[/FONT][/COLOR]
-tried uninstalling (not purging) nvidia drivers & reconfiguring xorg.conf again
-tried looking at /etc/rc.local (didn't understand)
-tried updating usplash (suggested in amd_64 forum)

Can anyone offer a direction I might be able to pursue? Also I'm new to the open source community. I saw a few bug reports that resembled my problem. Should I add this long winded description as a bug report? I would like to start contributing back in some way too. Thanks for any help...

---

### Post by PmDematagoda on 2008-01-24
Did you try reinstalling the Nvidia driver and reconfiguring your X-Server?

---

### Post by _Azrael_ on 2008-01-24
Yes, I tried reinstalling the nvidia drivers and reconfiguring -same problem occurs. > "..I can make it unstable in a few hours" :) LOL

---

### Post by _Azrael_ on 2008-01-24
** update:

This seems to be a case of the following confirmed bug:

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/145112]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/145112")

The strange thing is that X system is still inaccessible when the nVidia drivers are removed and xorg.conf reconfigured. Having backtraced a few steps, one would expect the system to return to it's previous working state.   

Anycase I'm bombed after spending nearly 9hrs solid on this. I'll try the hack in the above link tomorrow and if it doesn't solve things I'll add to the bug report and reinstall. Any further advice would be greatly appreciated.

---

### Post by jrickard on 2008-01-24
I haven't done anything that I know of except download and install updates.  Just rebooted my system and have exactly these symptoms, hang on local.rc scripts, and multiple logon cycle.

Ran ENVY and get 800x600 screen.  NVIDIA tells me the xorg.conf isn't using their driver.  Ran sudo nvidia-xconfig and rebooted.  Same problem.

Intel Core 2 Extreme QX6850 with Nvidia 8800 Ultra

Jack Rickard

---

### Post by _Azrael_ on 2008-01-24
It's frustrating. Based on the bug report above it looks like lots of x86 architectures are having problems with Gutsy and the latest nVidia drivers. 

What started this whole thing for me was not being able to go above 1024x768 with the nvidia-glx-new drivers (100.14_amd64). Using [FONT="Courier New"]dpkg *x y z*[/FONT] caused this boot problem.

I found some hope again though.  I was experiencing the same limitiation with screen resolution in Fedora. I browsed the forums and found this:
[http://ubuntuforums.org/showthread.php?p=4147612]("http://ubuntuforums.org/showthread.php?p=4147612")

Following FuturePilot's advice, (thanks man!) entering [FONT="Courier New"]nvidia-settings[/FONT] (as root) brings up a fully functional driver tool which allows you to customise your resoultion and refresh rate. Fedora is looking superb now.

I'm going to mess around a bit in recovery mode and see if any progress can be made. If you can just get around that hang, [FONT="Courier New"]nvidia-settings[/FONT] is the way to setup your display for sure! Hope you come right!

---

### Post by _Azrael_ on 2008-01-25
Some progress this morning:

-In recovery mode, backed up xorg* files in /etc/X11 then deleted all of them
-This allowed me to to boot back into X Window\\:D/

Now busy reinstalling nVidia drivers using ENVY. Will try using [FONT="Courier New"]nvidia-settings[/FONT] to change screen resoultion as well as [FONT="Courier New"]dpkg-reconfigure xserver-xorg[/FONT]. Will post events if scenario reoccurs.

---

### Post by _Azrael_ on 2008-01-25
Gutsy's running beautifully in my native res with all the effects I wanted to show her off to the clones in my home ;) 

The problem seems to be caused by the older nVidia drivers (100.14) which were installed by the default package manager. Envy got the most current release (169.09) which apparently addresses this X window lock. (see [http://nvnews.net/vbulletin/showthread.php?t=106661]("http://nvnews.net/vbulletin/showthread.php?t=106661"))
As you see these drivers are very new so I'm anxious of future problems -but for now things work great! 

If you also cant boot X window after installing driver 100.14 here's a summary of what fixed it for me:

-back up xorg* files in /etc/X11 : [FONT="Courier New"][SIZE="1"]tar -cvzf backup.tar.gz xorg*[/SIZE][/FONT]
-delete xorg files: [FONT="Courier New"][SIZE="1"]sudo rm xorg*[/SIZE][/FONT]
-joy as X terminal boots:biggrin:
-reinstall latest nvidia drivers (I used ENVY in system tools -thanks tseliot!)
-setup the drivers from terminal with file permissions [FONT="Courier New"][SIZE="1"]sudo nvidia-xconfig[/SIZE][/FONT]
-setup your screen settings from terminal with file permissions[FONT="Courier New"][SIZE="1"]sudo nvidia-setup[/SIZE][/FONT]

---

