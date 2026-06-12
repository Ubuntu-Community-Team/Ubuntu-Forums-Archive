---
title: "&quot;Could not write intrinsic&quot; when trying to launch ATITD"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by virgilnilson on 2007-06-30
I just finished installing A Tale in the Desert, and after running elaunch, it seems to update fine, I get to the server/connection select, click play and then immediately get an error message saying "could not write intrinsic", and the game does not start.

Googling for this error message turns up zero results, anyone have any ideas?

---

### Post by Pluribus on 2007-07-09
The user running the game MUST have write permissions to the top level game directory and all sub-directories.  The most frequent cause of this issue is downloading and installing the game as root then attempting to run it as another user.  NOTE: ATITD will REFUSE to run as root to avoid any security issues.

---

### Post by HellRat on 2007-10-26
I installed atitd as user with permissions but when I try running the game with './elaunch' nothing happens. any ideas?

---

### Post by Cernunnos on 2008-01-18
I've hit the same wall. Though the frustrating thing with me is that about 7 hours ago I was playing the game fine, having obviously managed to install it a few days ago. The only thing I've changed that I can think of is a recent xorg core update through synaptic, which forced me to also reinstall my nvidia drivers. I've tried everything I can think of, setting all the permissions, re-running eClient-linux-i686.run, etc. But no joy.

I'd really appreciate any help.

---

