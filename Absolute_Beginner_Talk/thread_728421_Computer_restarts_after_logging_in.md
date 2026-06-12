---
title: "Computer restarts after logging in"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by slymi2005 on 2008-03-18
Okay so I was tinkering with the graphics settings, why I do not know, and it said that I had to log out so I did and when I try logging back in everything happens in the background but I can't see anything happen, I just see the splash screen. I know that it logged in because when I hit ctrl+alt+bkspace I see the desktop. For some reason this only affects certain users and not others, also I was able to log into xfce but not gnome or kde4. On kde4 everything logs in and it appears to work fine but then it restarts on its own. In gnome it just goes to the splash screen and everything happens in the background but I cant see it so  I have to restart it myself.This happened to me before and I remember that I had to log into recovery mode and change some setting, I think it had to do with the display, someting about 16 or 24, I don't recall. Anyway if anyone could help that would be fantastic.

---

### Post by dsauxier on 2008-03-18
2 things : 
First, if it's specific to a particular user, then try reverting back to that users default gnome settings.  You can do that by renaming the .gnome2 directory : 
(assuming the username is "user")
```
mv -i /home/user/.gnome2 /home/user/.gnome2_saved
mv -i /home/user/.gnome /home/user/.gnome_saved

```
I don't use KDE, but there's likely a similar configuration area that could be renamed.
If that works, then you can copy certain things back from your .gnome2_saved to restore any settings that you want to retain.

Second, (if the above doesn't work) then you can boot with the liveCD and grab a working copy of /etc/xorg.conf (since you mention that you think it had to do with the display when this happened before)

---

### Post by adi_das on 2008-03-18
Try conducting a memtest.

---

