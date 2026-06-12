---
title: "Numlock stopped working"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by whein on 2006-09-04
Ok, so everything seemd all happy and working a few days ago.  I'm using a wireless keyboard and mouse combo from Logitech and Gnome seemed to have no problem with them.  Then a few days ago I installed compix + xgl.  Now my numlock button doesn't seem to work and the keypad only executes the non-numeric functions like insert and pagedown.  I've tried rebooting, selecting the default Gnome session instead of compiz, nothing seems to make a difference.   I also now get a message dialog on login that says the X keyboard settings and Gnome keyboard settings don't match, which would I like to use?  I've tried both options and neither fixes the problem.  I don't know if compiz caused the problem, but I only noticed it after the install.  Help!  Any ideas?

A couple more datapoints: the numlock LED turns on and off on the wireless receiver, but when I go to Keyboard Shortcuts and try to assign numlock to an unused function it doesn't seem to recognize that a key was pressed.  Not sure if it is supposed to for numlock.
:(
-Will

---

### Post by whein on 2006-09-06
Ok, further investigation.  I tried switching from the wireless to a wired keyboard to rule out that.  The wired keyboard behaved the same way.  I tried installing the gkrellm-leds plugin but it was giving me some error about not being able to resolve names on the x-server so I would not be able to set/get the led status.  Not sure if that is related or a separate problem.  Then, on a random inspiration I decided to try holding down the numlock key while using the number pad.  BINGO!  For some reason the numlock key now works as a modifier like the Shift key instead of a state like the caps-lock key.  Ok, now how do I fix this and make it go back to being state based like it should be?
-Will

---

### Post by whein on 2006-09-07
/BUMP
Anyone?  Help please?  :(

---

### Post by DarthBlingBling on 2006-09-14
I'm going to bump this too as I have the exact same problem, got Xgl and compiz to finally work and now my numlock no longer works.
Must be something to do with the keyboard layout as when I went to check it out it was set to unknown, and the list of keyboards is now empty!!
So i'm lost as to what to do.

---

### Post by whein on 2006-09-14
Well, I made a little progress.  I ran gconf-editor from a terminal and under desktop->gnome->peripherals->keyboard-><my computer name>->kbd I noticed that the keyboard layout and model were blank so I copied the vales from kbd.sysbackup which were layout [us] and model pc104.  Now the keypad works only with the number functions (which is fine for me) but I cannot toggle back to using the alternate functions.  I think I saw a key in gconf somewhere about numlock always on, so I'll hunt around a little and see if that will help, but at least for now I'm happy since I never used the alternate functionality of the keypad anyway.  :)
-Will

---

### Post by Paul41 on 2006-09-14
I had some strange things happening like this before and fixed it by choosing a different keyboard layout.

System->Layouts

I originally had it set to a Dell keyboard since that is what it is, but changing to a generic keyboard fixed my problem.

---

### Post by DarthBlingBling on 2006-09-15
But my layout list is empty so I cant pick another layout.
Where did you find the kdm.sysbackup?

---

### Post by whein on 2006-09-18
> But my layout list is empty so I cant pick another layout.
Where did you find the kdm.sysbackup?
Darth,
open up a terminal and run
```
gconf-editor
```
This should open up a window very reminiscent of the registry editor in Windows (only much easier to comprehend).
Under the desktop->gnome->peripherals->keyboard->[computer name]->kbd path there will be two keys named layout and model.  Both of mine were blank and I'm betting yours will be too.  Right click on them and manually set the values as described above.  This is not really the correct fix, but it gets the numbers working on the keypad instead of the alternate functions (though you can't use the alternate functions afterwards).  For me this was acceptible.  YMMV
-Will

---

### Post by Solow on 2006-09-18
Thank You gays. Had exactly the same problem.

---

### Post by DarthBlingBling on 2006-09-20
Cheers, working now!

---

### Post by chiklit on 2006-10-10
I tried editing the entries in gconf-editor but when I restarted they were back to being blank. Do I need to save them somehow? Also, my caps lock key isn't working either.

---

