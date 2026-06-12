---
title: "resolution locked"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by rmvg on 2006-03-31
I cannot get my  VIA VT8378 video card to work properly when i boot up ubuntu 5.10 the monitor is all giggley and the refresh and resolutions are locked.

I read several posts stating that this could be caused by not having the nessary  horizsync and VertRefresh lines in my /etc/x11/xorg.conf file i check and they are present.

I also ran the xorg redetect command cannot remeber what it is right now and it hurts my eyes to look at that machine.

Please help.

---

### Post by andrewsawyer on 2006-03-31
Try ```
sudo dpkg-reconfigure -phigh xserver-xorg
```.  This may help.

Let me know.

---

### Post by Mustard on 2006-03-31
Try this...

ctrl + alt + f1 to get to a terminal (remember that you can use ctrl + alt + f7 to get back to desktop). Login with username and user password to get a command prompt

```
sudo /etc/init.d/gdm stop
#shutdown gnome desktop manager
```

```
sudo dpkg-reconfigure xserver-xorg
#reconfigure xorg.conf
```

Choose the default answers for whatever things you don't know the answers to.  When you get to the screen resolutions dialog, add the screen resolutions you want.  When you finish answering all the questions it will make a backup of your old xorg.conf and name it according to the date and time it was made.  It will then write a new copy of your xorg.conf according to the choices you made in the configuration dialog.

Then do this..

```
startx
#restart the Xserver
```

if startx doesnt work try this..

```
sudo /etc/init.d/gdm restart
#restarts the gnome-desktop-manager
```

Check to see if your new resolution settings are working.

If you still have issues visit this thread...

[http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)

---

### Post by Mustard on 2006-03-31
[QUOTE=andrewsawyer]Try ```
sudo dpkg-reconfigure -phigh xserver-xorg
```.  This may help.

Let me know.[/QUOTE]

I believe auto detection works best if gdm is shut down, hence the reason I pasted a more elaborate set of instructions.  In this case X is running, so I figure its better to shut down X first.

---

