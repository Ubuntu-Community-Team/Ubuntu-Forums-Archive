---
title: "Difficulty booting into X-K-Ubuntu with many errors"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by pmueller on 2007-06-14
Hello,

I am wondering how I should set up a grub boot list again so that it will work for me. I have XP on hda1, fat32 for shared windows and linux files on hda2, Kubuntu with Xubuntu and Ubuntu feisty installed on hda3, and my home directory ifor K-X-Ubuntu on hda4. I also have Mepis on hdb1, Christian Ubuntu (feisty)on hdb2, Linux Swap on hdb3, and the newly installed SAM Lnux on hdb4 that replaced an old version of Ubuntu dapper with edgy and fiesty upgrades that developed problems for me.

When I try to boot into my feisty only K-X-Ubuntu, I get these errors:

Unable to resolve 'UUID= ....... etc.
fsch died with exit status 9
files system check failed
A log is being saved in /var/log/fsck/checkfs
The program 'apt-get is currently not installed. You can install it by typing apt-get install apt.

When I try to boot Christian Ubuntu on a different partition I get errors as well.

To get into the K-X-Ubuntu I am given the choice of hitting Control D to continue with booting and eventually I can get it started.

My problems booting into (K)(X)Ubuntu first occured after installing SAM Linux and editing my menu.lst for my grub boot located on Christian Ubuntu. On the menu.lst, I removed entries regarding an incorrect location for Mepis, which I moved myself to a different partition, and I removed old references to a earlier installation of Ubuntu, which became useless to me after doing several upgrades from dapper, to edgy, to feisty.

Should I try to get grub to build a list again? Should I install a brand new distribution so that It can put my current partitions together again?

Thanks,

Paul In NH

---

### Post by confused57 on 2007-06-14
> **pmueller said:**
> Hello,

I am wondering how I should set up a grub boot list again so that it will work for me. I have XP on hda1, fat32 for shared windows and linux files on hda2, Kubuntu with Xubuntu and Ubuntu feisty installed on hda3, and my home directory ifor K-X-Ubuntu on hda4. I also have Mepis on hdb1, Christian Ubuntu (feisty)on hdb2, Linux Swap on hdb3, and the newly installed SAM Lnux on hdb4 that replaced an old version of Ubuntu dapper with edgy and fiesty upgrades that developed problems for me.

When I try to boot into my feisty only K-X-Ubuntu, I get these errors:

Unable to resolve 'UUID= ....... etc.
fsch died with exit status 9
files system check failed
A log is being saved in /var/log/fsck/checkfs
The program 'apt-get is currently not installed. You can install it by typing apt-get install apt.

When I try to boot Christian Ubuntu on a different partition I get errors as well.

To get into the K-X-Ubuntu I am given the choice of hitting Control D to continue with booting and eventually I can get it started.

My problems booting into (K)(X)Ubuntu first occured after installing SAM Linux and editing my menu.lst for my grub boot located on Christian Ubuntu. On the menu.lst, I removed entries regarding an incorrect location for Mepis, which I moved myself to a different partition, and I removed old references to a earlier installation of Ubuntu, which became useless to me after doing several upgrades from dapper, to edgy, to feisty.

Should I try to get grub to build a list again? Should I install a brand new distribution so that It can put my current partitions together again?

Thanks,

Paul In NH

Sounds like your UUID's have changed on one of your partitions that (K)(X)Ubuntu is attempting to mount in your /etc/fstab.
Open a terminal & check the current UUID's with:
```
blkid
```

then open your /etc/fstab & edit your UUID's to reflect the new UUID:
```
sudo cp /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab
```
you should be able to just copy & paste the new UUID to your /etc/fstab

---

### Post by pmueller on 2007-06-14
Hi

I am a little confused. I have problems with both Christian Ubuntu on hdb2 and K\X\Ubuntu on hda2. The grub that I use is on Christian Ubuntu, which was installed after the other ubuntu's. Do I edit fstab on each of the partitions or just Christian Ubuntu?  I use hda2 K-X-Ubuntu more than the hdb2 installation.

At any rate, I need to get some rest and I will try your suggestion out tomorrow.

Thanks,

Paul

---

### Post by confused57 on 2007-06-14
> **pmueller said:**
> Hi

I am a little confused. I have problems with both Christian Ubuntu on hdb2 and K\X\Ubuntu on hda2. The grub that I use is on Christian Ubuntu, which was installed after the other ubuntu's. Do I edit fstab on each of the partitions or just Christian Ubuntu?  I use hda2 K-X-Ubuntu more than the hdb2 installation.

At any rate, I need to get some rest and I will try your suggestion out tomorrow.

Thanks,

Paul
You'll need to run "blkid" and compare the /etc/fstab on each of the distros separately...for example, when you're booting your KXUbuntu, it's fstab is being read to mount partitions(using UUID) and the same goes for when you boot your Christian Edition.

---

### Post by pmueller on 2007-06-20
Hello,

Thanks to Confused57 who solved my problem. First I tried correcting the problems in my hda3 partition, where it turned out to be errors in my UUID for my Linux swap (hdb3) and my SAM Linux hdb4 partition. I still could not boot into the k-x-Ubuntu immediately. 

Next I checked for my errors in my hdb2 drive and found the same partitions with UUID corruption . I fixed the errors in this partition as well and I found that I was now able to boot into the two partitions without being stopped with cryptic messages.

Another satisfied customer. How much do I owe you?  P.S. I was late in getting back because I had a little flood in the apartment.

Paul M.

---

