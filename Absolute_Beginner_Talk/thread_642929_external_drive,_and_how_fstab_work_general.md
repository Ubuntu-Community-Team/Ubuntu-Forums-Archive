---
title: "external drive, and how fstab work general"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by Mular on 2007-12-17
I had a question regarding Fstab...

I been having some issues with fstab and sometimes my computer doesn't boot.. Like I get to ubuntu splash, it fills 1/4 the way then goes black.. Now I waited a long time one time and the comptuer rebooted and loaded fine (does ubuntu do like a hard drive scan or something if you shut it down improperly?)

Anyway the real question is this, my external drive is named annoyingly. Its a 500 gig, partitioned into 2 right. Auto it gets named disk for both parts, so I have like disk 1, 2 , 3 (3 is a partition on another HD) How do I change the name it gets assigned, and also if I add a custom entry into fstab and say I disconnect the external drive will I have a problem booting into my system? Or will fstab be booted to this point, see the hard drive isn't there and go on without it?

Hope that made sense lol

---

### Post by kpkeerthi on 2007-12-17
Read up on [Drives and Partitions]("https://help.ubuntu.com/community/DrivesAndPartitions"). It talks about renaming partitions. 

For more information on FSTAB, see [this]("http://en.wikipedia.org/wiki/Fstab").

> 
also if I add a custom entry into fstab and say I disconnect the external drive will I have a problem booting into my system?

No. Your system will boot normally (only that the partion will not be mounted).

---

### Post by Mular on 2007-12-17
awesome thanks, 

Also sometimes I get on my desktop the same mounted drive icon twice.. They are both linked to the same place.. If I unmount it, only one disapears and the other one gives me a message if I try to open it from the desktop..

Whats causing that?

---

