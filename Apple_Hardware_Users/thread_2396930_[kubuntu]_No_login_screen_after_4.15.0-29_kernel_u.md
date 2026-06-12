---
title: "[kubuntu] No login screen after 4.15.0-29 kernel upgrade"
date: 2018-07-23
forum: Apple Hardware Users
---

### Post by Anquietas on 2018-07-23
Hello all,

Please help me with a problem, which is starting to get on my nervs ...

I have a MacBook Air laptop which is running Linux (Kubuntu 16.04.5 LTS) with NVidia Graphics Card, KDE, Xorg, SDDM, and so on... Clean and natural install, no funky custom kernel or drivers or anything...

Everything worked fine (with the 4.13.* kernel) until I've upgraded all my packages (which included the "wonderful" 4.15.0-29 kernel, which broke my system).

Now, everytime I try to boot normally, it asks me for my disk password (I have an encrypted LVM) and after that, guess what ?: blank screen. The login screen does not appear.
I can switch the Terminals with Ctrl+Alt+Fx, however.

However, the same kernel, if I boot it in recovery mode and then I select "Resume", the login screen appears, but it lags a little bit...

Needless to say, if I boot the older kernel (4.13), everything works perfectly.

I dug up some logs and found something like "sddm-greeter" segmentation fault in nouveau_dri.so or something like this.

So, it looks like the new kernel doesn't quite seem to look eye-to-eye with nouveau drivers...

And no, I don't want the NVidia proprietary drivers because I get along just perfectly with Nouveau on other machines, and I don't want to reinstall nvidia drivers everytime I'm upgrading the kernel.

And yes, I already have "haveged" installed, to provide sufficient entropy (I saw that the possible lack of entropy might be a problem in some cases)...

So, what is going on ?

Any help would be appreciated...

---

### Post by Anquietas on 2018-07-25
Bump

---

### Post by QIII on 2018-07-25
Moved to Apple Hardware Users for a better fit.

---

### Post by Anquietas on 2018-07-27
I'm opening a bug report... It looks like there are no capable people of helping me here...

---

