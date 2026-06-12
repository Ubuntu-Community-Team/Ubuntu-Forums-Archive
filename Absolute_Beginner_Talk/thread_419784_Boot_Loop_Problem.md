---
title: "Boot Loop Problem"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by thefoolisme on 2007-04-23
Hi there, 

I'm running Edgy on a laptop with a dual-boot with XP.  My issues started out yesterday with the Gnome panel hanging.  I would sign in, and then just get the beige screen with the white square in the top left corner.  I perused this forum, and came up with a couple of suggestions, i.e. reinstalling the Ubuntu desktop (which didn't work because it couldn't find the ubuntu package) ,  reconfiguring xorg, which appeared to work somewhat, but it wasn't fixed properly because the screen saver wouldn't work right.  

Later, I restarted the laptop to go into Windows for a minute, came back to Ubuntu, and ended up in this endless boot loop.  The login screen comes up, I log in, then enter my password, then the login screen reappears again.  An endless cycle.  I can get into terminal using crtl+alt+F1, but I wouldn't know what to fix.  Apparently I just keep breaking everything.  :-)   It's not a space problem, as mentioned in one post, there is plenty of room left on the drive.  It's a relatively new install and has 15GB each for the root and home partitions. 

At any rate,  I could probably just reinstall it and be done with it, but I want to figure out how to fix it instead.  I'll call it one of those linux lessons.  Can anyone advise?  Please keep in mind that this is the beginner's forum and I am a beginner, and if you don't type slowly and succinctly, I probably won't understand  :)  Thanks in advance.

---

### Post by leibowitz on 2007-04-23
You seems to explain that everything is fine, until you boot into Windows and then Ubuntu won't work again. That's unbelievable, at least for me.

Anyway, you can try to start this. Go to the console (CTRL+ALT+F1), and stop the session manager.
```
sudo /etc/init.d/gdm stop
```

Then try to start Xorg without session manager.

```
startx
```

And paste any output you get from this command.

---

### Post by Cypher on 2007-04-23
Were you doing anything in particular while your issues started, or did it just appear all by itself? 

As, **leibowitz**, suggested, start up X without anything and see what happens. If X is OK, then it might be some application that gets started by during GNOME starting that is crashing itself and perhaps X with it and causing the respawn.

Regards

---

