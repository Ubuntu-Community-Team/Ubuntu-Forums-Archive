---
title: "Quick Question on installing"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by flintfinder on 2007-07-04
I am installing the latest Ubuntu on my desktop pc. Have a laptop that has duel boot (XP & Ubuntu) installed and after about three months of using it I find myself booting to Ubuntu most of the time. Great system. Now I want to have duel boot on my desktop, I'm installing it right now (never done it before) and I kind of need some expert advice on the Prepare Disk Space window. I **don't** want to erase the entire hard drive but which is the best selection. Use the largest continuous free space or manually edit partition table. Not certain how many gigs it will use up. I can spare 15-20gigs.

---

### Post by lisati on 2007-07-04
If you've already freed up some space, possibly the "use the largest free space" option. Otherwise have a think about the "guided - resize" option.

---

### Post by skwishybug on 2007-07-04
If you are comfortable editing the partition table yourself, I would recommend going for that. It will allow you the most control over what gets done with the drive.

As for how much you will use, if you are going to have a common partition or drive for storing your files, 10-15 Gbs should be more than enough. If you are going to have your home folder integrated with Linux, make it bigger since you will eat up space in saved files.

just my $0.02

---

### Post by flintfinder on 2007-07-04
No I'm not comfortable editing the partition table at this point but by selecting, Using the largest continous free space option, will that use up space not used by Windows.

---

### Post by TravMan63 on 2007-07-04
Win XP needs about 1.5 - 2GB minimum, add extra for programs etc...

To safely share data with linux - a fat32 partition is needed - you can install XP on that or create 2 separate partitions, XP system on NTFS (more secure)  Linux can read data off a NTFS partition but not write (safely - there are some workarounds - up to you if you wish to try).  XP and Linux can both read and write to FAT32

gparted is a tool for managing partitions

---

### Post by flintfinder on 2007-07-04
Thanks

---

### Post by coolen on 2007-07-04
> **flintfinder said:**
> I am installing the latest Ubuntu on my desktop pc. Have a laptop that has duel boot (XP & Ubuntu) installed and after about three months of using it I find myself booting to Ubuntu most of the time. Great system. Now I want to have duel boot on my desktop, I'm installing it right now (never done it before) and I kind of need some expert advice on the Prepare Disk Space window. I **don't** want to erase the entire hard drive but which is the best selection. Use the largest continuous free space or manually edit partition table. Not certain how many gigs it will use up. I can spare 15-20gigs.

I'd manually edit, personally. It's not as daunting as you might think, if you have a basic grasp of the concept of partition (not to mention a good way to get a little more experience).
If you've defragged recently, using the largest continuous free space should work, too.

---

