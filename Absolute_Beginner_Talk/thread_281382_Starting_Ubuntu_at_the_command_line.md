---
title: "Starting Ubuntu at the command line?"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by sp00ki on 2006-10-21
I have a laptop running Ubuntu which i'd like to configure to boot without loading Gnome (i can always launch the desktop environment later).  Can anyone point me in the right direction?
Thanks

---

### Post by ReaderRat on 2006-10-21
When you reach the login screen, there is a Options menu in the bottom left corner of the screen. Click on it, select session, and click on Failsafe Terminal.
Hope this helps...

---

### Post by jordanmthomas on 2006-10-21
The quickest (and probably not the best) way I know is to edit /etc/X11/default-display-manager and change it to something that does not existt.

i.e.
```
sudo nano /etc/X11/default-display-manager
```
change it from ```
/usr/sbin/gdm
```to something like ```
/usr/sbin/gdmPLEASEDONOTSTART
```...just something easy to change back if you wish to do so later.

You'll still be able to start gdm with sudo gdm, but it won't load by default.

Alternatively, you could read up on how init works and remove gdm from init.

---

### Post by nyinge on 2006-10-21
As Jordanmthomas noted at the end of his post, you can remove gdm from all the run levels.  I've found this easiest to start from CLI.  Issue the following command:
```

sudo update-rc.d -f gdm remove

```
That would remove gdm from all run levels.

---

### Post by chuckyp on 2006-10-21
Why not just start in a runlevel that doesn't init gnome or gdm.  That would actually be the correct way to do it.

---

