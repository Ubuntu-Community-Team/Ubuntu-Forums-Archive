---
title: "RAID 1 on Gutsy Gibbon...HELP!!!"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by pmartiz on 2007-12-31
](*,)I read and followed the instructions on [http://users.piuha.net/martti/comp/ubuntu/en/raid.html](http://users.piuha.net/martti/comp/ubuntu/en/raid.html) and it was great.  I have two (2) hard drives, each 160 GB, and I would like to create 4 x 40 GB RAID partitions.  However, as I understand Linux, I have to have *root *(/) and *swap* (swap) partitions.

I was trying to create the floowing partitions:
3.5 GB for */*
500 MB for *swap* and
four equal partitions (39 GB) with the reamining 156 on each drive.  I am sure that I am doing this wrong.  Can I create more than 4 partitions in Ubuntu?  Should I create 4 partitions of 40 GB each with the first 2 partitions being mounted in */* and *swap*?  If I mount the first 2 40GB partitions as *root* and *swap* what should I mount the 4th partitions as? I can only have one */home*.  Should I mount the remaining 40 GB partitions as */boot, /temp, /var* or what?  I am probably making this process harder than it needs to be.  I am new to Linux and would appreciate any assistance, comment, and remark.:confused:

---

### Post by overdrank on 2007-12-31
> **pmartiz said:**
> ](*,)I read and followed the instructions on [http://users.piuha.net/martti/comp/ubuntu/en/raid.html](http://users.piuha.net/martti/comp/ubuntu/en/raid.html) and it was great.  I have two (2) hard drives, each 160 GB, and I would like to create 4 x 40 GB RAID partitions.  However, as I understand Linux, I have to have *root *(/) and *swap* (swap) partitions.

I was trying to create the floowing partitions:
3.5 GB for */*
500 MB for *swap* and
four equal partitions (39 GB) with the reamining 156 on each drive.  I am sure that I am doing this wrong.  Can I create more than 4 partitions in Ubuntu?  Should I create 4 partitions of 40 GB each with the first 2 partitions being mounted in */* and *swap*?  If I mount the first 2 40GB partitions as *root* and *swap* what should I mount the 4th partitions as? I can only have one */home*.  Should I mount the remaining 40 GB partitions as */boot, /temp, /var* or what?  I am probably making this process harder than it needs to be.  I am new to Linux and would appreciate any assistance, comment, and remark.:confused:

HI and I have not set up a raid as of yet but as you see in the screen shot #4 there is 3 partition on each drive. As I understand it that the max partitions for a drive is 4 and as I understand your description you are trying to create 4x40 and swap and 3.5. SO you may have to create a extended partition to achieve this.

---

### Post by cliffa3 on 2008-01-02
Using the gnome partition editor (gParted), you'll likely have problems creating the 4th partition for the reason stated by overdrank.  If you can start from scratch, I'd try creating an extended partition out of the entire disk and then create any partitions you want.  I'm not entirely sure you can do that, so google around or see if someone else responds...meaning a drive might have to have at least one primary partition before you go extended/logical.  I know I have 3 primaries for Windows and using gParted I was able to create /, /boot, /home, and swap within an extended partition that spanned the rest of the drive (that windows wasn't using).  I haven't been successful in getting my raid-1 setup going fully yet, so you might want to check into dmraid and other things like lvm (if linux is your only os) if the problems you're having turn out to be dealing with your raid.  Good luck.

---

### Post by pmartiz on 2008-01-03
Thank you everyone.  I am still working on that server and now I started on another without completing the first...go figure!  This one I created 3 partitions much like the instructions and it works well until I disconnect one sdb2 and then Ubuntu just hangs.

I am going to try some solutions I found when I Googled the issue.  However, if anyone has any ideas as to how to fix bug #120375?

---

