---
title: "cloning a user cp -rx doesn't include gnome settings"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by SunKing2 on 2008-02-07
Using gutsy/gnome
I set up an old computer for a person named pam, but it turns out a person named lorraine is getting it.  I was planning on creating a lorraine account and recursively copying all the /home/pam stuff to it.

But first I created a john account to try it.  I signed into gnome with john, then using Ctl-Alt-F1, I entered
```
cp --force -rx /home/lorraine/* .
```

So I signed out, signed back into john and the resolution is wrong, the icons on the top panel are wrong, and it has the original wallpaper, whereas lorraine has no wallpaper.

Any advice of how to create a lorraine account (I didn't do it yet), and use the settings and gnome settings from the pam account?

---

### Post by bilge.tutak on 2008-02-07
If you did not edit some of the files specifically, I think the behaviour is normal. Since some of the files are user name dependent, if you do not edit them correctly from lorraine to john, it will have some problems. Maybe it will try to reach a path with lorraines files and will not have enough permission. Just make sure none of the files have lorraine in it. 
And also * might exclude the dot (.*, hidden) files which basically has most of the user specific settings. So probably they are regenerated for the new user by the system (like .gnome2, .profile, etc.)
Instead of copying files do a folder copy with
```
cp -rfx /home/lorraine /home/john
```
if it is appropriate.

---

