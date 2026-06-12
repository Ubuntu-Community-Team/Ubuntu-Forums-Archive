---
title: "Video signal is out of range, can't see login (or anything else)"
date: 2007-12-22
forum: Apple PPC Users
---

### Post by AmishMack on 2007-12-22
Ok, I was trying to set a new resolution and refresh, which seemed to be fine at the time, but now when I startup, I get through the splash screen and just before the login screen it goes out of range.  I think the problem is I need to use the ATI drivers with my 9600, which I read AFTER the change.  My question is: How to I get to a command line BEFORE the login screen?  My only options in yaboot are linux and old, neither which works.  I've read that I need to use sudo dpkg-reconfigure xserver-xorg, but when?  Is there a safe or recovery I don't know about?  I'm using a CRT Viewsonic A90f+ PPC MDD G4 Ubuntu 7.10.  Please help, I'm very new to this and things were going well until I hosed the video.  Thanks!  Please note, on a PPC mac, so I don't have a grub menu (I don't think).

---

### Post by Whiffle on 2007-12-22
Try hitting ctrl+alt+F1   (or f2, f3 etc).  when you're supposed to be at the login screen, it should take you to a terminal where you can login.

---

### Post by AmishMack on 2007-12-22
Ok, tried that, and it seemed to do something, because my monitor would turn back on but would still not be able to get a signal.  The refresh rate on the original install would not go above 60, I set it at 75 which my monitor can handle in OS X and I see an orange screen with cursor for about 2 seconds before it goes blank and plays the login sound effect.  Resolution was also limited to 800 x 600, so I changed that to 1024 x 768, which is also within the limits for my monitor.  Thanks for your suggestion!

---

### Post by AmishMack on 2007-12-28
I ended up doing a fresh install using a alternate cd.  This took care of a few other problems I had as well.  Thanks!

---

