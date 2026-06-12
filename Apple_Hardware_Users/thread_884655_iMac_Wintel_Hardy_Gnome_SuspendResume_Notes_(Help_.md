---
title: "iMac Wintel Hardy Gnome Suspend/Resume Notes (Help Save the Planet)"
date: 2008-08-09
forum: Apple Hardware Users
---

### Post by texadactyl on 2008-08-09
Assumption: You are using the fglrx driver for ATI accelerated graphics that comes on the iMac motherboard.  Any other X driver is an inferior experience and probably garbage to look at.

My iMac: 20-inch circa October 2007.

_**Suspend/Resume**_

Does you iMac get really hot, especially in the rear upper left-hand corner?  You can help yourself and help save the planet a little bit as well.

Enable suspend/resume by this set of Gnome menu actions:

1. System -> Preferences -> Power Management.
2. On AC Power: Use finite values of your choosing for *Actions* and *Display*; I am using 20 minutes each.
3. General tab: I have set both button presses to go to Suspend.

Net effect:
Push power button in rear for resume from suspend.
I also can use the power button to suspend manually.

But, wait.....you are not done yet.

_**Unfortunately, the fglrx module needs extra attention in acpi.**_  

Here is a recipe that worked for me:

1. In */etc/default/acpd-support*, to avoid suspend-hang problems, set
[INDENT]*MODULES="fglrx"* (or add it to the existing list)[/INDENT]
2. Reboot because */etc/init.d/acpi-support restart* with the fglrx module does not seem to be currently not reliable.  But, suspend/resume will work after a reboot.
3. Using *gconf-editor* on the command line, go to apps -> gnome-power-manager -> lock
[INDENT]Recommendation: Check on use_screen_savers.
This will synchronize Gnome power saving security with screen saver security.
Otherwise, there are 2 asynchronous security processes.  
I prefer cooperative synchronous processes.[/INDENT]

_**USB Mouse and Keyboard**_

If you are using a USB mouse and keyboard, they probably will not cause Ubuntu to wake up from suspend.  Use the power button for wakeup.  

It might be possible to add the USB modules to the keep list in */etc/default/acpi-support* so that mouse or keyboard action will cause resume but this will also defeat some of the power-saving purpose and may carry risk of being a pioneer [(^;]; I did not try this as I need to get back to work (software development).  

I chose to use the power button for resume after suspend.

**~.~.~.~.~.~.~.~.~.~.~.~.~.~.~.~.~.~.~.~.~.~.~.~.~.~.~.~.~.~.~.~.~.~.~.~.~**

So far, so good.  And, my iMac never gets hot any more.

Never figured out how to make hibernate actually work; it keeps going into an udefined state.  However, I don't think that I need it.

Bye bye.........Richard

---

### Post by cyberdork33 on 2008-08-10
> **lemon8h8ead said:**
> Never figured out how to make hibernate actually work; it keeps going into an udefined state.  However, I don't think that I need it.
Do you have enough swap?

---

