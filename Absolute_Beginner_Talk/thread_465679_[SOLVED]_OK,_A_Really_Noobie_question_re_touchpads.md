---
title: "[SOLVED] OK, A Really Noobie question re touchpads"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by john wagner on 2007-06-05
Here I go again, displaying my ignorance....  But...  I have an Hp Pavillion dv5220us laptop that I'm running Ubuntu, Dapper Drake 6.06 on (in case it matters, 2 gig ram, 160 gig HD).  

My Noobie question is, How do I configure the touchpad?  I want to switch off the hover function(the function where the cursor self-selects whatever it happens to be over to open).  I hate it.  I've been to the mouse and keyboad choices on **SYSTEM>MOUSE & KEYBOARD**.  No luck.

Oh yeah, I got another problem re **SKYPE (FOR lINUX)**.  I installed it, it gave me problems with an incorrect login, so I removed ALL files/dependencies.  EVERYTIME I DOWNLOAD ANOTHER VERSION, IT GOES STRAIGHT TO THE WRONG INFO!  I thought that by removing everything, the data would be gone?  HELP!!!!!

Thanks, in advance!

john

---

### Post by kerry_s on 2007-06-06
i know the feeling, damn sensitive touchpad. the best i know is to turn off the tap, so you will have to use the buttons instead.

sudo gedit /etc/X11/xorg.conf

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	    "0"
                   Option                         "MaxTapTime"               "0"
EndSection
```

---

### Post by john wagner on 2007-06-06
> **kerry_s said:**
> i know the feeling, damn sensitive touchpad. the best i know is to turn off the tap, so you will have to use the buttons instead.

sudo gedit /etc/X11/xorg.conf

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	    "0"
                   Option                         "MaxTapTime"               "0"
EndSection
```

Thanks!  That seems to work just fine!  I never use the tap function anyway!  Now, any advice re the Skype question???

Heh...

---

### Post by john wagner on 2007-06-06
> **john wagner said:**
> Thanks!  That seems to work just fine!  I never use the tap function anyway!  Now, any advice re the Skype question???

Heh...



Hmmmm, interesting....  I've redone/saved the MaxTapTime edit, it solved the problem...but....  I still have the tap function!  A single, SOLID tap delivers the same result as a click of the ol' buttons!

Strange!

john

---

### Post by kerry_s on 2007-06-06
oops, when ever you make a change in xorg.conf you need to restart X, you can reboot or logout and press ctrl+alt+backspace.

there's proasbly a hidden settings file for skype in your home folder. open nautilus and press ctrl+h to view the hidden files, then just locate and delete the skype one.

---

### Post by Ripfox on 2007-06-06
Yes delete the .skype folder after you uninstall skype and it will erase all settings. Oh, and I use Gizmo instead of skype...it works better imho.

Peace

Ripfox

---

