---
title: "Need help installing UBuntu/Xubuntu"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by theemrsweets on 2007-05-11
I've installed Ubuntu on a few different computers already and haven't had any problems at all.  However for one computer I just can't get it done.  This computer is a dell p4 2.2ghz with 512kb ram with standard on board video card.  When I try to install either Ubuntu or Xubuntu in graphics safe mode, I get an error (something about "X", I didn't write it down but I will try again later.  I then try it with the normal install mode and for Ubuntu I can't get past the map where you select your city for the time to set.  It just freezes and thats it.  I've let it sit for hours and nothing.

For Xubuntu, I get through all 7 steps for installing and it actually starts to install.  It gets up to 15% and it says  "detecting file systems" and either freezes or the screen goes black for a second and then the background screen comes on (blue) without any icons on the screen.

---

### Post by phidia on 2007-05-11
If you are using the desktop/livecd version try the alternate cd it sometimes works when the desktop doesn't.
Also with onboard video you may need to drop to a shell and run dpkg-reconfigure xorg-xserver and choose the driver for that onboard gpu.

---

### Post by theemrsweets on 2007-05-12
Thanks.  I tried that and it worked.

---

