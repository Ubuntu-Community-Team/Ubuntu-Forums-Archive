---
title: "[SOLVED] Preparing a hard drive for Ubuntu setup"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by nuddernuby on 2007-08-15
When planning a new installation of Ubuntu (7.04) as the only OS on a computer that was previously running Windows, is there any preparation of the hard drive required before installation?
If so, could you please indicate what the required steps are.
Thank you

---

### Post by grimmoner on 2007-08-15
personaly when i installed Ubuntu over windows,
didn't make any preperations.

In the installation process, when i was asked,
i just choose to erase any partition and then create an ext3 and swap.

---

### Post by MQMike on 2007-08-15
That’s almost   a religious issue.

Basically, you have two general choices:

1   Use the Ubuntu installer do the partitioning/formatting of your hard drive during the installation of Ubuntu.

2  Do the partitioning/formatting of the hard drive yourself using another program.  A favorite (and EASY to use!) is GParted, and it’s a good idea to have a Live GParted CD on hand.
GParted:   [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
GParted how-to:   [http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)


The issues are:

Your Linux should have 3 partitions:
/    (the root files of the operating system)
/swap    (swap files for memory management—used by the OS)
/home    (a place for all your stuff—data, photos, music, etc.)

Others here will give you recommendations for the sizes of these partitions.
Usually, /swap is 1 ½  times the size of your PC’s RAM (but many will say that’s a bit too much).  So if your RAM is 1 GB, /swap would be set at 1.5 GB.

/, root files – a minimum of 3-5 GB, many will say at least 8-10 GB.

/home – Gee, anything from 1 GB on up, depending on your needs.  10-50 GB would be a typical number you’d see for average users.

Then you need formatting.  Linux uses FAT 16 and FAT32, and its own ext2, ext3, and reiserfs.  You are safe with ext2 and ext3, for sure.  Windows can read FAT16 and FAT32.

Let others chime in here with their specific advice/experience.  Per haps you can tell u more about how you will use your PC.

---

### Post by carloslosgrande on 2007-08-15
Personally I found it MUCH easier to let the install do the partitioning for me and then later I adjusted it (with the GParted live cd) to suit my needs.
I always try to follow the philosophy of kiss.

---

### Post by MQMike on 2007-08-15
Yes, that’s right.

And then others feel better (safer?) doing the partitioning separate from the intensity of installing Ubuntu.  Maybe easier to relax and think and make experimental changes to the partitions/formatting by using GParted beforehand and off to the side.

I’ve done it both ways, on internal HD, external HD, and UFD (flash drive).

---

### Post by ramjet_1953 on 2007-08-15
My personal feelings on partitioning are along the same lines as MQMike's.

I like to have a separate /home partition and the default automatic Ubuntu install doesn't give you this.

Nevertheless, if you are not comfortable with manual partitioning, go ahead and use the auto setup.

Your install won't run any slower, or really be inferior.

It is just generally looked upon as "good housekeeping" by having a separate /home partition.

Others  also say that separate /boot /var /etc partitions are also a good idea.

Regards,
Roger :cool:

---

### Post by armandh on 2007-08-15
restating the obvious
the reason behind a seperate home partition for your user data....
easier backup and if you want the latest or manage to trash the OS you can install the newest easily.
I have come to like the parted magic utility [http://partedmagic.com/](http://partedmagic.com/)
just leave 10 mb and install with the use unallocated option

---

### Post by nuddernuby on 2007-08-15
Thanks for the contributions, guys. 
At this stage I have to backpedal a bit to the preparation stage.  If I understand correctly, Feisty will sort itself out as far as formatting etc is concerned.  If that is so, it means I may have a different problem, as I am not getting Ubuntu to install at all - it just hangs up on me after the first couple of steps that follow selecting the install option on the start-up screen.

Guess I'll need to do a thorough hardware diagnosis.
Thanks again to all.

---

### Post by Drakkor on 2007-08-15
Did you download the correct version for your computer ? Also check the md5sum of the .iso
to make sure you don't have a corrupt download, then click the option to "Check CD for defects"
when booting to the live CD to make sure the burn is good. If bad, burn at a lower speed. Hope this helps, Good Luck ! :)

---

### Post by nuddernuby on 2007-08-15
> **Drakkor said:**
> Did you download the correct version for your computer ? Also check the md5sum of the .iso
to make sure you don't have a corrupt download, then click the option to "Check CD for defects"
when booting to the live CD to make sure the burn is good. If bad, burn at a lower speed. Hope this helps, Good Luck ! :)

Checked all these without much luck, but I am happy to share that the problem turned out not to be with disk formatting but with the video card or, more specifically, that the system did not like the idea of dual monitors.  Discovered this quite by chance. When the card was removed, the install went through. Phew!

Thank you again for your help.

---

