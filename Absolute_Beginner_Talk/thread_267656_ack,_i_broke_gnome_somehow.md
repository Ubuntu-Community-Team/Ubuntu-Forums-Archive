---
title: "ack, i broke gnome somehow"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by econobeing on 2006-09-28
i'm not sure what i did, i haven't used gnome for a couple days(been using KDE). 

and i installed a few things, code::blocks, amaroK codecs, and NVU(these are the ones that i remember, don't think i put anything else on.)

aside from that i'm not sure what i did that could have screwed gnome up :/

when i start it up all i see is the two bars on the top and the bottom, and they keep appearing and dissapearing, after it does that a few times i see a quick flash of a window that says "error" on it, but it doesn't say anything on it, and goes away really fast.

is there a way i can fix this? i'm assuming i just have to re-install gnome.

i really really don't want to re-install ubuntu itself...

---

### Post by jordanmthomas on 2006-09-28
While using KDE, did you change the GTK appearance so GTK apps would look better?

---

### Post by aysiu on 2006-09-28
Try this in KDE: ```
mv ~/.gnome ~/.gnome.old
mv ~/.gnome2 ~/.gnome2.old
mv ~/.gconf ~/.gconf.old
mv ~/.gconfd ~/.gconfd.old
mv ~/.metacity ~/.metacity.old
mv ~/.nautilus ~/.nautilus.old
``` Then log out of KDE and back into Gnome. Anything different?

---

### Post by econobeing on 2006-09-28
oh yeah, i changed the GTK style to Qt, then changed it back to "use my KDE style in GTK applications"

i tried the moving commands, that kind of worked, it brought it up(with an apparent reset of my themes and preferences, but thats okay, as long as i can use gnome). but then it told me that the clock and the battery monitor have quit unexpectedly. to test it out i logged out, logged into KDE real fast, then logged out and back into gnome, and the blinking bars thing came back. :/

---

### Post by aysiu on 2006-09-28
Hm. That's weird.

Well, we tried resetting the user settings. Have you tried creating a new test user and seeing if that user can log into Gnome?

---

### Post by jordanmthomas on 2006-09-28
```
mv ~/.gnome.old ~/.gnome
mv ~/.gnome2.old ~/.gnome2
mv ~/.gconf.old ~/.gconf
mv ~/.gconfd.old ~/.gconfd
mv ~/.metacity.old ~/.metacity
mv ~/.nautilus.old ~/.nautilus
```
move your stuff back
Go back in KDE and tell it you want to use a specific GTK theme.  At the top of the list is a blank entry.  Use this.  It has always fixed this same error for me.

---

### Post by econobeing on 2006-09-28
the blank GTK theme works :D thanks a bunch!

---

