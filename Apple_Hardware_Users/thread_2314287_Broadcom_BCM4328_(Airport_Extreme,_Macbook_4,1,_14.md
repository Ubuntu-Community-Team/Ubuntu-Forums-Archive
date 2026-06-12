---
title: "Broadcom BCM4328 (Airport Extreme, Macbook 4,1, 14e4:4328) issues"
date: 2016-02-19
forum: Apple Hardware Users
---

### Post by Jaswinder_Singh on 2016-02-19
Hi,

I'm very new to Linux with barely any experience in handling scripts and command line installations, in spite having worked on a Macbook for the past 8 years. I recently installed Ubuntu 15.10 on my early 2008 Macbook 4,1 (white). I'm facing a lot of trouble with my Broadcom BCM 4328 wi-fi card. 

Here's a detailed description of what the trouble is - 

1. I installed the STA drivers that come with the Ubuntu package. The wi-fi card was visible in the network connections, but when I tried to connect it to my home wi-fi network, it would not. However, it would connect to my office network, and to my android phone's 3g wi-fi hotspot (Moto G-2). I figured there must be something wrong with my home router (D-link 2730U). So to try a workaround, I bought a Tenda USB wi-fi card, and it worked flawlessly with all networks (home, office, phone). But keeping it plugged in is taking its toll on the battery life. The battery is already performing at half capacity in terms of up-time compared to Mac OS X (5+hrs on OS X vs. 2 hrs on Ubuntu) and barely charging to 92-93%. So I looked up an alternative to the external wi-fi card and found this link on the forum - [http://ubuntuforums.org/showthread.php?t=2165178](http://ubuntuforums.org/showthread.php?t=2165178)

2. I followed the instructions and installed the "linux-firmware-nonfree_1.14ubuntu1_all" package, deactivated the STA drivers and rebooted. The internal wi-fi worked absolutely fine. I finished my work and switched off for the night. Next morning, there was no sign of Broadcom in the wi-fi networks list to let me connect to my home or phone hotspot network. I'm back to using the external wi-fi card as of now. 

Any suggestions on where I might have gone wrong?

EDIT: This solution seems to be working for now - [http://ubuntuforums.org/showthread.php?t=2230194&p=13052784#post13052784](http://ubuntuforums.org/showthread.php?t=2230194&p=13052784#post13052784)

---

