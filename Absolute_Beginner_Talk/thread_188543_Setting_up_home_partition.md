---
title: "Setting up /home partition"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by xrchris on 2006-06-04
I have set up my laptop partitions as follows 

XP 30gb 
Shared FAT partition 41gb
/ 21gb
Swap 4gb

I was thinking about splitting my / partition to include a seperate /home partition but was wondering if it was worthwhile given that i have a shared FAT partition and whether i would have to reinstall Ubuntu to do this or if there was a way to just alter the existing setup?

---

### Post by adam.tropics on 2006-06-04
Easiest and quickest way since you have windows installed would be, if you have one to use a partition manipulation tool from windows, (or a live cd), which preserves your data. The issue being you can't mess with a mounted drive as far as I know.

A couple things though. Your swap partition is huge! Normally a size of 1.5 - 2 times your memory is advised. Although there is a point at which it becomes kind of moot as with say 2gb ram, the swap is hardly ever if ever actually gonna be used. The /home is always better kept on a seperate sizable partition. That way should you need to reinstall, you just tell the installer not to format /home, then once done, and when you have reinstalled your software, you will still have all your settings.

There are many more posts around with partitioning advice, best to read a few more before you dive in, but yes a seperate /home always good.

---

### Post by Lord Illidan on 2006-06-04
With a shared /home, if you ever need to reinstall ubuntu, your configurations and stuff will not be touched. So do make it.

---

### Post by xrchris on 2006-06-04
OK so...

The swap i just configured as twice my ram so i could drop to equal it and see no difference. 

I did try (when installing Dapper) to set up seperate /, /home and swap partitions but couldnt as kept getting message that only 4 primary partitions are allowed? couldnt see a way around this.

---

### Post by taurus on 2006-06-04
You can only have 4 primary partitions but can have as many as extended partitions.  So if you plan to have more than 4 partitions, better make the last one as logical and create two extended partitions with that...  So your HD now would look something like

/dev/hda1 --> XP
/dev/hda2 --> Share
/dev/hda3 --> /
/dev/hda5 --> /home
/dev/hda6 --> swap

---

### Post by xrchris on 2006-06-04
[QUOTE=taurus]You can only have 4 primary partitions but can have as many as extended partitions.  So if you plan to have more than 4 partitions, better make the last one as logical and create two extended partitions with that...  So your HD now would look something like

/dev/hda1 --> XP
/dev/hda2 --> Share
/dev/hda3 --> /
/dev/hda5 --> /home
/dev/hda6 --> swap[/QUOTE]

OK so... 

/dev/hda4 would be a logical partition which contains 
/dev/hda5 --> /home
/dev/hda6 --> swap

as extended partitions?

Also is there any need for the FAT share partition to be a prmary partition?

---

### Post by taurus on 2006-06-04
> **xrchris]OK so... 

/dev/hda4 would be a logical partition which contains 
/dev/hda5 --> /home
/dev/hda6 --> swap

as extended partitions?
[/QUOTE]
That's correct.  That's why you don't see /dev/hda4 in there.   said:**
> Also is there any need for the FAT share partition to be a prmary partition?
No.  You can make it an extended partition if you choose.  There's no rule where it should be.

---

