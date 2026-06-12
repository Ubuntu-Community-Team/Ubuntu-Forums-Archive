---
title: "Lost X environment"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by fairmeadow on 2007-03-08
I'm hoping that soemone can help me.  I was attempting (unsuccessfully) to install a driver for my NVIDIA GeForce2MX.  The result now is that when I start the system I get a dialogue telling me: the X server is incorrect, then that it is disabled - start GDM when it is correct.  I then just get a black screen.

As someone new to Linux I'm now completely stumped.

Bob

---

### Post by chewearn on 2007-03-08
Press CTRL+ALT+F1 to get to login prompt. login using your user's name and password.  

Then at the terminal, restore your original xorg.conf (you did remember to back-up before you start installing nvidia driver, right? :biggrin: ); e.g.

```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

Else, try this:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by fairmeadow on 2007-03-08
Thanks for the help.  Unfortunately no backup.  I would have had no idea where to look or what to copy in any case.

I've gone through the manual reconfiguration, and no improvement.  I still get the message: "failed to start the X server".  It says that it has created a log file - how do I look at that, and what should I look for?

---

### Post by chewearn on 2007-03-08
I can't remember exactly where to find the log.  But if you could examine the error messages carefully, there might be a clue, where to find it and how to fix the xorg.conf file.

---

### Post by strikeback03 on 2007-03-08
did you make any changes when doing manual reconfiguration with dpkg-reconfigure?  If you had graphics when you first installed, reconfiguring with all the defaults will usually get them back to the original state.

---

### Post by konungursvia on 2007-03-08
sudo nano -Bw /etc/X11/xorg.conf
then change driver back to "nv" from "nvidia", then ctrl-O, then startx

---

### Post by fairmeadow on 2007-03-09
Finally I have the NVidia driver working.  Thanks to all who have given help and advice in this and other threads.  Either directly or indirectly it has all helped.  In the end a combination of editting xorg.cong, installing nvidia-glx and running nvidia-xconfig did the trick.

Again, thanks to all.
Bob
:)

---

