---
title: "External hard disk no longer mounts"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by RogerD on 2006-10-18
Hi

I've got a Western Digital My Book external hard drive. Up to now, it automatically appears on the desktop whenever I switch on. Suddenly it's stopped doing this.

When I click on Places>computer, I see the My Book icon complete with the Gnome footprint icon (not sure if there's any significance in the icon). When I right click on 'open', I get the message: 'Uanble to mount the selected volume'. 'Show more details' gets me:

error: directory/medi/mybook not empty
error: could not execute pmount.

All advice on what to do, would be much appreciated.

Roger D

---

### Post by dbd on 2006-10-19
No real idea, but you could try navigating to /media/mybook and seeing if there is anything in the directory. If it is complaining that it is not empty, then might be worth checking if it is empty, and moving anything from there to somewhere else. (make sure you look for hidden files too, use the command ls -a when in that directory).

---

