---
title: "how do i add windows after i have installed linux"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by chester on 2006-08-21
I finally bit the bullet, after having trouble installing with every other option given me on the live cd, and reformatted the whole drive and installed ubuntu. What are my dual boot options now?

---

### Post by yaddoshi on 2006-08-21
> after having trouble installing with every other option given me on the live cd, and reformatted the whole drive and installed ubuntu

It is much easier to install Windows first, and Ubuntu second - the reason is that Windows installations will over-write the master boot record of your hard-drive and you will boot straight into Windows without getting the option to boot into Ubuntu.  You will need to resize your ext partition (which you can do with gparted - look for it in Synaptic Package Manager or sudo apt-get gparted from the terminal).  After you install Windows you can recover Ubuntu's grub loader by following the steps [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28add%29%7C%28windows%29").

If you just installed Ubuntu, however, it would be much easier and less time consuming for you to format and install Windows XP, specify the size of the partition you want to use for Windows during the installation (ie: if you have a 40GB drive and you want to dedicate 20GB to Windows and 20GB to Ubuntu, you can have the Windows installer destroy your current partitions, add a new 20GB NTFS partition and install Windows to it, leaving the remaining 20GB of the hard drive unused).  

After you have reinstalled Windows, reinstall Ubuntu, selecting the Use Unused Space option during the install, and everything should be happy.

Good luck!

---

