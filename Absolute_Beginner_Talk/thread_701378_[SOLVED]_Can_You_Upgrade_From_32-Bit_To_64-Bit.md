---
title: "[SOLVED] Can You Upgrade From 32-Bit To 64-Bit?"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by Minker17 on 2008-02-19
I was just wondering if it was possible to upgrade to 64-Bit? I'm sure it's not, but I figured it was worth a shot?

If not, what is the best way to back up stuff so that I can do the upgrade and restore it all? Is there key folders/files I need other than my personal stuff?

---

### Post by Paqman on 2008-02-19
You can't do an in-place upgrade. You'll need to reinstall.

As far as backing stuff up goes, besides your personal data you'll want to copy all your program settings and preferences. These are stored in your /home directory. Gnome keeps them pretty tightly organised in .gconf there (KDE, I believe, has them scattered around /home a bit more) Easiest thign to do would be grab a copy of the whole of /home. Of course, if you mounted /home on a seperate partition when you installed then just leave it as it is (just don't format it when you reinstall)

Whatever you do with /home, make sure you set the users up exactly the same on the new installation. Otherwise you'll get permissions issues. The important bit to get right is the user number. Create them in the same order as you originally did and you should be fine.

You might want to take a copy of /etc/fstab if you've edited it at any point. You can also [automatically generate a list of installed packages](http://ubuntuforums.org/showthread.php?t=261366) that makes the reinstall go a lot quicker.

---

### Post by Minker17 on 2008-02-19
Thank you!

---

