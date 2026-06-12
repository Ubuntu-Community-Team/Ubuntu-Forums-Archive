---
title: "Powerbook - External Monitor Support?"
date: 2005-10-01
forum: Apple PPC Users
---

### Post by fl1pper on 2005-10-01
Install was a breeze (no pun). I'm fully updated. 

On an Aluminum 1.25 Gig/1GB ram, blah blah blah.... just as with a previous Debian install, I see no way to access the external monitor I use normally. 

The Radeon 9600 is recognized right away (a big improvement over the most recent Deb distro, by the way). resolution switching, no probs (also a improvement over the Deb distro).

But I have to kill the external to avoid burning in the wacky horizontal gibberish thing. None of it's life and death, but has anyone figured out a script, or edit, to get the /dev thing happening for an external CRT? 

Thanks  :)

---

### Post by kwa on 2005-10-15
This works fine for me. edit your /etc/X11/xorg.conf file, and modify these bold lines in the "Device" section to look like this:
```
Section "Device"
     Identifier     "ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
     Driver         "ati"
     [B]Option        "UseFBDev"      "false"
     Option        "MergedFB"      "true"
     Option        "CRT2Position"  "LeftOf"[/B]
EndSection

```

The "CRT2Position" option is pretty strait forward. The value "LeftOf" means your external monitor will be to the left of your powerbook's display. You can also use the values, "RightOf" and "Center", which is mirror mode.

Then restart your X server with "/etc/init.d/gdm restart"

---

### Post by xamat on 2005-11-22
It works with LeftOf and RightOf for me but not with Center. Then I get a message from the monitor telling me that it cannot work on that particular video mode. How can the video mode be different if I choose Center instead of LeftOf???:confused:

---

