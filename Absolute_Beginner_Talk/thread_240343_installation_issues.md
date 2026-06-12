---
title: "installation issues"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by chester on 2006-08-20
I have been trying to install on and off for a few days now and i seem to be running into some of the same problems each time i give it a go. I successfully download and burn the iso to a disk and the live cd works perfectly, but when i try and install i run into a couple of problems:

1. when i try and choose the first hard drive resizing option on step 5, i get an error that says not enough space (i think that is what it says)i haven't tried to reformat the entire drive yet, option 3 (the one that uses the largest contiguous space will give me two error after i try and go beyond that point (failed to partition drive, after which it still allows me to go further, the disk starts spinning again and then it tells me that there is no root file system)i also have not tried to manually resize the hard drive since i am essentially a wuss and scared of mucking something up beyond repair.

sorry that was a long #1

2. So i tried to install it using instlux and it says that it can't read the data off of the disk (or something to that effect). I used instlux and the ubuntu live disk to both  check the integrity of the disk and instlux says it is valid but the ubuntu live cd tells me i have two bad checksums

any thoughts comments suggestions cyanide pills?

---

### Post by zxee on 2006-08-20
Just to get the ball rolling on this I would suggest, that while running from the live cd, you open a terminal (Applications>Acessories>Terminal) and type > sudo fdisk -l That will provide your hard disk info. Post that here, and someone should be able to give you a hand on how to get ubuntu installed. 
You may need to learn to use cfdisk though to set up the partition. We will know more after you provide that disk info.

---

### Post by agurk on 2006-08-20
Some people seem to have been more successful using the alternate (text mode) install CD instead. I'd follow the previous poster's advice first and post some more info though.

---

### Post by chester on 2006-08-20
Thanks guys, this is what i have:

Disk /dev/hds: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot       Start        End       Blocks      Id      System
/dev/hdal   *            1       3647     29294496       7      HPFS/NTFS


Watcha think?

---

### Post by agurk on 2006-08-21
Umm.. I'd try the alternate CD. 

[size=1](then again, I'm a drooling, helmet-wearing retard ;))[/size]

---

### Post by zxee on 2006-08-22
> **chester said:**
> Thanks guys, this is what i have:

Disk /dev/hds: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot       Start        End       Blocks      Id      System
/dev/hdal   *            1       3647     29294496       7      HPFS/NTFS


Watcha think?

From what you supplied it looks like your disk has just one parttion for windows. Is that correct?
You will need to shrink that partition to make room for a partition for ubuntu to format and install to. The alternate cd by the way won't be any real help-since you said earlier that you don't want to use commandline tools. In this situation perhaps your best bet is to get some commercial partition shrinking softwre-like partition commander or whatever you feel good about using. Once you've created a partition you can then try the ububntu installer again. Hope that helps.

---

