---
title: "Intel C2D gen2 Compiz Definitive Answer"
date: 2007-12-14
forum: Apple Intel Users
---

### Post by tizzod on 2007-12-14
OK, I just dual booted my MBP with Gutsy.  Works great!  One of my main reasons for installing it was to try out Compiz and see some cool effects.  Now, I've done a lot of googling, and have run through a few howto's but I can't seem to get it to work.  this is on a gen2 MPB w/ an ATI X1600, not the nvidia version
This tutorial seemed the best:
[http://www.howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-ati-mobility-radeon-9200](http://www.howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-ati-mobility-radeon-9200)

I installed the restricted driver for the ATI card through the Restricted Drivers Manager, and installed all the necessary compiz packages

However, when I go to choose "custom effect" under System>Preferences>Appearance>Visual Effects, it says "composite extension not available".  So then I read to add this into xorg.conf, so I changed
```
Section "Extensions"
        Option          "Composite"     "0"
EndSection
```
to
```
Section "Extensions"
        Option          "Composite"     "Enable"
EndSection
```
Now when I try to enable custom effects, it thinks, then says "Desktop effects could not be enabled"

then I read somewhere that the X1600 doesn't support Composite, so that's why I can't enable desktop effects.

Is it possible to run Compiz with the X1600?  I just can't find any definitive answer in the forums.

The wiki on installing 7.1 on the mbp doesn't help either, it only talks about compiz fusion icon

Any help is greatly appreciated

---

### Post by cyberdork33 on 2007-12-14
the proprietary ATI driver in the repos does not support composite. The latest drivers from ATI (on their site) does though.
If you don't want to install those manually, then just install XGL and you can then use compiz. (must restart first).

```
sudo aptitude install xserver-xgl
```

---

### Post by tizzod on 2007-12-14
Thanks for the quick reply!  I'll give that a shot.

Can you explain one thing though?  What's the difference between composite and xgl?

---

### Post by cyberdork33 on 2007-12-14
> **tizzod said:**
> Thanks for the quick reply!  I'll give that a shot.

Can you explain one thing though?  What's the difference between composite and xgl?xgl provides the compositing that is lacking in the ATI driver. Other drivers have an implementation of AIGLX which enables compositing without the use of xgl.

---

### Post by tizzod on 2007-12-14
is there an advantage to using a driver with compositing built in?  so, the likewise is there any big disadvantage using xgl?

---

### Post by cyberdork33 on 2007-12-14
> **tizzod said:**
> is there an advantage to using a driver with compositing built in?  so, the likewise is there any big disadvantage using xgl?speed, annoyance.

---

### Post by benanzo on 2007-12-14
XGL and AIGLX have exactly the same purpose.  The difference is that with XGL none of the compositing code is built into the driver or the X server, but rather supplied as 'extensions' to the X server.  With AIGLX the supporting code is in the server itself so the driver can call it directly rather than through the X server as intermediary.  It's just two methods to achieve the same goal: wobbly windows.

It's often stated that AIGLX is the "correct" method.

---

