---
title: "screen fonts"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by frenchsquared on 2007-12-30
the text is driving me crazy it is making my eyes water

The fonts on ubuntu are all slightly blurred like if you turn off font smoothing in windows. There has to be a way to fix this

moniture is a 28" HD plasma
brand new

---

### Post by Perpetual on 2007-12-30
Did you try System > Preferences > Appearance > Fonts and making adjustments?  I find my fonts are clearer with Subpixel.

---

### Post by frenchsquared on 2007-12-30
that helped aliitle
but I think it is something with the display drivers

---

### Post by nick_h on 2007-12-30
You have already posted this question today - [link](http://ubuntuforums.org/showthread.php?t=653294).

---

### Post by frenchsquared on 2007-12-30
actually last night and no one seemed to answere, I still have the problem and was hoping someone else was on today

---

### Post by frenchsquared on 2007-12-30
gordon@Asus:~$ sudo apt-get install msttcorefonts
Reading package lists... Done
Building dependency tree... Done
Package msttcorefonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package msttcorefonts has no installation candidate
gordon@Asus:~$

---

### Post by nick_h on 2007-12-30
Go to System->Administration->Software Sources and make sure that the multiverse repository is enabled.  You may also want to enable universe at the same time.

---

### Post by lleonard on 2007-12-30
28" plasma monitor?  What type of connector is on the cable between the display and the video card?

---

### Post by lleonard on 2007-12-30
Also what is the native resolution of the display and what resolution is your graphics card running at?

---

### Post by frenchsquared on 2007-12-30
multiverse rep is enabled

have both HD and Normal but the normal blue is connected

native 1920x1200 
running 1920x1200

---

