---
title: "touchpad detected as mouse?"
date: 2012-06-19
forum: Asus Ubuntu Support (CLOSED)
---

### Post by cmullican on 2012-06-19
I've been trying different window managers on my Eee Seashell, and xubuntu is making me happiest, except for a few details.  The worst is that it seems to detect my touchpad as a mouse, so it's not respecting the "disable touchpad while typing" setting. My Settings Manager only has a "Mouse" entry, not "Mouse and Touchpad", and the listing there for the touchpad has a mouse icon.

I've googled every relevant keyword combo I can think of, and tried several solutions, to no avail.  The only touchpad settings I can find with dconf show it already disabled, but that's not what my experience has been -- I'm typing, and the cursor jumps up elsewhere, scrambling my output.

---

### Post by cortman on 2012-06-19
Try running

```
synclient TouchPadOff=1
```

in a terminal, and see if that turns it off.

---

### Post by cmullican on 2012-06-20
That did turn it off, but I don't want to completely disable it -- I just want it disabled while I'm typing.

---

### Post by cortman on 2012-06-20
> **cmullican said:**
> That did turn it off, but I don't want to completely disable it -- I just want it disabled while I'm typing.

Ok, if it didn't work in gpointing-devices-settings, try using Touchpad-Indicator- instructions for installation [here]("https://help.ubuntu.com/community/SynapticsTouchpad#Disabling_Touchpad_while_Typing").

---

