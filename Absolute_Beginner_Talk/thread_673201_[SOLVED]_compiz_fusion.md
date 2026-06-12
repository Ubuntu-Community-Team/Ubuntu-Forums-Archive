---
title: "[SOLVED] compiz fusion?"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by kamitsukai on 2008-01-20
how do i setup compiz fusion on ubuntu gutsy? i know its pre-installed but how do i get it working?

thanks

---

### Post by mgmiller on 2008-01-20
System > Preferences > Appearance and select The Visual Effects tab and try clicking on one of the choices like, normal or extra.

An Nvidia video card will need to have the restricted drivers installed for this to work.  With an ATI card it will work out of the box with the regular ati driver, but not with the restricted driver without a bit more work.

Since you have an ati video card, as long as your didn't use the restricted drivers manager to install the accelerated driver, it should just work by clicking one of the other choices.

---

### Post by Seisen on 2008-01-20
Go to System>Preferences>Appearance click on the visual Effects tab and select Extra which will give you the default plugins. To have access to more to more plugins install ccsm

```
sudo apt-get install compizconfig-settings-manager
``` once you install that you can access it by going to System>Preferences>Advanced Desktop Effects Settings.

---

### Post by kamitsukai on 2008-01-20
thanks! works great :)

---

### Post by Motorhead Kaze on 2008-01-20
Seisen!  Thanks.  That is the first time getting Compiz to work was easy.  

Interesting... this time I didn't need to do A THING with my xorg conf and it works anyway.  Someone must've finally realized that a lot of us use Nvidia, and fixed the problem.  I tried Compiz when Gutsy first came out and it slowed my computer way down, so I chucked it.  But just bumped into this thread now, and after my fresh reformatting of the PC, and these instructions everything Compizzy seems to be cool...knock knock.

...but you leave Buddha alone. You roughian.

---

