---
title: "1680x1050 Video Resolution"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by w8diz on 2007-03-18
In the file /etc/X11/xorg.conf, I notice in the "Screen" section that I should have 1680x1050 pixel resolution available as a selection, but it does not show up as an option in my Screen Resolution Preferences.
My PC video hardware is a VT8378 S3 Unichrome from VIA

Any ideas why the data in the xorg.conf file does not correlate with the selection options?

TIA, -Diz

---

### Post by w8diz on 2007-03-18
Doing a search on the forum got me some things to try like...
sudo gedit /etc/X11/xorg.conf
sudo dpkg-reconfigure xserver-xorg
Everything I try works - EXCEPT I still do not see an option in the screen resolution option for 1680x1050. Will check the VIA web-site again.
I assume it's a video driver issue. Anybody have a clue where else I might find help?

---

