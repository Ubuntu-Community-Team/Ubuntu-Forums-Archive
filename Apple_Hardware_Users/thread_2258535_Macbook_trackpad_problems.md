---
title: "Macbook trackpad problems"
date: 2014-12-28
forum: Apple Hardware Users
---

### Post by Jakesploder on 2014-12-28
EDIT: I meant to put the ubuntu tag on the thread. i am not using kubuntu.

I just installed ubuntu 14.04.1 LTS, and the trackpad is very hard to use as it will not move the mouse unless if i put a lot of pressure on it. any way to change the sensitivity of the trackpad? I tried modifing this file:/usr/share/X11/xorg.conf.d/50-synaptics.conf, but that caused the computer to stop booting.  The computer is a mid 2007 macbook, intel core 2 duo.

---

### Post by este.el.paz on 2014-12-30
@jakes:

I've been working in my PPC iBook this am in Lu 14, Lubun didn't show any Trackpad adjustments, but usually in System Preferences "mouse" is also where "trackpad" will have a tab.  I booted up my Ubuntu MATE live DVD and checked in "Control Center" and again, there was "mouse" . . . so I think the trackpad on my iBook is kaput . . . .  Then, the MATE respin desktop "froze" again for the third time, so I'm back in Lu . . . .

I have LM 17 installed on my '10 MBPro and I can almost guarantee that in "Control center" I have adjusted trackpad settings for "disable tap to click" and "disable while typing" . . . can't remember if "sensitivity" is in the GUI or not.  I did have "issues" with the trackpad in my MBPro . . . posted on this forum and in LM forum when I was back in LM 13 or 15 . . . and some folks did indicate some adjustments to "synaptics" or something in the xorg.conf file to "try" . . . but, didn't want to fiddle with it . . . .  I'll be jumping over to the MBPro a little later on, I'll check on it and see what shows up . . . .  It's probably "easier" to just use a mouse . . . linux doesn't seem to have the apple trackpad "figured out" very well . . . IMHO and in my humble experience of it, etc.

e.e.p.

[Edit:  So, booted up in LM 17, based on Ubuntu, it is Control Center that has the "mouse" preferences, and in there is a tab for Trackpad, but no "sensitivity" bar.  I tried my trackpad and it's fine, I think linux just considers it a "mouse" and the sensitivity for the "mouse" will adjust the trackpad???  Try it, or, like I said, I use a mouse most of the time in my MBPro.  It's easier to krieg around an obstacle than to spend time going through it, or "solving" it . . . .]

---

### Post by Jakesploder on 2014-12-30
I tried to change the 50-synaptics.conf file, and now i can't boot. it gets stuck at a black screen with a small white cursor in the top left corner after the splash screen . Help!

---

### Post by Jakesploder on 2015-01-06
OK, so i took a copy of the synaptics config file from another hard drive, and it booted again. Restarting the machine again, it won't boot. i went to get the file off the hard drive again, but (of course) i dropped it. And it died. Does anybody have a copy of the 50-synaptics.conf file that they could give me?

---

### Post by mcoyle on 2015-01-11
Here's a copy of the 50-synaptics.conf from 14.10.

```


Section "InputClass"
        Identifier "Touchpad"
        Driver "synaptics"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"

EndSection

Section "InputClass"
        Identifier "touchpad ignore duplicates"
        MatchIsTouchpad "on"
        MatchOS "Linux"
        MatchDevicePath "/dev/input/mouse*"
        Option "Ignore" "on"
EndSection

Section "InputClass"
        Identifier "Disable clickpad buttons on Apple touchpads"
        MatchProduct "Apple|bcm5974"
        MatchDriver "synaptics"
        Option "SoftButtonAreas" "0 0 0 0 0 0 0 0"
EndSection


```

---

### Post by Jakesploder on 2015-01-14
Thanks, i can boot now (or at least i could). Mac osx  decided to delete EVERY partition on the hard drive except for the mac os one. I'm now going to install debian instead (mostly because i plan to make my own linux distro.)

---

