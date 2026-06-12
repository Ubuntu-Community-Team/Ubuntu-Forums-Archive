---
title: "SOLVED - XFCE tiny login fonts"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by 01000111 on 2008-01-31
I'm running Xubuntu on my 61" HDTV at 1920 x 1080 and have been suffering with tiny (nearly single dot) fonts on my login screen.  After quite a bit of poking around, I finally found the right place to fix this...

sudo mousepad /usr/share/gdm/themes/xubuntu/Xubuntu.xml

Replace the part after /themes/ with whichever theme you're using.

Look for "user-pw-entry" and in that <item> block, add:

                <normal font="Bitstream Vera Sans Bold 12" color="#000000"/>

Adjust the font name, size and color as you see fit.  Save the file and CRTL-ALT-BACKSPACE.

That's it.


Binary-G

---

### Post by chewearn on 2008-02-01
You can also add to /etc/X11/xorg.conf, under Section "Monitor":

   DisplaySize <x> <y>

where
<x> is the horizontal size of your display, in millimeter
<y> is the vertical size of your display, in millimeter

This will fix all unusually tiny fonts problem in Xubuntu.

---

