---
title: "File server file system?"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by martymart on 2006-07-20
What is the best file system to use for my file server if I want both linux and windows machines to access it? I was thinking about using NTFS with the new NTFS driver that is out this may be the best bet as windows can not read ext2 only NTFS and FAT32. What do you think? If I use NTFS do I have to use Samba as a file server or can I use NFS? One more quick question for you all, can windows use a cups print server or again do I have to use Samba?

Thanks,

Martin

---

### Post by geco on 2006-07-20
In most cases you can install windows on a NTFS (more stable for big partitions) and Linux on ext3 (journaled file system, no need to defrag, easy to recover) and create a FAT32 partition to exchage files...
Linux can read NTFS but is limited in writing on it.
for more informations: [http://www.linux-ntfs.org/](http://www.linux-ntfs.org/)

---

### Post by Landoln on 2006-07-20
If you are setting up a seperate machine to be a file server, the file system that you use doesn't really have any effect on what kind of other machines can access it.  If you want windows machines to be able to access it, samba works really well.  I just recently set up an ubuntu file server with a 30GB main drive and a 320GB drive both formatted ReiserFS.  After installing samba, my windows machines have had no trouble accessing it. I don't even bother with nfs anymore, as I can set up my linux installs to access the samba shares pretty easily.  

If your using Linux as the operating system for your file server (which I recommend doing an ubuntu server install for), then use a native linux file system with journaling like ext3 or Reiserfs, not NTFS.   NTFS and linux have never been good friends.

---

### Post by mcduck on 2006-07-20
There is also Ext2/Ext3 driver for windows. Works fine with my storage partition, formatted in Ext3 and accessible from both Ubuntu and Windows. :)

---

### Post by az on 2006-07-20
> **martymart said:**
> What is the best file system to use for my file server if I want both linux and windows machines to access it? 

Only the file server has to access it.  The client which wants to read the files does ot access the filesystem, only the file-sharing server (samba, nfs, or whatever.)

---

### Post by Landoln on 2006-07-20
> **mcduck said:**
> There is also Ext2/Ext3 driver for windows.
Where can I get this magical driver?

---

