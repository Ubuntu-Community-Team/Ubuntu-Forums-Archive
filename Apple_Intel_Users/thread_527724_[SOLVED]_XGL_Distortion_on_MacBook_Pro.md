---
title: "[SOLVED] XGL Distortion on MacBook Pro"
date: 2007-08-16
forum: Apple Intel Users
---

### Post by xIke on 2007-08-16
I've been struggling to get XGL to work on my MacBook Pro.  My end goal is to get compiz up and running.  When I login with XGL, my screen is distorted [[picture]("http://tinyurl.com/2vp38y")].  Has anyone had any luck getting XGL to work?  If so, could you please point me to a working tutorial for feisty, or better yet, tell me what might be causing the artifacting?

Thanks a lot,
-xike

---

### Post by cyberdork33 on 2007-08-17
I was getting that when my ATI graphics were not setup correctly. What graphics do you have?

If it is an ATI card, login without XGL and give the output of 'fglrxinfo'

---

### Post by macaholic on 2007-08-17
> **xIke said:**
> I've been struggling to get XGL to work on my MacBook Pro.  My end goal is to get compiz up and running.  When I login with XGL, my screen is distorted [[picture]("http://tinyurl.com/2vp38y")].  Has anyone had any luck getting XGL to work?  If so, could you please point me to a working tutorial for feisty, or better yet, tell me what might be causing the artifacting?

Thanks a lot,
-xike
I had the same problem, what worked for me is to do a Ctrl + Alt + Backspace (restart xserver) and do that and you *might* fix the problem. Mine still does that every once in a while when I change something major in compiz, like updating it. Overall it seems the only workaround I could get to work after a few hours of digging through forums and modifying my xorg file. 
Hope this helps!

---

### Post by xIke on 2007-08-17
macaholic: same here, control-alt-delete always fixed the problem.

I somehow fixed it for good though.  I figured out that when it wasn't working, it was using the mesa drivers.  When I reset the xserver, for some reason it used the ati drivers then.   I had used Envy to install the drivers, so I just uninstalled that and reinstalled fglrx and it works now.  Lesson learned. :D

Thanks all.

---

### Post by cyberdork33 on 2007-08-17
> **xIke said:**
> macaholic: same here, control-alt-delete always fixed the problem.

I somehow fixed it for good though.  I figured out that when it wasn't working, it was using the mesa drivers.  When I reset the xserver, for some reason it used the ati drivers then.   I had used Envy to install the drivers, so I just uninstalled that and reinstalled fglrx and it works now.  Lesson learned. :D

Thanks all.

Yep, this all falls into the same experience I have had. In fact, I don't have to do anymore I like used to, it just stopped being a problem somehow.

---

### Post by ronocdh on 2007-08-17
> **cyberdork33 said:**
> Yep, this all falls into the same experience I have had. In fact, I don't have to do anymore I like used to, it just stopped being a problem somehow.
I can't recall a time when alt+ctrl+delete broke XGL for me, but I guess I'm lucky! I've certainly accidentally reverting to mesa drivers by messing around with dpkg-reconfigure xserver-xorg, though.

Xlke, I'm very glad your situation worked out so well, but remember to post the generation of your MBP! (Very important now that there are Nvidia cards in the newest ones.)

---

