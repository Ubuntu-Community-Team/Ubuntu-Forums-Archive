---
title: "[SOLVED] X Server Won't Start"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by Chernevik on 2008-03-10
I have just installed Ubuntu 7.04 on a new computer from a DVD, but X server won't start (I did the installation from text mode).  

The error reported is "Failed to start X server" -- the specific error is "Fatal error -- no screens found".

The video card is NVidia GeForce 8800GT; the detailed error log shows files for GeForce 8800 GTS and GeForce 8800 GTX.

Any suggestions?

---

### Post by Jimmey on 2008-03-10
The typical solution to this problem is to ```
sudo dpkg-reconfigure xserver-xorg
``` in a terminal, and then select the "VESA" Driver, just until you can install the nvidia drivers (assuming they're not installed).

---

### Post by marufaberlin on 2008-03-10
Well,... you might not have your screens set up properly. have a look in /etc/X11/xinit.rc.

---

### Post by marufaberlin on 2008-03-10
Oh, .. I see that Jimmey has just told you to dpkg-reconfigure, that does that for you.

---

### Post by Chernevik on 2008-03-10
That worked.

Friends, for this relief, much thanks.

---

### Post by Jimmey on 2008-03-10
Could you possibly edit the thread and mark it as solved? This might help any others with the same problem as you.Thanks!

---

