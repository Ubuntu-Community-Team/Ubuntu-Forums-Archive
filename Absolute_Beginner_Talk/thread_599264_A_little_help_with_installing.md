---
title: "A little help with installing?"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by Prothoss on 2007-11-01
Hey,

I was wondering if I need to do anything special to install on the following system:

AMD AM2 Athlon 64 X2 5200+ CPU
ATI Radeon X550 XTX PCI-E 16X
Gigabyte GA-M61PM-S2 AM2 MB
2048Mb 2Gb DDR2 667 Kingston

I already have Ubuntu running on my laptop and am really happy with it, however I don't consider myself very knowledgeable at all. In addition, what would be a handy disk partitioning software to use?

---

### Post by ofb on 2007-11-01
Well, the release notes mention a problem with some ATI hardware. You might have a look at that.
[http://www.ubuntu.com/getubuntu/releasenotes/710](http://www.ubuntu.com/getubuntu/releasenotes/710)

Definitely take the LiveCD on a test run before installing. That's not a guarantee of no troubles after install, but if trouble shows up on the test run then you do at least know there /will/ be trouble.

As for partitioning, the LiveCD comes with its own partitioner. It shows up during install, and you can also operate it while running the LiveCD session. It's called GParted. If it's not listed in the menus, then just open a prompt with Alt-F2, and type in: gksudo gparted

Do a little reading about partitioning if this is the first time. You really don't want to mess up with partitioning.

---

### Post by JBAlaska on 2007-11-01
Gutsy should fairly scream on that system.

Use the LiveCD to partition your drive, and if you feel slightly adventurous, choose manual partition as follows (assuming your going to use 100% of your drive for Ubuntu);
/ (root) 10GB+
/home all the rest of your drive space  - 1GB
/swap (that 1GB)

This way if you need or want to reinstall, all your home data will stay intact.

If you want to use desktop effects (compiz fusion), you will have to either use XGL or the new open source ATI driver. I'm using the OS driver and on my system XGL was faster, that may differ on your video card. Hopefully the next release of the OS driver (8.43) will fix that.

Have fun!

---

### Post by Prothoss on 2008-02-14
Well, I *finally* got around to attempting to install today but to no avail. I am trying to install Kubuntu 7.10, I boot from the CD however whenever I try to "Start or install Kubuntu" or "Start Kubuntu in safe graphics mode" my screen goes blank and nothing seems to happen. I have tried leaving it for an extended period of time. If anyone has any idea on the right direction to head with this it would be much appreciated.

---

### Post by emarkd on 2008-02-14
Could be that ATI card.  You could try installing from the [alternate CD]("http://releases.ubuntu.com/7.10/").  It's text-based, so it won't need any fancy drivers for that card.  Then after the install, you'd have to enable the restricted drivers for your video using the restricted driver manager.

---

