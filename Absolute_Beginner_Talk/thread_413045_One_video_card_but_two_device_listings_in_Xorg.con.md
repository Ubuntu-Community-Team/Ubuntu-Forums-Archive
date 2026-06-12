---
title: "One video card but two device listings in Xorg.conf"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by Supercross on 2007-04-18
I have been having some video problems leading to lockups which I detailed in a previous thread.  For the most part these lockups have resolved themselves, although I want to try Fiesty in the next couple of days and see if they exist there.  However, I was looking through my xorg file and I noticed there were two instances on "Device" with two separate parameters.  I have an ATi Radeon 9500 and maybe this is normal for this card since it has the capability for two displays.  I just wanted to know if this is normal and if I should do something about this redundancy.  I am using the latest fglrx driver.
```

Section "Device"
	Identifier  "ATI Technologies, Inc. R300 AD [Radeon 9500 Pro]"
	Driver      "ati"
	Option	    "UseFBDev" "true"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "on"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection
```

---

### Post by crispy_420 on 2007-04-18
Don't worry it is nothing. Mine has the same lines in xorg (9800 Pro here).

---

### Post by lotacus on 2007-04-18
One may be your on-board video. But since the second reference doesn't have a bus ID, you shouldn't have any problems. You can remove that too if you wanted.

---

### Post by crispy_420 on 2007-04-18
I would not delete it tell we know what exactly it is. NOthing worse than a reboot and no gui. I don't have onboard video but it is there. I say leave it alone, it isn't harming anything.

If you really must mess with it, just comment it out (#). That way you can easily fix via nano /etc/X11/xorg.conf.

---

### Post by freebird54 on 2007-04-18
When you installed the fglrx driver, and ran the aticonfig tool, it ADDS the new device, and ignores the old one.  If you look at the 'Screen' section, you will see which section is actually used.  (probably the one marked **aticonfig-Device[0]**)

There may be other duplicate sections too - but only the ones referenced in **Screen** and **Server Layout** matter....

Hope this helps!

---

### Post by Supercross on 2007-04-18
Alright, so the duplicate entry apparently does not matter.  However, I do have another question.  When I originally had my lockups someone told me to paste my xorg.conf output and under devices there were no "Option" parameters, apparently because I never configured the driver after I installed it.  So someone pasted their options from a similar card (9550 I think) and I put them into mine.  They were VideoOverlay On and OpenGLOverlay off.  This apparently solved my lockup issues but now screensavers would never start and it would just go to a black screen, albeit with no lockups.  When I switch it back to ON and I leave my computer for a while idling, I would come back and my screensaver would be frozen onto my screen and I would have to hard reboot.  My big question is, what exactly does the OpenGLOverlay parameter do, and why would it cause my screen to lockup on me?

---

### Post by freebird54 on 2007-04-19
Hey - that might have been me :)  There are a number of the screensavers that call on OpenGL to operate, and they seem to have a problem with an ATI card set up to run XGL (at least with fglrx drivers).  I don't have an answer, except not to use those screensavers. (so far).  Things like Gleidoscope(sp?) and so on are particularly bad - and things like Cosmos are fine - no lockups.  Sorry couldn't be more helpful (yet - still trying to find out more)

---

