---
title: "If I delete GRUB, will windows still boot?"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by ConsummateK on 2007-05-30
I'm thinking of jumping ship from AMD64 to i386....Right now I'm dual booting to WindowsXP and Ubuntu with GRUB.

My plan to make the switch was to download the bootable version of GPartition and use it to delete the Linux partition. I would then use Windows to format the new space into NTFS (So windows had the entire drive) and then boot to the Feisty i386 Live CD and use it to resize the big partition and create it's own. 

I know this seems like a lot of extra work (it very well may be) but the only luck I've had with Ubuntu installs so far has been using the resizing tool. My question is...once I use GPartition to kill the Linux partition will the MBR take over and boot to Windows? Or, if I use my XP install CD could I just format it from there and run the resize...and then after I had reinstalled would GRUB pick everything back up?

As always, insight is much appreciated :D

---

### Post by drowner on 2007-05-30
sorry. bad advice.

---

### Post by ConsummateK on 2007-05-30
Like I said...I was just doing the way I know worked for me before. Currently i'm not having any problems other than AMD64 is proving a little more daunting than a brand new Linux user would like. 

Basically I just need to replace AMD64 with i386 on a drive that is dual booting Ubuntu and XP. 
How would one go about simply installing over top of the current version? 

As far as just installing directly into the blank space left after wiping the Linux partition goes I'm a little confused as how to manually partition up the drive what with swap, root and main partitions being required.

---

### Post by hellmet on 2007-05-30
I'm not sure of Gparted, but you could use XP's installation cd to reinstall your MBR within a few minutes. I'm still not sure why you are following a longer process!!

---

### Post by drowner on 2007-05-30
> **hellmet said:**
> I'm not sure of Gparted, but you could use XP's installation cd to reinstall your MBR within a few minutes. I'm still not sure why you are following a longer process!!
edit: entirely incorrect advice.

---

### Post by gn2 on 2007-05-30
All the answers you need are in here: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by louieb on 2007-05-30
> **gn2 said:**
> All the answers you need are in here: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
By all means check out Herman's site. You already have your partitions set up. If it were me I'd reuse them. Its been my experience that when I have trashed XP so bad it would not boot -  It has been when I was resizing it partition. and you plan to do it twice?

---

### Post by dstew on 2007-05-30
If you remove the Linux partition, grub will not be able to boot Windows because it needs its stage 1.5 or stage 2, which is on the Linux partition. If you remove the Linux partition, you need to do **fixmbr** from the Windows recovery console to get your computer to boot Windows. You could even do fixmbr before you remove the linux partition.

---

