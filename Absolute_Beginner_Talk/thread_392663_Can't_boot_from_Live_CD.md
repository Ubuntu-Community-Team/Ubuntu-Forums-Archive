---
title: "Can't boot from Live CD"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by BLiveOne on 2007-03-24
I'm trying to check out and possibly install Ubuntu on my home system, but I'm having problems getting the system to complete booting off of the CD. I'm using the 6.10 Live CD and also saw the exact same problems when I tried 6.06. 

The CD boots properly and gets to the boot options screen just fine. It's after that I'm having a problem.  When I try to actually boot Ubuntu I get a mouse cursor, orange/brownish background, and a sound effect. I also see a rectangular window in the middle with what appears to be the Ubuntu logo, but it's hard to tell as the contents of the box are corrupted. I sometimes have mouse control, other times I do not.

This is the point I get stuck at.  It doesn't matter if I try graphics safe mode or not.  From reading other posts here I *think* I should be seeing a window with the options to either run Ubuntu or Install, but I can't say for sure since I've never gotten past this point.


AMD64 3400+
nVidia 7800GT OC (BFG)
nForce4 mobo
1.5GB RAM

---

### Post by zvacet on 2007-03-25
**ctrl+alt+F1** and you will be in terminal
```
sudo dpkg-reconfigure xserver-xorg
```
pick **nv** instead of **nvidia**
You should have graphic now.Install your nvidia drivers with Envy script

---

### Post by BLiveOne on 2007-03-25
Hmmm...

Tried **ctrl+alt+F1** but I didn't get a terminal... in fact nothing happened.  I also tried the 7.04 Beta disc with the same results.

I've attached a quick camera phone pic of what I'm seeing.  :(

---

