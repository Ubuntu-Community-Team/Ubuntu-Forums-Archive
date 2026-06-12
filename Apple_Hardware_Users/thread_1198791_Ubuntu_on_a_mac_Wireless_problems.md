---
title: "Ubuntu on a mac Wireless problems"
date: 2009-06-27
forum: Apple Hardware Users
---

### Post by kcaz on 2009-06-27
OK so I'm running Ubuntu on a mac, I have 2 partitions, the mac and ubuntu. The ubuntu is actually just windows from boot camp, and then I installed Ubuntu over Windows.

Anyways the wireless internet isen't working. I think I've heard of some of these problems before, but I was just wondering what the general consenses is.

I have a modem, and on other computers and the mac partition of my computer the internet works fine, but ubuntu wont reconize it. When I stick an eithernet cable from the modem to the computer however the internet works fine.

Any suggestions?
~Kcaz

---

### Post by philcamlin on 2009-06-27
what mac ? and what wireless card ?

---

### Post by kcaz on 2009-06-27
It is an new Intel based MacBook with a Broadcom bcm4328 wireless card. It says "This networking card is activated but not in use" I can't get any internet.

Thanks
~kcaz

---

### Post by tlois on 2009-06-28
I hope you read this thread:

[http://ubuntuforums.org/showthread.php?t=1198702](http://ubuntuforums.org/showthread.php?t=1198702)

---

### Post by gregorthebigmac on 2010-02-26
> **kcaz said:**
> OK so I'm running Ubuntu on a mac, I have 2 partitions, the mac and ubuntu. The ubuntu is actually just windows from boot camp, and then I installed Ubuntu over Windows.

Anyways the wireless internet isen't working. I think I've heard of some of these problems before, but I was just wondering what the general consenses is.

I have a modem, and on other computers and the mac partition of my computer the internet works fine, but ubuntu wont reconize it. When I stick an eithernet cable from the modem to the computer however the internet works fine.

Any suggestions?
~Kcaz

I'm having the exact same problem, running the same setup. Dual-booted mac OS and Karmic Koala. Got the Broadcom 4328 card. Under 

System>Admin>Hardware Drivers

it says "Activated, but not in use." Looked at over a dozen threads, mostly saying to deactivate driver, reboot, activate driver, reboot, works. Saw a couple other methods to try, so far, all has failed.

I'm out of ideas.

---

### Post by linuxopjemac on 2010-02-27
Uninstall your broadcom driver and follow this post:

[http://mac.linux.be/phpBB3/viewtopic.php?f=3&t=30&p=42&hilit=broadcom#p42](http://mac.linux.be/phpBB3/viewtopic.php?f=3&t=30&p=42&hilit=broadcom#p42)

---

### Post by gregorthebigmac on 2010-02-27
Yes. Tried that, as well. Had trouble getting it to compile. Finally gave up, and wiped the OS, put a fresh install on, used the cd to activate the drivers, rebooted, works fine now. I'm actually posting this from that very laptop, via wifi card :)

---

