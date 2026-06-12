---
title: "I want to watch a DVD"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by bgast1 on 2007-12-27
This probably has to be something stupid. I want to watch a DVD. Totem comes up but it doesn't start my DVD. I got Kissology volume 2 for Christmas, and I would like to watch it in Linux. Not windows.

---

### Post by taurus on 2007-12-27
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by iris-n on 2007-12-27
The easiest way to do it would be installing ubuntu restricted extras, have you tried it?

Now, the hard way would be installing the xine version of Totem, getting the plugins and libdvdcss form Medibuntu.

---

### Post by bgast1 on 2007-12-27
I got it to work. Next question would be that I see (very faint) lines when the video plays. I went back to Windows and checked it out to see if the same lines appear but they do not. I checked the resolution of my monitor and Gutsy reports that as correct as well. These lines are not something really really bad that I couldn't live with them, I was wondering if there was a way I could get the picture sharper in full screen. I have a 22" LG Flatron Wide screen monitor.

How do you install the Ubuntu restricted extras?

---

### Post by crjackson on 2007-12-27
> **bgast1 said:**
> I got it to work. Next question would be that I see (very faint) lines when the video plays. I went back to Windows and checked it out to see if the same lines appear but they do not. I checked the resolution of my monitor and Gutsy reports that as correct as well. These lines are not something really really bad that I couldn't live with them, I was wondering if there was a way I could get the picture sharper in full screen. I have a 22" LG Flatron Wide screen monitor.

How do you install the Ubuntu restricted extras?

What video card do you have?

---

### Post by taurus on 2007-12-27
Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by bgast1 on 2007-12-27
I have an ATI Radeon X1950 Pro. PCIe. I have everything working with it so far, including the cube. I have not tried any windows games yet. That is one reason why I dual boot, but I do want to give it a go in the future or buy or build a new computer just for gaming.

---

### Post by blueridgedog on 2007-12-27
Remember the core philosophy behind Ubuntu:

[http://www.ubuntu.com/community/ubuntustory/philosophy](http://www.ubuntu.com/community/ubuntustory/philosophy)

Certain multimedia features that users take for granted are not included in the base distribution and must specifically be sought out by the user.  If you install Ubuntu expecting to have a multimedia workstation, you have a few extra steps (albeit well defined) to go through in configuring your system.

---

