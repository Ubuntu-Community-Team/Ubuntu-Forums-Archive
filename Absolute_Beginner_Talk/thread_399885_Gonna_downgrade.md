---
title: "Gonna downgrade"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by CrucialTK on 2007-04-02
So after using 6.10 for the weekend, I'm gonna go ahead and roll back to 6.05. I managed to come across a 120 gig hd this past weekend, and I want to also use this along with my other hardware

So, what is the biggest partition available for Linux? Can it go as high as 150 gigs? (a 160 drive). I figure I'm gonna go ahead and reformat all three drive in the computer, so I'm looking at how to set them up. As always, any ideas are welcomed and heavily appreciated! Thanks again!

---

### Post by mikewhatever on 2007-04-02
I think the max size of partitions depends on the limit your BIOS supports, it does not matter for Linux.

---

### Post by crispy_420 on 2007-04-02
No limit as far as I know with ext3 format. There may be but it would be unreachable with your setup. I have mine running on a 200GB drive.

As far as other drives, use them for important data. Stuff like config files and media, basically stuff that may be hard to replace.

---

### Post by CrucialTK on 2007-04-02
> **crispy_420 said:**
> No limit as far as I know with ext3 format. There may be but it would be unreachable with your setup. I have mine running on a 200GB drive.

As far as other drives, use them for important data. Stuff like config files and media, basically stuff that may be hard to replace.

Well, I was gonna keep all my vitals on the 80 gig drive. The 160 gig is going to have to act as a music drive since it already has 130 gigs of music on it (but thats formattable because I've backed up that music onto my portable drive) and use the 120 gig for Video files such as Top Gear and various comedians work.

---

### Post by daniel of sarnia on 2007-04-02
I'm pretty sure ext3 maxis out just short of 16 TB as in 16000 GB. But ext4 will fix that. Either way I think you'll be fine ;)

---

### Post by CrucialTK on 2007-04-02
> **daniel of sarnia said:**
> I'm pretty sure ext3 maxis out just short of 16 TB as in 16000 GB. But ext4 will fix that. Either way I think you'll be fine ;)

Is there a way to format from NTFS to FAT32 using Ubuntu, or will I have to do it outside of Linux?

---

### Post by Clay_Banger on 2007-04-02
> **CrucialTK said:**
> Is there a way to format from NTFS to FAT32 using Ubuntu, or will I have to do it outside of Linux?

As far as i know, it isnt possible. But i know that partition magic can do it, but i have found that it hasnt worked that well 4 me, and i generally have 2 reinstall windows anyway.

---

### Post by CrucialTK on 2007-04-02
> **Clay_Banger said:**
> As far as i know, it isnt possible. But i know that partition magic can do it, but i have found that it hasnt worked that well 4 me, and i generally have 2 reinstall windows anyway.

howabout NTFS to EXT3?

---

### Post by jem7v on 2007-04-02
To just convert the file system without affecting the files? I doubt it, but if you just want to repartition the disk (without worrying about losing the data) you can do that pretty easily with the GParted LiveCD... [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

On the other hand, NTFS support is apparently now OFFICIAL instead of experimental in Ubuntu, as long as you download the right package to do it. Again, I've been seeing this pop up recently so you can probably find out more with Google.

---

### Post by bobpur on 2007-04-02
Go to : [www.distrowatch.com](www.distrowatch.com) for the Gparted live cd.

---

### Post by crispy_420 on 2007-04-03
I can't see any reason you would not be able to format NTFS to fat32. Even assuming you can't read/write to it because of drivers doesn't mean you can't format, that is just theory as it will be recognized as NTFS. But like somebody mentioned earlier, you will lose your data on that drive. As far as "official" support for NTFS, not to sure about that. Last I heard NTFS drivers were still beta, I may be wrong though.

---

### Post by CrucialTK on 2007-04-03
> **crispy_420 said:**
> I can't see any reason you would not be able to format NTFS to fat32. Even assuming you can't read/write to it because of drivers doesn't mean you can't format, that is just theory as it will be recognized as NTFS. But like somebody mentioned earlier, you will lose your data on that drive. As far as "official" support for NTFS, not to sure about that. Last I heard NTFS drivers were still beta, I may be wrong though.

it seems the NTFS drivers just came out of beta and are officially supported. However, i talked with a friend of mine last night and he made the point that because I wasn't running Windows on the computer, why not just switch to EXT3 and be done with it. So I did the Apt-Get for Gparted, and formatted one drive last night, and another this AM. Since I'm downgrading, I'm just reformatting the PC and then putting on 6.06. By the time I get back from work/practice, I should have a fresh install of Linux waiting for some commands to download all the various things I'll need for it. Excitement is ahead. 

As always, I appreciate every piece of input. This place is a really awesome resources for Newbs like me who're so new we haven't had our umbilical cords cut yet.

---

