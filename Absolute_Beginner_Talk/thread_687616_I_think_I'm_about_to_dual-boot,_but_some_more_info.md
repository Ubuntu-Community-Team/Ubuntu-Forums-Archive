---
title: "I think I'm about to dual-boot, but some more info needed."
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by ChristDude on 2008-02-04
Well, I recently reinstalled XP home on my laptop due to the install getting really, really slow and sluggish. In the setup, I went ahead and created 2 other partitions along with my main XP partition. One's a 15 GB and the other is 10 GB, and both are formatted to NTFS. It is possible to install Ubuntu on one of those partitions correct?

Thanks.

---

### Post by NightwishFan on 2008-02-04
You should leave the partition you want for linux unformatted so Ubuntu can format it to ext3 during the installation. After doing that, use the "Use largest continuous free space" option in the live cd install.

---

### Post by ChristDude on 2008-02-04
Crap, all of them are formatted. Anyway to undo me formatting to the NTFS file system? I should have thought about that.

---

### Post by NightwishFan on 2008-02-04
I believe you can get a gparted live cd. I'm not sure if Ubuntu would reformat an empty ntfs partition on its own as I have never tried it.

---

### Post by ChristDude on 2008-02-04
Hmm, would it be possible to take one of the NTFS partitions and make a new partition using the space that is in there using the Ubuntu Partitioning Tool?

---

### Post by b0b138 on 2008-02-04
Boot into xp and use disk management to delete the partitions. Then create new one(s) but don't format them

---

### Post by NightwishFan on 2008-02-04
[http://psychocats.net/ubuntu/index.php]("http://psychocats.net/ubuntu/index.php") is a guide for the installation process.

---

### Post by LRT on 2008-02-04
a little outdated but should do the trick,,,

[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty)

---

### Post by jan quark on 2008-02-04
also have a look at

[http://apcmag.com/node/5162/](http://apcmag.com/node/5162/)

---

### Post by ChristDude on 2008-02-04
Thanks for all the guides, yet I know a lot of that already. I read those too much when I was first learning about Ubuntu. Anyway, here's a little bit of a better explanation of what I think I'll do now. Right now, I have a 50 GB (XP install partition), 15 (plain NTFS - used for backing up), and 10 (NTFS for anything else). I'm thinking I will just simply take maybe 10 GB off my XP partition and use it for Ubuntu.

One question though. I've been reading these guides, and I still don't understand a SWAP partition or what it is used for. Any assistance with that? Thanks :guitar:.

---

### Post by jhenager on 2008-02-04
It's like the permanent swap file for windows.

---

### Post by ChristDude on 2008-02-04
I'm clueless to what a SWAP partition does whatsoever. I need some more info on it.

---

### Post by ChristDude on 2008-02-04
Never mind about that, just googled it and found out it can be used as RAM when you're actual RAM is low. I have a gig or RAM, so 512 mb would do well as my swap.

One more question. My 50 gig NTFS XP partition can be resized to make my ex3 Ubuntu partition correct? If this is the case, I should have Ubuntu in the next day or two.

---

### Post by b0b138 on 2008-02-04
dont manually make a partition for the swap. it will be done automatically during the install when you select guided partitioning (and it wont even make one that big) While I am no linux expert, it seems linux does a much better job compared to windows of actually using your ram before dumping stuff into the swap

---

### Post by ChristDude on 2008-02-04
> **b0b138 said:**
> dont manually make a partition for the swap. it will be done automatically during the install when you select guided partitioning (and it wont even make one that big) While I am no linux expert, it seems linux does a much better job compared to windows of actually using your ram before dumping stuff into the swap

Well, then I'm confused. According to this tutorial ([http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty]("http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty")), it shows you making the swap partition manually. Confused a bit now.

---

### Post by tobydeemer on 2008-02-04
> **ChristDude said:**
> Never mind about that, just googled it and found out it can be used as RAM when you're actual RAM is low. I have a gig or RAM, so 512 mb would do well as my swap.

One more question. My 50 gig NTFS XP partition can be resized to make my ex3 Ubuntu partition correct? If this is the case, I should have Ubuntu in the next day or two.

Hi-

Yes, you can resize the XP NTFS partition, and the Ubuntu install CD will be able to walk you through that pretty well, but first it would help to boot into XP, and run a full defrag and chkdsk to make sure there are no errors before resizing. If there are any errors and you go ahead anyway, you run a much greater risk of data loss. (As I'm sure you've read already.) Of course, make backups of everything you can't afford to lose. I know I'm stating obvious, but sometimes it helps... :) 

Also, I second the previous post of, also through XP, deleting the new NTFS partitions you created, and then letting the install CD format the space it's going to use when you get to that point. Once you've run the disk cleaning in XP, look at how much disk space it's really using, decide how big you would like XP to be, and then tell the installer to resize it and use the rest of the space after that for Ubuntu. XP will be on something like hda1 and hda2 from 0 to 50GB, and you can specify it to be shrunk to hda1 and hda 2, 0 to 30GB or however large you want. This is the process I did on my laptop with an 80GB hard drive, with 35 for XP and 45 for Ubuntu.

Anyway, I hope all this helps, and if you know it already, I'm sorry. Good luck. :)

---

### Post by b0b138 on 2008-02-04
you can do it like that turorial. you can also let the install do it for you. on step 6 of the linux install on that tutorial, you will have an option (which isnt showing on that tut.) for guided - use largest continuous free space. Your largest continuous free space will be the 10gigs once you delete that partition in xp.

---

### Post by tobydeemer on 2008-02-04
> **ChristDude said:**
> Well, then I'm confused. According to this tutorial ([http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty]("http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty")), it shows you making the swap partition manually. Confused a bit now.

There are a couple of different install methods, and one involves making the swap manually, and making a separate /Home folder partition as well. These are options that are good, but you won't necessarily gain or lose anything by letting the installer do this for you. And it's also something you can do from inside Ubuntu later on if you decide to. From my experience, Ubuntu's latest installer Live CDs are really good at handling XP, creating an easy boot menu with Grub, and living nicely on HDs with other OS's installed. Again, I hope this helps...

---

### Post by NightwishFan on 2008-02-04
Swap is the same thing as a page file. Its where your ram is paged to disk to save memory for more programs.

---

### Post by ChristDude on 2008-02-04
> **tobydeemer said:**
> Hi-

Yes, you can resize the XP NTFS partition, and the Ubuntu install CD will be able to walk you through that pretty well, but first it would help to boot into XP, and run a full defrag and chkdsk to make sure there are no errors before resizing. If there are any errors and you go ahead anyway, you run a much greater risk of data loss. (As I'm sure you've read already.) Of course, make backups of everything you can't afford to lose. I know I'm stating obvious, but sometimes it helps... :) 

Also, I second the previous post of, also through XP, deleting the new NTFS partitions you created, and then letting the install CD format the space it's going to use when you get to that point. Once you've run the disk cleaning in XP, look at how much disk space it's really using, decide how big you would like XP to be, and then tell the installer to resize it and use the rest of the space after that for Ubuntu. XP will be on something like hda1 and hda2 from 0 to 50GB, and you can specify it to be shrunk to hda1 and hda 2, 0 to 30GB or however large you want. This is the process I did on my laptop with an 80GB hard drive, with 35 for XP and 45 for Ubuntu.

Anyway, I hope all this helps, and if you know it already, I'm sorry. Good luck. :)

Thankfully, I just reinstalled XP two days ago, so I still have everything backed up and I doubt I will need to defrag i right now.

I'm a little confused, I want to keep all the partitions I have right now for XP that are formatted in NTFS. As long as I can resize my XP partition for Ubuntu and the swap, I will be fine. As long as that won't affect the Xp or Ubuntu installs.

---

### Post by tobydeemer on 2008-02-04
> **ChristDude said:**
> Thankfully, I just reinstalled XP two days ago, so I still have everything backed up and I doubt I will need to defrag i right now.

I'm a little confused, I want to keep all the partitions I have right now for XP that are formatted in NTFS. As long as I can resize my XP partition for Ubuntu and the swap, I will be fine. As long as that won't affect the Xp or Ubuntu installs.

Sorry, I was referring to the new blank NTFS partitions you mentioned creating. Anyway, yes, you can keep the XP partitions- just the same as they are, or you can shrink them a little to give Ubuntu more room if you like. Either way, both OS's should be fine. I've had a dual-boot system that was done using this method working beautifully for six months with no issues from XP or Ubuntu. If you don't want to shrink XP, then just tell the installer to use the largest contiguous free space, and it will install to what's left after XP's space on the disk. If you want it to use the whole non-XP 25GB, then the easiest thing to do would be to delete any partitions (using Disk Management in XP) that are not part of the 50GB XP install, and let the CD installer use the 25GB. (I hope I explained what I mean a little better this time... Sorry.)

---

### Post by ChristDude on 2008-02-04
OK, so here's the plan. I'm going to take my 50 gig XP partition, resize it to 40 gig for XP and 10 for Ubuntu along with using that to get my swap partition and install away. Thanks for all the help everyone.

---

