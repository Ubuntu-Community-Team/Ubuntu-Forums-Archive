---
title: "NTFS partition not showing up this time"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by onthefence on 2008-02-15
So, I did a fresh install of Gutsy and whereas before it had automatically mounted the other NTFS partitions, now I am getting none of them. 

Basically my laptop drive is partitioned as follows:
1. Swap space 
2. ext2 - Linux isntall
3. NTFS - Windows install
4. NTFS - documents storage only, no OS installed here.

Now, in all honestly I have changed the partitions around since the last fresh isntall of Ubuntu, so I may have done something I am not aware of, but is there a way to view and mount the partitions.
I'm a newbie so speak slowly please.

I think I can list partitions in a terminal
(can't remember command)
then, mount the partition:
mount /dev/sdaX

Does this sound right?

Please help with commands or with other possible problems with mounting NTFS partitions.

Thanks

---

### Post by spiderbatdad on 2008-02-15
```
fdisk -l
``` careful when shutting down windows to do so cleanly...not hibernate windows, then boot Ubuntu.

---

### Post by onthefence on 2008-02-15
GENIUS!

I've always been the curious type, do you mind explaining? I understand some things don't deserve explanation...Although I can understand that a saved state would mean saving mounted partitions, I don't understand why ubuntu cares since the session isn't active.

Problem solved.

---

### Post by spiderbatdad on 2008-02-15
Unfortunately, I am not intelligent enough to know the reason. I can usually fake a good line though. I only suggested the clean shut-down because I have hung around the forums enough to have seen the issue a number of times.:popcorn:

---

