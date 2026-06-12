---
title: "Weird hard drive space issue"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by Kadmium on 2006-11-24
Hi, I am having a weird problem here, in Ubuntu 6.10.

I have now reached my hard drives max capacity, so I was deleting stuff.
But, it seems like it doesn't react, kind of. It says I still have 0 bytes of free space, even when I have deleted files up to 5 GB in size.

It seems like it won't "give my hard drive space back". I am running Ubuntu 6.10/Edgy Eft. I am using ntfs-3g on the drive.
Don't know if that has something do with it. Any answers would be highly appreciated, since I'm in need of the space, as soon as possible.

Please, help a newbie.

---

### Post by Dual Cortex on 2006-11-24
Answer from a newbie to another newbie:
Have you emptied the trash?
Though I don't think the even trash holds a 5GB file...

;) lol, can't help you much more.

---

### Post by Kadmium on 2006-11-24
Yes, the trash is empty.

---

### Post by drphilngood on 2006-11-24
It seems to be known bugs.  Just see [here]("http://www.ntfs-3g.org/support.html#diskspace").

edit: I´ll print the info from **NTFS-3G Support** in hopes that it may help later:

> **Why doesn't file deletion free disk space?**
    In most cases it does, except for the following scenarios:

        * In some desktop configurations files are not deleted for real but moved into a 'Trash' or '.Trash-username' directory in the root of the partition. When these directories are emptied then the disk space is reclaimed.
        * By design, Linux and Unixes free the disk space of the deleted files permanently only if no software keeps them open anymore.
        * NTFS is able to store small files and directories in fixed size (1 kB) MFT records (inodes). When such files are deleted then the MFT records are marked free for reuse or for undelete, and no space can be freed. 

    Status: Not a driver problem.

---

### Post by Kadmium on 2006-11-24
Thank you! I fixed it now, by going to /media/hdb1/.Trash-kadmium/ and deleted everything in there!

Finally!

---

