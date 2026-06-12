---
title: "Missing screensavers"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by ColdFusion09 on 2006-08-17
After reading [this topic]("http://www.ubuntuforums.org/showthread.php?t=195557"), I decided to follow the instructions on there because I am more comfortable with xscreensaver's "preview" option and I like its screensavers better. I believe I did everything on there correctly, but now I am missing about half of the normal screensavers included with xscreensaver. 

This is how most of the screensavers are:
[[IMG]http://img291.imageshack.us/img291/368/untitledsn6.th.jpg[/IMG]](http://img291.imageshack.us/my.php?image=untitledsn6.jpg)

Would anybody know how to fix that and install all the missing screensavers? I know it seems like a dumb issue (probably easy to solve, too), but I literally have been using Ubuntu for about a day. 
PS: If it doesn't make sense that I can already have a preference for xscreensaver over gnome-screensaver, I began with installing 5.10 and then upgraded everything.

Thank you.

---

### Post by it.henrik on 2006-08-17
search in synaptics after screensaver :) or the ones that you are missing

---

### Post by bulldog on 2006-08-17
Did you actually installed the extra screensavers?

sudo apt-get install xscreensaver-data-extra xscreensaver-gl-extra

Walk trough the HowTo again and see if you missed a step.

If you haven't done yet,install the drivers for your video-card as well,to be sure the screensavers are working.

---

### Post by ColdFusion09 on 2006-08-17
Great, I feel stupid now. I checked the repositories list and they were somehow all set to be for Ubuntu 5.10. So I set them all for 6.06 and "sudo apt-get install xscreensaver-data-extra xscreensaver-gl-extra" worked now (before, it would say that it wasn't found).

Again, thanks a lot.

---

