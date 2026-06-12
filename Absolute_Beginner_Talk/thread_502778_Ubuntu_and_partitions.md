---
title: "Ubuntu and partitions"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by orthiles on 2007-07-17
hi, soon I will be making the move from windows xp to linux. I'm looking forward to the new experience but I have a question I need answered first.

atm I have 2 harddrives, one which is just used for file storage. it uses NTFS filesystem (one large partition). will this be a problem when I install ubuntu on my other drive? will I instantly be able to access all the files on this drive and be able to write to the partition? if not, is there a way I can change the filesystem on this drive without losing all of the files?

thanks for your time.

---

### Post by hailtothethief on 2007-07-17
When I installed Ubuntu, I only had one hard drive, and was able to keep running my windows OS. Right from the install I was able to access the windows (NTFS) partition, and even execute file operations between my Linux and Windows partition. I don't see why this would be any different for separate drives, except for possible needing to mount your second hard drive.

---

### Post by bodhi.zazen on 2007-07-17
Post install you will have read-only access to the ntfs drive.

If you want read-write access you can install ntfs-config :

[http://doc.gwos.org/index.php/Mount_NTFS_volumes_with_write_support](http://doc.gwos.org/index.php/Mount_NTFS_volumes_with_write_support)

---

### Post by rahul.gupta on 2007-07-17
support for reading a ntfs partition is there in feisty, however, by default it is mounted as read only.. you might want to install a NTFS admin package to enable write support. (can't recall the name of the package, but you will be able to locate it in Add Remove Programs after selecting Show All Applications )

---

