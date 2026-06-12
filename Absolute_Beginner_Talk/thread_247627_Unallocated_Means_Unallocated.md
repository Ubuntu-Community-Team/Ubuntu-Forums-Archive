---
title: "Unallocated Means Unallocated?"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by Tom Husband on 2006-08-30
I'm about ready to load Ubuntu and have done some searching here on dual booting XP and Ubuntu but still have a question.  I have several partitions already and I also have about 30GB of unallocated space.  Will Ubuntu automatically use the unallocated space to install, recognize my XP install and allow dual booting at start up or do I need to create a fat32 partition for Ubuntu first?

Many thanks,

Tom

---

### Post by majesticturkey on 2006-08-30
Use ext3 for Ubuntu, first of all.

Second of all, I think the default is for Ubuntu to take the entire hard drive. There is a second option (at least under the graphical installer) for you to do it manually, and you can choose the unallocated space. I think there is a selection on the alternate install CD to use unallocated space for install, but I'm not sure, never having used it. But the installer has a partitioner and formatter with it, so you shouldn't have to worry.

---

### Post by Tom Husband on 2006-08-30
Ext3 got it.  What's the alternate install CD?

Thanks,

Tom

---

### Post by majesticturkey on 2006-09-01
When you download the Ubuntu ISOs, you have the LiveCD (that's graphical) and the alternate. You can choose either the LiveCD, the server install CD, or the alternate. It's not so graphical, but it's not hard to use. You can use the LiveCD to install Ubuntu, which is more user-friendly and point-and-click, you just have to choose to manually partition your drive. You already did that, so when you choose the "mount point" (where Ubuntu is), you just choose the partition that is unallocated. It formats that partition into ext3 and installs, no problem.

That's pretty much all I know on the subject, the wiki has a lot of info too. Good luck, you seem to know enough about computers to get through this well.

---

### Post by argie on 2006-09-01
> Will Ubuntu automatically use the unallocated space to install, recognize my XP install and allow dual booting at start up
It did for me. I think it is supposed to.

In the alternate install disc I asked Ubuntu to "partition all available free space" and it made a / and a swap partition filling the 19GB I had. I think it should be similiar. It recognized Win 98 easily.

> do I need to create a fat32 partition for Ubuntu first?
No.

---

### Post by jesus of suburbia on 2006-09-01
on my shipit i only got live cd, oh well im using ubuntu now installed on my drive

---

### Post by Tom Husband on 2006-09-01
Thanks all.  You've been a big help.

Tom

---

