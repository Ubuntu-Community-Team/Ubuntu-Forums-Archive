---
title: "Error activating XKB configuration"
date: 2008-05-20
forum: Apple Hardware Users
---

### Post by Sparragus on 2008-05-20
Hey there! Everytime I restart the computer (or restart X as well) I get this error.

> Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10400090

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd


The result of xprop -root | grep XKB:
```
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "us", "mac", "lv3:ralt_switch"
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "us", "mac", "lv3:ralt_switch"

```

And The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd is
```
layouts = []
 model = macbook78
 options = [Compose key	compose:rwin]
 overrideSettings = true
```

I'm using Ubuntu 8.04 on a Macbook Core Duo. 

Any help on how to fix this is greatly appreciated.

---

### Post by HuoMaKe on 2008-05-21
I have the same problem, same configuration except with a dvorak variant.

I think it started after I tried switching to a French keyboard (with dvorak variant), but even after I switched back it won't work.

xprop -root | grep XKB:

_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "us-dvorak", "", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "us-dvorak", "", ""


gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd:

 layouts = [us-dvorak]
 model = 
 options = [compose	compose:lalt]
 overrideSettings = true

Any help would be much appreciated.

---

### Post by Rog-Mahal on 2008-05-21
*Bump* Same problem as Sparragus. 

```
:~$ xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "us", "mac", "lv3:ralt_switch"
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "us", "mac", "lv3:ralt_switch"

```

```
:~$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = []
 model = macbook78
 options = [lv3	lv3:ralt_switch,lv3	lv3:switch]
 overrideSettings = true

```

---

### Post by undertakingyou on 2008-06-17
I have the same issue with a third gen MacBook Pro.  Has anyone gotten a workaround here?

---

### Post by cyberdork33 on 2008-06-17
Since this asks for technical information to be posted, it might be helpful to find / start a bug report in launchpad.

---

### Post by undertakingyou on 2008-06-18
> **cyberdork33 said:**
> Since this asks for technical information to be posted, it might be helpful to find / start a bug report in launchpad.

Wonderful suggestion, I guess this should have been my first thought on the matter.  There is a bug here [https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/67188](https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/67188), and it says that it has 7 duplicates.  Interesting also that this has been an issue since Edgy, that doesn't instill a lot of confidence that it will be fixed.  

There is a post on the bug that is noteworthy.  A friend of mine, Christer Edwards, gave a sort of workaround on the matter.  I'll have to check it out and post back if I can find anything.

The reason that this bothers me so much is because NumLock doesn't work.  I figure that the reason is because the keyboard layout isn't set right, so I try and change it and get the bug.  Does anybody else have this same symptom?  Where the NumLock light goes on but the keys don't work?

---

### Post by cyberdork33 on 2008-06-18
> **undertakingyou said:**
> Wonderful suggestion, I guess this should have been my first thought on the matter.  There is a bug here [https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/67188](https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/67188), and it says that it has 7 duplicates.  Interesting also that this has been an issue since Edgy, that doesn't instill a lot of confidence that it will be fixed.  

There is a post on the bug that is noteworthy.  A friend of mine, Christer Edwards, gave a sort of workaround on the matter.  I'll have to check it out and post back if I can find anything.

The reason that this bothers me so much is because NumLock doesn't work.  I figure that the reason is because the keyboard layout isn't set right, so I try and change it and get the bug.  Does anybody else have this same symptom?  Where the NumLock light goes on but the keys don't work?
The numlock thing is actually another bug, but for Apple keyboards only... Pressing F6 twice should turn numlock on/off. There are several issues affecting Apple keyboards right now. Read through these bug reports and see if any of the information helps.
[https://bugs.edge.launchpad.net/mactel-support/+bug/201887](https://bugs.edge.launchpad.net/mactel-support/+bug/201887)
[https://bugs.edge.launchpad.net/mactel-support/+bug/207127](https://bugs.edge.launchpad.net/mactel-support/+bug/207127)
[https://bugs.edge.launchpad.net/mactel-support/+bug/214786](https://bugs.edge.launchpad.net/mactel-support/+bug/214786)
[https://bugs.edge.launchpad.net/mactel-support/+bug/201711](https://bugs.edge.launchpad.net/mactel-support/+bug/201711)

---

### Post by undertakingyou on 2008-06-19
So two things that relate to this thread.  I was able to change the keyboard layout to MacBook/MacBook Pro by running ```
gksudo gnome-keyboard-properties
```  Once I did it as root it worked just fine.  My theory for doing that being that maybe the gnome tool would need to edit the xorg and didn't have the permissions.  I don't know if that is true but, that is what I did.

Second thing: with my numlock issues, I found that if I edited the xorg.conf and added this ```
Option     "XkbOption"     "numpad:mac"
``` my numlocked worked as designed.  I don't know if anyone else had the same problem I did but, that seemed to fix it.

---

### Post by cyberdork33 on 2008-06-20
> **undertakingyou said:**
> So two things that relate to this thread.  I was able to change the keyboard layout to MacBook/MacBook Pro by running ```
gksudo gnome-keyboard-properties
```  Once I did it as root it worked just fine.  My theory for doing that being that maybe the gnome tool would need to edit the xorg and didn't have the permissions.  I don't know if that is true but, that is what I did.

Second thing: with my numlock issues, I found that if I edited the xorg.conf and added this ```
Option     "XkbOption"     "numpad:mac"
``` my numlocked worked as designed.  I don't know if anyone else had the same problem I did but, that seemed to fix it.
gnome and xorg can use two different keyboard settings. That might have actually been the problem.

That is a nifty option, though there really was a bug in the kernel and i think it is supposed to be fixed upstream.

---

### Post by Motorhead Kaze on 2008-06-27
I just developed this bug today. While trying to get over an issue with Gnome breaking down, then going WHITE, somehow my Japanese keyboard settings no longer work. The settings are correct in the keyboard menu, but my keys are wrong for my keyboard now.

I tried going through the terminal 
```
gksudo gnome-keyboard-properties

```
But I got my hopes up too fast, it READS that things are right, but they are not. 

Why in the heck would Gnome and xorg have different keyboard setups?  Any other workarounds for this annoying XKB error issue? Reporting the bug will help people...in like, Jeopardized Jaguar or something like that, but I need this fixed like...by tomorrow?

So, "Bump" and "Bump" again for good measure.

---

### Post by Motorhead Kaze on 2008-06-30
How weird, I am sure I responded to this after I fixed the problem but...

Get into xorg.conf
```

 gksudo gedit /etc/X11/xorg.conf

```
went to "InputDevice" and deleted all these options (the red text)
[code]
Section "InputDevice"
 Identifier "Generic Keyboard"
 Driver  "kbd"
[COLOR="Red"] option us 105
       option japan 106
       option... (something, I forget what it was)
     [/COLOR]
EndSection

I had all these Options right after "driver 'kbd'" that were in conflict with the settings in my keyboard prefs. I deleted all of those options, did ctrl+alt+bksp, then went to system/preferences/keyboard and reset my keyboard to the way I want it (Japanese keyboard, 106keys). Now my keyboard is back to normal.

---

### Post by Ceylo on 2008-12-18
I was having the same "Error activating XKB configuration" message on my MacBook (4,1) with Ubuntu 8.04 because I had chosen the "MacBook/MacBook Pro (Intl)" layout instead of the "Apple" one. I don't really know the differences between these keyboard layouts but everything is working fine now.

---

### Post by ramnarayan on 2009-07-15
Have the same problem and it appeared after updating my 9.04 
so its quite sure some update messed my system up - the question is what ??

> **Motorhead Kaze said:**
> ..

Get into xorg.conf
```

 gksudo gedit /etc/X11/xorg.conf

```
went to "InputDevice" and deleted all these options (the red text)
[code]


ok i tried that but the following are the entire editable contents of my xorg.conf
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2424 1050
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

seems like nothing to do with the keyboard is in it.

??

ram

---

### Post by betaparadogma on 2009-07-26
Same thing here with german USB Apple Keyboard (on Ubuntu 9.04). No AT sign, no EURO, no nothing instead I also receive this funky error message. 

(AT) Motorhead Kaze
Sadly your hint with removing all the trash from the 
/etc/X11/xorg.conf
but in my case there is no entries for "inputdevices" neither!


Please *Mr. Shuttleworth* help us willing Mac guys to switch to Ubuntu... ;)

---

