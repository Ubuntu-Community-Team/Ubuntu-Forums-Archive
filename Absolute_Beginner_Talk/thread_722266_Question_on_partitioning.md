---
title: "Question on partitioning"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by BlizzofOZ on 2008-03-12
I am trying to install server 7.10 and at the point of partitioning the drive.

I have a 750GB SATA drive.

I used the guided option and is stating:
partition #1 primary 747.1GB  ext3 type format
partition #5 logical 3.1 GB

Would this be ok? I may end up installing the GUI on the server, so I know I need at least 1GB.

Should I go the guided LVM route?

---

### Post by justleen on 2008-03-12
in this setup you are using 747GB for Ubuntu..(#1)  im guessing #5 is your swap..


That ought to MORE then enough... 

are you sure there is no other data on your disk? it will format the 747 GB!

---

### Post by BlizzofOZ on 2008-03-12
Sorry... yes, the 3.1GB is listed as swap.

This is a brand new hard drive... so, no data on it!

Just curious as if this was ok... wasn't sure about the LVM route.

Curious, why is lists partitions #1 & 5 and not make #1 & 2.  Why the jump from 1 to 5?

---

### Post by Golem XIV on 2008-03-12
> **BlizzofOZ said:**
> Sorry... yes, the 3.1GB is listed as swap.

This is a brand new hard drive... so, no data on it!

Just curious as if this was ok... wasn't sure about the LVM route.

Curious, why is lists partitions #1 & 5 and not make #1 & 2.  Why the jump from 1 to 5?

It's probably an extended partition.  You can have only 4 primary partitions on a physical drive, so the logical ones start the count from 5.

---

### Post by justleen on 2008-03-12
i was wondering about that myself :)

I think the installer just numbers them like that, and the actual devices will be /dev/sda1 and /dev/sda2

SInce this is a blank drive, i would suggest to you not to use the whole disk.. 747GB is a lot of space, and it might be wiser to choose the manual install, make a disk of 20GB, assing "/" as a mount point.
20GB is still plenty for the OS, and that way you can add some data disks later.

Or better yet, add them straight away, and create a seperate partition for /ome while your at it.

I wouldnt use LVM, if your an unexperienced user.

---

### Post by BlizzofOZ on 2008-03-12
I understand about adding the 20GB logical swap partition...

Lost me adding "data disks".  Do you mean breaking up the 730GB into primary partitions?

---

### Post by BlizzofOZ on 2008-03-12
I  think you might have meant that I can create more partitions now or later... right?

---

### Post by Oldsoldier2003 on 2008-03-12
> **BlizzofOZ said:**
> I  think you might have meant that I can create more partitions now or later... right?

its always easier to create the partitions before installing, especially if you plan on having separate partitions for /home  and  /

---

