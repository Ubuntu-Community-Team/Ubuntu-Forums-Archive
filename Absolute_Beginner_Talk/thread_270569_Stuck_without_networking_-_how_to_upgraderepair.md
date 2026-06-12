---
title: "Stuck without networking - how to upgrade/repair?"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by bobmct on 2006-10-03
Gentlemen;
I've been using Kubuntu on my desktops since 6.06 was released.  Its working quite well.  However, I needed a new notebook to cart my work around with and I purchased a compaq p3015nr model.  I installed Kubuntu 6.06 on it and the LAN adapter was not recognized so I tried Edgy 6.10 and it did so I installed it.  While the install went as expected I have NO NETWORKING ability at all.  The OS sees my nvidia LAN device but it will not start and forget about the broadcom 43xx wireless.

As a result of all my research on the wifi issue (using other desktops) I printed much of the help and instructions.   Now I would like to apply some of this wisdom to my new laptop but without a network I have a dilemma:  Virtually all of the fixes and upgrades require use of apt or adept or at least some downloads of things like drivers, etc.

I am at a loss!  If I could at least get the LAN working then I should be able to access the necessary sites and download the required software.

So, can someone PLEASE detail how one could perhaps get the LAN functional so this can be accomplished?   It SURE would help!

Thank you.

---

### Post by ciscosurfer on 2006-10-04
On your top panel, click System > System Adminisration > Networking.  Enter your password.  Make sure all of your settings are correct.  When you've done this, go to a terminal and stop/restart your connection to bring up the interface```
sudo ifdown eth0
sudo ifup eth0
OR IF YOU'RE USING eth1, swich it up:
sudo ifdown eth1
sudo ifup eth1
```See if this helps...

---

