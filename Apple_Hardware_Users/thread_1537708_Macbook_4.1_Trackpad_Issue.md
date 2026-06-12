---
title: "Macbook 4.1 Trackpad Issue"
date: 2010-07-24
forum: Apple Hardware Users
---

### Post by n1ghtley on 2010-07-24
I have tried several versions of Ubuntu and many other distros on my black Macbook 4.1, and everything works perfectly except for the trackpad.  The trackpad will not respond to any single-finger gesture unless you place your finger completely flat on the pad (in other words, the trackpad will not pick up input from my fingertip).  Two-finger scrolling works perfectly and is not affected.  I have attempted to fix this problem countless times to no avail, including the use of Gsynaptics.  This is clearly an issue with the generic trackpad driver, and I would be eternally grateful if someone could help me with this problem.

Thanks in advance!

---

### Post by v41 on 2010-07-24
Firstly the touchpad package, xserver-xorg-input-synaptics, ought to be  installed.  It might be worth checking that in the software center.

Secondly try adjusting the touchpad pressure sensitivity by typing the following commands in the terminal:

```
synclient FingerLow=10
synclient FingerHigh=20
```(For details, see the synclient and synaptics man pages).

The effect of the synclient commands will be lost when you shutdown the computer (and possibly after sleep/restore).  If you need help making the change permanent then add another post to the forums.

PS  synclient is deprecated in favor of xinput. Here is a thread on xinput, [http://ubuntuforums.org/showpost.php?p=9377033&postcount=9](http://ubuntuforums.org/showpost.php?p=9377033&postcount=9)

---

### Post by n1ghtley on 2010-07-25
Thank you so much for the advice!  Your fix wiorks perfectly.  I'll be working on a solution to make those changes persist.

---

### Post by NoBugs! on 2010-07-26
This should fix it permanently:
run "sudo gedit /usr/lib/X11/xorg.conf.d/10-synaptics.conf"
Find the touchpad section and add these three lines to the end of the section:
```
Section "InputClass"
	Identifier "touchpad catchall"
	MatchIsTouchpad "on"
	MatchDevicePath "/dev/input/event*"
	Driver "synaptics"

	Option "FingerLow" "10"
	Option "FingerHigh" "20"
	Option "SHMConfig" "on"
EndSection
```

Now it will apply the changes after reboot.
More info here: [https://wiki.ubuntu.com/X/Config#line-26](https://wiki.ubuntu.com/X/Config#line-26)

---

