---
title: "Screeen resolution"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by jim h on 2007-02-17
This is not really an Ubunto quibble, but maybe.
 Basically my problem is that ctrl+alt+keypad + or - does nothing.  Searching  posts it seems that everyone else thinks it works, but I had jumped the gun and assumed that gnome-display-properties or someone had snuck in there and defeated it.  Apparently I was dead wrong.  (Surprisingly, this is not the first time.)  
  My xorg.conf certainly looks right, and I even tried several variants of Option "DontZoom" "off" in case the default was changed, to no avail.  It worked with this hardware and RH7.2, so I assume it's software somewhere.
  The fancier tools including xrandr rebuild the desktop, which is not what I want.  I just need to zoom and scroll.
   Any ideas about where I can hunt to solve this would be very much appreciated - some 10 hours of searching haven't turned up any clue that I could find.  Thanks.
   Jim

---

### Post by nereid on 2007-02-17
This is normally only a Xserver option. Sorry but I don't remember the exact name but you are talking about the virtual resolution. Maybe you changed the resolution in Gnome and this overwrites the settings from X.

---

### Post by Georges on 2007-04-09
it's a bug

[http://ubuntuforums.org/showthread.php?p=2427387](http://ubuntuforums.org/showthread.php?p=2427387)

---

