---
title: "Mesa/ATI Graphics"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by Tumpster on 2007-08-12
Hey there, so i'm a guy who likes to keep everything updated and going strong. Ive downloaded the newest ATI drivers packaged as my comp screws up when I used the opensource ones so I've stuck with the ati released ones until I buy my nvidia card. But, my problems is that when I install these through depackaging and installation opengl reverts back to Mesa. So i get the typical mesa problems that my games won't run at all. Right now as it stands when I punch in fglrxinfo I get this: 
craig@craig-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X700 PRO Generic
OpenGL version string: 2.0.5814 (8.25.18)

craig@craig-desktop:~$

But I want to install the newest package as I know .25 is not the newest but I don't want to revert back to Mesa. ANy ideas how I can update AND keep ati as my opengl? THank you in advance!

---

### Post by Tumpster on 2007-08-13
I would appreciate any help....

---

### Post by r4ik on 2007-08-13
Try,

[http://www.stchman.com/video_drivers.html](http://www.stchman.com/video_drivers.html)

Good luck !

---

### Post by Tumpster on 2007-08-14
No such luck, any other ideas? :)

---

### Post by tadada on 2007-08-14
did you try the restricted driver?

I run Ati Raedon x1300 PRO with the FGLRX restricted driver and it works perfectly (even with my 3-D games at one time I even ran Compiz-Fusion very nicley I will add)

if not go to System>administration>Restricted Drivers Manager
and then enable the Ati accelerated graphics driver (also known as FGLRX) (I might be wrong on the FGLRX name thing but I know that drive works for me...)

---

### Post by Tumpster on 2007-08-15
i am running fglrx,  but when i do an install via the packages from ati it goes back to mesa but when I run it through terminal it does everything just fine but it's an older version. Any ideas?

---

