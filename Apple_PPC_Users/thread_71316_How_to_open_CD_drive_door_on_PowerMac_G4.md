---
title: "How to open CD drive door on PowerMac G4?"
date: 2005-10-03
forum: Apple PPC Users
---

### Post by gurdy on 2005-10-03
I've just installed Hoary PPC, and it looks great. Once I've logged into Ubuntu in Gnome or KDE, how do I get the CD drive door to open on  my PowerMac G4?  I want to insert a CD, but the "open drive" button on my keyboard doesn't do anything. Thanks!

---

### Post by stuporglue on 2005-10-03
Quick fix: In a terminal you can type "eject" and it should pop open. 

Better fix: Run "xev" in a terminal to find out the keycode for whatever key you want to eject the drive. Edit /etc/pbbuttons.conf and use that keycode. You'll need to either restart pbbuttonsd or reboot for the changes to take effect.

---

### Post by gurdy on 2005-10-03
Thank you so much!

---

### Post by gurdy on 2005-10-11
I also see now that in Gnome you can choose Places-->Computer and in the window that appears right-click (or click + Function Key 12) on the CD icon and choose Eject to open the CD drive door or Mount to close it.

---

