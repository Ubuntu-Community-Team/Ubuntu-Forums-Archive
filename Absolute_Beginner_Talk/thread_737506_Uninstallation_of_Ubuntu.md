---
title: "Uninstallation of Ubuntu"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by sjbyer on 2008-03-27
I installed Ubuntu 7.10 a week ago and it was working fine until I started messing with a few programmes and now it doesn't seem to function right. I want to give Ubuntu another try as I am pretty new to it and like it a lot. 

I am dual booting Ubuntu 7.10 and Vista, and I have a recovery drive with a manufacture re-image. I've used the factory re-install of Vista before and it works great. I was wondering if, with the new installation of Ubuntu, if I could just re-image my laptop's hard drive and i was wondering if that would get rid of Ubuntu. 

I want to get Ubuntu 8.04 when it's out of Beta release, so I want to get rid of Ubuntu 7.10 because it's also messing up. 

I am wondering if doing a manufacture re-installation of Vista will be good or if it will mess up the GRUB bootloader.

---

### Post by (((X))) on 2008-03-27
Download gparted live cd and burn that image.
After rebooting delete all ext3/2, SWAP partitions and expand nfts partition.
Good luck.

---

### Post by jan quark on 2008-03-27
have a look at this thread dealing with reinstall of ubuntu
[http://ubuntuforums.org/showthread.php?t=152300](http://ubuntuforums.org/showthread.php?t=152300)

---

### Post by forrestcupp on 2008-03-27
You could just hang in there for a month and upgrade to 8.04 when it is released.  If you dual boot, you don't need to even boot to Ubuntu until then if you don't want to.  I think that way would save you a lot of headaches and time.

---

### Post by sjbyer on 2008-03-27
Will Ubuntu 8.04 re-write all what I have on my Ubuntu 7.10 partition? I think I made my partition only 3.7 GB, and that was a mistake. Is there a way to expand that?

---

### Post by sjbyer on 2008-03-27
Do you guys think using my recovery partition in Vista to restore to manufacture installation of Vista would work to get rid of Ubuntu? I'll want to create an 8 GB or so partition for 8.04.

---

### Post by forrestcupp on 2008-03-27
Yes, if you restore your computer to the factory settings, it will be bad for Ubuntu.  Since you made a new partition, it may not write over it, but it will overwrite grub.

If all you want to do is resize your Ubuntu partition, use [GParted LiveCD](http://gparted-livecd.tuxfamily.org/) to do that without losing your data.

And yes, when you upgrade, it Hardy will write over your current version, but if you upgrade instead of a clean install, you will keep your current settings.

---

