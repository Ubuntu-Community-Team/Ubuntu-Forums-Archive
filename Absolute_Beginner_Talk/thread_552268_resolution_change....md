---
title: "resolution change..."
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by ckarymesogeios on 2007-09-16
Dear all, I have downloaded and installed the drivers for my vga card (ATI MOBILITY RADEON 9700) but I can't change the resolution of the screen. I have tried through the terminal but with no results. Is there any program through which I can do it?Little help please...

---

### Post by autocrosser on 2007-09-16
Please upload your xorg.conf (found in /etc/X11/xorg.conf)--you will need to rename the file by adding .txt after it--the forum won't allow .conf

You should have a control panel in Menu>System>Preferences>Screen Resolution to change things. You can also add a panel applet via Synaptic to gain more direct access.

---

### Post by por100pre1 on 2007-09-16
> **autocrosser said:**
> Please upload your xorg.conf (found in /etc/X11/xorg.conf)--you will need to rename the file by adding .txt after it--the forum won't allow .conf

You should have a control panel in Menu>System>Preferences>Screen Resolution to change things. You can also add a panel applet via Synaptic to gain more direct access.

This is better:

```
cat /etc/X11/xorg.conf
```

and post the results...

(If the OP renames the original file instead of the copy, the OP could get in trouble.)

---

### Post by autocrosser on 2007-09-16
Very true---forgot to add the copy/paste into a text file:)

My bad----in any case--we need to see what resolutions are included in the xorg.conf

---

