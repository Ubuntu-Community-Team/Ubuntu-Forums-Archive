---
title: "Netrunner UEFI boot problem"
date: 2014-08-06
forum: Any Other OS
---

### Post by Skyflier on 2014-08-06
Hi, I am trying to install Netrunner 14 x64 on my laptop which boots with UEFI and has Windows 8.1 already installed.

I have installed Netrunner 14 using a USB drive and after installation I get an error. The system does not even boot, instead I get a basic GRUB command line to rescue my system. 

This is not the only Ubuntu base distro where this happens, also Elementary OS happens to have this issue.

---

### Post by oldfred on 2014-08-06
Did you install in BIOS or UEFI boot mode?

May be best to see all the details. Post link from Boot info report. Do not run auto fix until we see what your configuration is.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Skyflier on 2014-08-06
Thanks for the reply

Here is the link to the Boot info report:
[http://paste2.org/BF9I84bU](http://paste2.org/BF9I84bU)

---

### Post by oldfred on 2014-08-06
It looks like a standard UEFI install.
Does netrunner use btrfs by default? I do not know much about it. Some have tried it, others have had issues. Supposedly each version is a bit better.

       Linux 3.13 Kernel HDD File-System Benchmarks
[http://www.phoronix.com/scan.php?page=article&item=linux_313fs_hdd&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_313fs_hdd&num=1)
10-Way Linux File-System Comparison On Linux13.10
[http://www.phoronix.com/scan.php?page=article&item=linux_310_10fs&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_310_10fs&num=1)
BTRFS, not ready for prime time
[http://ubuntuforums.org/showthread.php?t=2111487](http://ubuntuforums.org/showthread.php?t=2111487)
Linux 3.11 File-System Performance: EXT4, Btrfs, XFS, F2FS
[http://www.phoronix.com/scan.php?page=article&item=linux_311_filesystems&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_311_filesystems&num=1)

---

### Post by Skyflier on 2014-08-07
No it does not install BTRFS by default, I did chose it. But that is not the cause of the GRUB problem because I have already tried installing in Ext4 and I get the same error.
I know how to deal with BTRFS, I maka some tweaks to the fstab file and I never had problems with it, only benefits.

The question here is what is causing the problem with GRUB, since Ubuntu and its derivaives do not generate this issue and even Kubuntu, which Netrunner is based on. 
Distros based on Ubuntu such as Netruuner or Elementary have this issue and I can't find the reason for it.

---

### Post by oldfred on 2014-08-07
It did not look like Boot-Repair opened any of your btrfs system. 
So that might indicate the drivers are not load or loaded correctly.
Also grub does have a btrfs.mod which should be loaded by grub with a insmod if it is not in your grub.cfg.

---

### Post by Skyflier on 2014-08-08
Well, I reinstalled Netrunner in Ext4 and the same error happens. As I said before, Ubuntu and Kubuntu install and boot fine, even in Btrfs

Here is the new Boot-info report:
[http://paste2.org/bsUhANas](http://paste2.org/bsUhANas)

---

### Post by oldfred on 2014-08-10
BootInfo report is not really showing anything that I can see as an issue.
But some file or configuration must not be correct.

Can you install in another 10GB partition, Ubuntu and will its grub boot your Netrunner?

---

### Post by Skyflier on 2014-08-10
Well it seems like after some investigations and testing I found the possible cause. 
I believe Netrunner 14 is not actually working well with UEFI boot and it is not meant to boot with it. The way it boots using Pendrive USB is an amendment and after installing GRUB is not ready to boot Netrunner. So I'll stick with Kubuntu for now until Netrunner's next version hoping the issue gets fixed or I find the fix for it.

---

