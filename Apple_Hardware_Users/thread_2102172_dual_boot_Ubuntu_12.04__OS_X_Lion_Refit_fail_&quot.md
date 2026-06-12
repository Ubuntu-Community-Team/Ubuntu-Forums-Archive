---
title: "dual boot Ubuntu 12.04 / OS X Lion /Refit fail &quot;missing operating system&quot;"
date: 2013-01-06
forum: Apple Hardware Users
---

### Post by boingo-bo on 2013-01-06
Hi-
I have been working at repurposing a mid-2009 MacBook Pro (5,5) as dual-boot OS X and Ubuntu 12.04

I have gotten fairly far, but post-installation of Ubuntu, it is failing to reboot.  This was a machine with a failing HD, and I decided that while I was upgrading the drive, I would make it dual boot

What I have done so far:
1) Single boot install from live 12.04 CD of Ubuntu (worked fine, standard .iso)  - I did this to test and make sure ubuntu would install and work ok.

2) erase and re-partition and reinstall of OS X Lion.  (partitioned disk... I now have working OS X including the EFI partition, OS X main partition, Recovery partition) In Disk Utility I created additional partiton for linux.  + one for shared files.  - Created these as hfs+ 

3) Install Refit  - Verify  that I can boot into OS X fine.

4) Install ubuntu 12.04 --- This seemed to work fine, ( I erased one of the hfs+ partitions, and re-created an ext4 and a swap partition from the free space)
 but I had a problem at the end of the install - It gave an error attempting to install grub into the ext4 partition I installed linux on. It have me additional chance to try to re-install grub,  I tried to install onto the drive (sda) - I also tried creating a small additional boot partition by dividing up the swap into two partitions, and installing onto this.

After this, I tried fixing things with boot-repair, and taking the defaults. at one point I also ran the refit partition sync.  Now, whether I try booting directly via EFI (option key) or via Refit, the Ubuntu install shows up (as tux penguin under refit, or as "windows" under EFI/option key) - but in both cases I get a black screen with "missing operating system"

Here is my boot-repair pastebin link: [http://paste.ubuntu.com/1503917/](http://paste.ubuntu.com/1503917/)

I suppose I could just do a re-install of ubuntu, but i want to use this as a learninng experience about the wacky-world of dual boot mac intel.:D
Thanks!

---

### Post by RMXO on 2013-01-07
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

Follow those directions to dual boot & you should have no problem.

---

