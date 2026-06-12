---
title: "check disk &amp; defragment function for Ubuntu"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by wpshooter on 2006-06-09
Are there utilities in Ubuntu that are comparable to the Windows chkdsk and defragment functions or are these NOT needed in Ubuntu/linux ?

I ask about this once before and someone gave me some type of file system check command and when I tried to run it, it said that running it might destroy the integrity of the information on the drive.

Thanks.

---

### Post by gabruo on 2006-06-09
Ubuntu actually will automatically run a chkdisk like function after 60 boots(not positive on the number).  Linux does not need defragmentation.

---

### Post by wpshooter on 2006-06-09
Thanks for the reply.

---

### Post by Luke771 on 2006-06-09
You can defragment the file system if you use ext2: you need to install "defrag" from the repositories and then (I guess) run "defrag <drivename> in terminal (never done that, I'm just guessing) 
An article I found some time ago on the internet said that defrag is not as important in Linux as in Windows because Linux checks how big the space is before it starts writing, so it'll look for a free space that's big enough for the whole file, resulting in less fragmentation.
Chckdisk-equivalent... I never needed anything like that under any Linux distro. There is probably some terminal command that does that but I never needed to use  it.

The Ubuntu automatic chkdisk function runs every 30 reboots under Breeezy, not sure about Dapper.

---

### Post by grsing on 2006-06-09
It's still every 30.

---

### Post by bruce89 on 2006-06-09
Defragmentation is not required, in fact it will break the disk.  You could do a ```
e2fsck /dev/(hard disk here)
``` command, but this won't work if the disk is mounted.

---

### Post by wislon on 2006-07-08
> **bruce89 said:**
> Defragmentation is not required, in fact it will break the disk.  You could do a ```
e2fsck /dev/(hard disk here)
``` command, but this won't work if the disk is mounted.

Yeah, if the disk was mounted, you'd actually need to do unmount it first and then fsck it 

```

sudo umount /dev/(hard disk here)
(sudo) e2fsck /dev/(hard disk here)

```

---

