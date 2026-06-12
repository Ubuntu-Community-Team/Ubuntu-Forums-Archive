---
title: "Modifying USB installer stick to overcome fan/overheat during macbook installation."
date: 2022-11-11
forum: Apple Hardware Users
---

### Post by proctorius on 2022-11-11
Hello all,

I have had great success on installing UBUNTU on old macbooks over the last few months.  The only issue I have had is an issue with heat during the installation process as there is nothing controlling the fans in the laptop during the install process, so there is no cooling.  If the install works out, have been letting the macbook cool completely and then quickly booting up and installing 'mbpfan' which I have preconfigured on a usb thumbstick and ready to go.  However, sometimes the install does not go well as the macbook overheats.  I can mitigate this by removing the bottom cover on some, and the battery cover and battery on others, and having a fan blowing on the macbook, and doing the setup in a cool/colder environment, and have even set up icepacks under one stubborn macbook that overheated and failed a couple of times.

However, that's all a pain.

What I would like to do is set up the installer usb stick with mbpfan already up and running when the UBUNTU 'TRY ME / INSTALL' session runs.  How would I go about setting up an installer stick to include mbpfan?  I would plan on setting the fans to full speed on the installation session and then after the install, set up mbpfan via the standard process as below at the 'ineedcoffee' beginners guide.

Anyone willing to offer some guidance?  I'm still pretty n00bish, but I catch on quickly.  I have set up about 20 oor so macbooks so far.  My experience with trying to convert Mac users is that often ppl have tried it but run into issues during the setup or use due to overheating issues, which are largely easy to fix with mbpfan.  Given that Apple 'stale-dates' thier machines, and they are often still pretty great all round when they hit the no-updates line, it seems to me that there is a really untapped user pool of people, and machines, that could be served by something like this.

I am currently using an aluminum Macbook (late 2008, 5,1: 8gb ram, 500gb ssd, Ubuntu 22.10) as my daily driver and it doesn't miss a beat.  It's a little slower booting up, and I try to keep track of how hard I am working it, but I have yet to have any issue.  On the buy and seel websites in my area there are so many macbooks at decent prices because they are no longer updateable/upgradable.  

INFO:
[https://github.com/linux-on-mac/mbpfan](https://github.com/linux-on-mac/mbpfan)
[https://ineed.coffee/post/a-beginners-tutorial-for-mbpfan-under-ubuntu](https://ineed.coffee/post/a-beginners-tutorial-for-mbpfan-under-ubuntu)

---

### Post by QIII on 2022-11-11
Moved to Apple Hardware users.

---

### Post by proctorius on 2022-11-11
Hey, thanks for the help... but my post is about modifying the installer, not about apple hardware.  Wouldn't I be more likely to get a useful reply where I posted it?

---

### Post by tea for one on 2022-11-12
> **proctorius said:**
> What I would like to do is set up the installer usb stick with mbpfan already up and running when the UBUNTU 'TRY ME / INSTALL' session runs.  How would I go about setting up an installer stick to include mbpfan? 
You can remaster an Ubuntu iso by using Cubic
[https://launchpad.net/cubic](https://launchpad.net/cubic)
[https://github.com/PJ-Singh-001/Cubic](https://github.com/PJ-Singh-001/Cubic)

---

