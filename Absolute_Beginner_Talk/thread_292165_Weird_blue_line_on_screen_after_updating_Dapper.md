---
title: "Weird blue line on screen after updating Dapper"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by spamzilla on 2006-11-03
I have just finished updating and installing all updates for Dapper, and I now have a weird blue line down the left of the screen. This line is only present on all Ubuntu screen. eg it shows on my desktop, all pages when laptop os loading up, BUT NOT say in firefox. Does anyone know how I can fix this problem?

Here's the blue line:

edit: hang on stupid screenie :/

edit2: the blue line doesn't show up in screenshots!!

---

### Post by spamzilla on 2006-11-03
Anyone?

---

### Post by ciscosurfer on 2006-11-03
How old is your laptop?  Does this happen when you're in Windows as well?  My bet is that your screen has failed.  But, maybe not.

You can try messing with your /etc/X11/xorg.conf file and make sure all the settings are how you want/need them [B]BE VERY CAREFUL HERE.

[/B]You can can also issue the following from a terminal and assign settings through a setup process (you may want to read up on how to use it before you do)```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by spamzilla on 2006-11-03
My laptop isnt *that* old, and lol I dont use windowsm anymore!

I'll read up and try that command, thanks :)

---

### Post by spamzilla on 2006-11-04
ciscosurfer, that didn't fix my problem, as the blue line is still there :(

---

### Post by spamzilla on 2006-11-04
Bumpage for help!

---

### Post by ciscosurfer on 2006-11-05
I would suggest you try running a liveCD of any distro to see if this problem is replicated there as well.  This, of course, is short of installing Windows or something similar to check to see if this can be duplicated there.  The reason for doing this is to isolate the problem.  If you can successfully run another distro without this blue line problem, then it can be isolated to Ubuntu.

---

### Post by spamzilla on 2006-11-18
This blue line is still present in Windows XP :( Does this mean my laptop screen is messed up, and is it possible to fix it? Bear in mind that this blue line does not show up when I have an application open on the screen!

---

### Post by spamzilla on 2006-11-18
Anyone got any ideas?

---

### Post by spamzilla on 2006-11-18
:'(

---

### Post by ciscosurfer on 2006-11-18
spamzilla,
I would have to say that unfortunately you have a bad screen.  On the plus side, we now know that it wasn't isolated to Ubuntu and is replicated in Windows as well -- this of course means that the problem is not OS specific, rather, it's a hardware issue (screen has gone bad).  To be specific, your screen hasn't "gone bad", it's just experiencing pixel loss or something to that effect.  I suppose if you've got the money to get it replaced, if it's still under warranty, then go ahead and do that, but if it doesn't really bother you that much, I wouldn't really worry about it.

---

