---
title: "Hi All! 1st post!"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by uboodumdum on 2007-11-21
Long time Windows user, would feel wonderfull to ditch it!  I think I just learned why Ubuntu is so secure.  The system imported an older Bookmark.html file for FireFox for some reason.  I figured I'd just use my password and delete it and drop in the most current one, Wrong!  I don't own that file, no permissions.  I guess I can just arrange it by hand and of course I can bring up the current file from the floppy or flash, any suggestions for a shortcut, a way to delete the old and replace it with the current?:confused:

:KS:KS
regards all

DumDum

---

### Post by jordanmthomas on 2007-11-21
type this:
```
sudo chown -R $USER ~/.mozilla
```
and then you will own all the files in your firefox folder.  (You SHOULD own this file, not anyone else.)

What this command does is changes the owner of /home/yourname/.mozilla and its subdirectories to be owned by your user ($USER)

---

### Post by uboodumdum on 2007-11-21
[FONT=Arial]I think I'm gonna like this Forum!:KS

Thanks [/FONT]jordanmthomas!

regards all
DumDum
:KS:KS

---

### Post by freesitebuilder on 2007-11-21
Have you already found this page? [https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows) (Switching from Windows) - lots of useful info.

You're right about the forum - it's been wonderfully supportive. :)

---

