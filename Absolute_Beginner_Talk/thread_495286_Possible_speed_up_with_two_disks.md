---
title: "Possible speed up with two disks"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by RTrev on 2007-07-07
I've been pretty much discouraged from trying to do software RAID-0 on my system disk(s), but it occurred to me that perhaps I could still benefit from having two disks involved in running the system.

What if I were to boot in maintenance mode, pick some of the directories like /usr /var /tmp and so on, and copy them to another disk.  Then simply put symbolic links on the current system disk pointing to those directories?

I'd be dividing some of the load over multiple disks, without having to figure out how to keep the /boot directory out of the RAID-0 array.  It wouldn't be as efficient, but it would be bound to help some, if it would work at all.

Would I incur any overhead from the system constantly having to interpret those symbolic links?

Is this a really bad idea, or does it have some merit?

Thanks,
Bob

---

### Post by chuckyp on 2007-07-08
Why use the symbolic links why not just mount the drive?

---

### Post by RTrev on 2007-07-08
> **chuckyp said:**
> Why use the symbolic links why not just mount the drive?

Not sure I understand the question.  The drive is mounted all the time, but now it's just being used for data.  I thought if it shared the load with the boot disk it would speed things up a bit, so thought I'd copy some directories to it and link to them.  

Is that making sense?  I just figured on a live system I should do the copying logged into single user mode..

---

### Post by Artemis3 on 2007-07-08
That won't do much i think. But check your swap, make another swap partition in the other disk and the swap access will improve (if pATA, disks must be on different cables). Better to have 2 256mb swap partitions (each on different disk) than 1 512mb. It might be late, but reiserfs instead of ext3 improves things a little and saves a lot of space.

The mounting means that you can make separate partitions just for those folders you mention, and mount them (in fstab). The partitions need not to be all in the same disk. A very simple and common thing is to make / in a partition, and /home in another, think of it as as a "system" partition and a "user data" partition. Quite useful when you want to upgrade from scratch without losing your data.

More complex methods involve having separate partitions for different folders of the "system" partition, eg: /var and /tmp somewhere / elsewhere, plus /home.

Yes you can have many different partition schemes, just make sure you do "manual" at the install (nor guided). And on top of that, there is also LVM; that might even ease things ^^

With lvm you take a physical disk (or partitions) and assign volumes to it (them), where you mount your things. Later you can easily resize the volumes without pain. You could even extend your volume into other physical disks (and partitions)... So your /home could span to 3 physical disks you see it as a large volume where you have just /home mounted. Neat huh?

More here: [http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)

---

### Post by RTrev on 2007-07-08
Thanks much!  Going off to read those LVM links.  That just might be the cat's meow.  :)

---

