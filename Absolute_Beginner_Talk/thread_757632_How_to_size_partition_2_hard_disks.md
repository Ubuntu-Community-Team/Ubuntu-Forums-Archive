---
title: "How to size/ partition 2 hard disks"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by yeehi on 2008-04-17
I would like to install the new Hardy Heron, when it arrives.
I have 2 hard disks.

I am thinking of using  VMware to run Vista on my Ubuntu system.

I would like to keep all the data documents, like photos and text files that are created in either Vista or Ubuntu in a dedicated  partition. 

What do you think the best way is to size / partition my system, which has 2GB of memory?

My concerns are:

1) Which partitions to allocate as primary/secondary
2) How much swap space to have
3) Allowing enough space for several large applications to be installed into Vista
4) Allowing enough space for several large applications to be installed into Ubuntu
5) An appropriately sized boot partition
6) Proper names for the partitions

Thank you for your help! :)

---

### Post by halln on 2008-04-17
this might help link: [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by halln on 2008-04-17
do know but this might help as well link: [http://www.linux.com/feature/114157](http://www.linux.com/feature/114157)

---

### Post by northern lights on 2008-04-17
1) Ubuntu (or any other Linux distro, for that matter) doesn't care much what partition it's installed on. Simply make sure your Windows is not only on a primary partition (i.e. not on one in an extended partition), but also at best on the first partition of the first harddrive (hd0,0 in GRUB syntax, hda1 if you have IDE devices, otherwise sda1).

2) Depends on how much you can afford (i.e. how large your HDD(s) is/are) and the size of your physical memory (the more RAM, the less often will swap (virtual memory, equivalent to the pagefile in windows) be used in the first place). In general 1GB is pretty sensible.

3) No idea how much space Vista hogs itself. Check and add to liking. If you don't play Windows games, 10gig for apps should be plenty. If you plan on installing a multitude of new generation games - well you'd know how large those can get.

4) Minimum requirements for Gutsy were given as 5GB. A functional Ubuntu can do with 2 to 3. My system for instance is loaded with apps and the Ubuntu partition is 10.8 gig large including a 7gig /home/ (i.e. my system with apps is 3.8 ). 10 gig should suffice to start with, especially if you plan to store large data on separate partitions.

5) What do you mean by "boot partition"?

6) "Names" are a Windows thing. Linux labels your drives as follows: IDE devices are hdxy, SATA or USB devices sdxy, where x declares the drive and y the partition. If you have a setup with two IDE drives and an additional external USB, for instance, the first IDE will be hda, the second hdb and the USB sda. The second partition on the second IDE would thus be hdb2, which translates to (hd1,1) in GRUB syntax...

---

### Post by yeehi on 2008-04-17
> **northern lights said:**
> 1) Ubuntu (or any other Linux distro, for that matter) doesn't care much what partition it's installed on. Simply make sure your Windows is not only on a primary partition (i.e. not on one in an extended partition), but also at best on the first partition of the first harddrive (hd0,0 in GRUB syntax, hda1 if you have IDE devices, otherwise sda1).

2) Depends on how much you can afford (i.e. how large your HDD(s) is/are) and the size of your physical memory (the more RAM, the less often will swap (virtual memory, equivalent to the pagefile in windows) be used in the first place). In general 1GB is pretty sensible.

3) No idea how much space Vista hogs itself. Check and add to liking. If you don't play Windows games, 10gig for apps should be plenty. If you plan on installing a multitude of new generation games - well you'd know how large those can get.

4) Minimum requirements for Gutsy were given as 5GB. A functional Ubuntu can do with 2 to 3. My system for instance is loaded with apps and the Ubuntu partition is 10.8 gig large including a 7gig /home/ (i.e. my system with apps is 3.8 ). 10 gig should suffice to start with, especially if you plan to store large data on separate partitions.

5) What do you mean by "boot partition"?

6) "Names" are a Windows thing. Linux labels your drives as follows: IDE devices are hdxy, SATA or USB devices sdxy, where x declares the drive and y the partition. If you have a setup with two IDE drives and an additional external USB, for instance, the first IDE will be hda, the second hdb and the USB sda. The second partition on the second IDE would thus be hdb2, which translates to (hd1,1) in GRUB syntax...

1) Windows will be installed after the Ubuntu installation is completed, via VMware. This system will not be dual booting. To ensure that windows goes onto the first partition of the first hard disk, should I set up something/allocate space during the initial installation of Ubuntu? 

2) I thought the rule of thumb was double the size of the memory to create swap space. I have large HDDs so 4 Gigs for swap is OK, I think. Or is that excessive?

3) Vista and its applications need loads of space. I would say 20 Gig, and 40 wouldn't be too large. I am thinking of leaving an entire 60GB HDD just to vista. That might make things simpler. I would leave the first HDD to vista, but don't know how to do this during installation.

By boot, I mean /boot (iirc) - it is the place where you put grub, i think.

Can vista understand ext3? Should I format the first HDD as fat32? or what?

Thank you for your help with this. I am very unsure about how to do this.

---

### Post by northern lights on 2008-04-17
1) If you wanna run Windows only via a virtual machine, you need not allocate any space or partition for it in the first place.

2) If you don't give a damn about a few gigs, there is nothing to keep you from having a 4 gig swap. Unless you're planning on running a thousand apps at the same time or on never rebooting for a month, I doub't it will ever near fill up. But too much is never enough. So as long as it really doesn't hurt to loose a few gig, go for it.

3) If you really wanna use Vista that excessively, why VMware and not a regular dual boot? In the latter case, leaving a 60 gig HDD is fair enough. Once again, if you have more and can afford.

/boot needs not be a separate partition. It resides well right on your main ext3.

Without additional apps, Windows will not read ext3. However, FAT32 is really outdated and since ntfs-3g (which are included in Ubuntu since Feisty), Ubuntu mounts, reads from and writes onto NTFS partitons out of the box.

---

### Post by yeehi on 2008-04-17
One reason I would like to VMware Vista, rather than dual boot, is because I believe i would be able to run  vista in a window inside Ubuntu - use the vista aps as and when I need them, and then revert quickly back to Ubuntu. 

Maybe I am wrong, but I think that I would be less likely to get virus trouble on Vista this way, too.

I don't want to have to, for example, think "Oh, I must check/reply to email now" and have to reboot from Linux to Vista and then back again.

---

### Post by northern lights on 2008-04-17
As far as email goes, my tip would be to set up your email clients (for instance thunderbird in both Linux & Windows) to use IMAP. The emails will remain on the server and be accessible from both your Linux and Windows...

I boot my Windows (I have an XP installation) rarely, but if so, I'd rather have the real thing running. It's personal preference, I guess.

Also, it's never a bad idea to have two operationg systems (of whatever sort, for that matter - it could very well be any other linux distro) installed in the first place. If you're Ubuntu dies, you're virtualmachine will also be shot...

---

### Post by timcredible on 2008-04-17
> **yeehi said:**
> I would like to install the new Hardy Heron, when it arrives.
I have 2 hard disks.

I am thinking of using  VMware to run Vista on my Ubuntu system.

I would like to keep all the data documents, like photos and text files that are created in either Vista or Ubuntu in a dedicated  partition. 

What do you think the best way is to size / partition my system, which has 2GB of memory?

My concerns are:

1) Which partitions to allocate as primary/secondary
2) How much swap space to have
3) Allowing enough space for several large applications to be installed into Vista
4) Allowing enough space for several large applications to be installed into Ubuntu
5) An appropriately sized boot partition
6) Proper names for the partitions

Thank you for your help! :)

what I would do:

1) all as primary
2) 2GB if you have >200GB of hd space
3) if you're using vmware, you don't need to have a partition for vista
4) 40gb if you're installing vista inside vmware
5) use #4
6)
  / (40gb)  for boot partiton, where you install ubuntu apps
  /data (rest of space) for your ubuntu data, your vista data has to go inside vmware files

---

