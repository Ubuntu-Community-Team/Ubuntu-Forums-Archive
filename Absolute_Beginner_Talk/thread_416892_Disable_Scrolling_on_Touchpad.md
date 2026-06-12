---
title: "Disable Scrolling on Touchpad"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by tm0054 on 2007-04-21
I looked around in the mouse settings and can't seem to find this:

I'd like to disable the regions of the touchpad that cause the screen to scroll (A thin portion of the right of the touchpad scrolls the screen up and down, and the bottom scrolls the screen left and right).

Does anyone know how to disable this feature in Feisty?

Thanks!

---

### Post by ViGiLnT on 2007-04-21
Edit the /etc/X11/xorg.conf file:

After the line 

```
Option "HorizScrollDelta"	"0"
```

insert:

```
Option "VertScrollDelta"	"0"
```

If you want to disable the click feature add this:

```
Option "MaxTapTime" "0"
```

---

### Post by Pobega on 2007-04-21
Or you can run "gsynaptics" and configure your touchpad from there; That is, if you are using a synaptics touchpad.

---

### Post by tm0054 on 2007-04-21
Thanks! Editing the xorg.conf file worked perfectly! I'm no longer scrolling wildly, Plus my laptop has a nice four-sided scrolling button built right into the touchpad that works great with Ubuntu.

---

