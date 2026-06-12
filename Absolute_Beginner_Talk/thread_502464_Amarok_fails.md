---
title: "Amarok fails"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by RedKyuubi on 2007-07-16
A

---

### Post by RedKyuubi on 2007-07-16
sorry.. i accidently typed enter... but anyways I tryed everything i can thing of to get amarok to run but it starts load up then dies as the logo screen disappears. I have the newest version of everything, and yet it still fails miserable. 

> redkyuubi@ThePub:~$ amarokapp
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x813e108 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x813e108 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
Amarok is crashing...
Running: gdb --nw -n --batch -x /tmp/kde-redkyuubi/amarokWxHOuc.tmp amarokapp 8741

warning: no loadable sections found in added symbol-file /usr/lib/libtheora.so.0
Running: file `which amarokapp`
1.4.5 [___stripped][validity: 0.13][frames:  55][]

Amarok has crashed! We are terribly sorry about this :(

But, all is not lost! Perhaps an upgrade is already available which fixes the problem. Please check your distribution's software repositor

If this was already answered i have not found it, and would be just as happy with a finger pointing me to where it is.

---

### Post by forestpixie on 2007-07-16
do you get same response running amarok instead of amarokapp?
what happen if you run it from the menu?

---

### Post by RedKyuubi on 2007-07-16
same thing

---

### Post by odiseo77 on 2007-07-16
Have you tried removing ~/.kde/share/config/amarokrc and ~/.kde/share/apps/amarok/ and starting amarok from scratch to see if it works?
(You'll loose all your amarok configuration, obviously, but maybe it works).

---

### Post by orbital on 2007-07-19
I had the same problem and this solved it, thanks!

---

