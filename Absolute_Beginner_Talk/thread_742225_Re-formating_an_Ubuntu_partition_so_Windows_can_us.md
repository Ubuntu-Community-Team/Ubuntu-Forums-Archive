---
title: "Re-formating an Ubuntu partition so Windows can use it..."
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by LesIsMore on 2008-04-01
Hi All-I am moving my Ubuntu install to a different machine and wondered if there was a way to have the partition it is on currently (it is on a partition of a dual boot Ubuntu and Windows machine) and re-format it so that I can use it for the Windows install.* Any help would be much appreciated.

---

### Post by TeoBigusGeekus on 2008-04-01
Boot up with live cd, open gparted and format it as NTFS. Thus, window$ will recognise the free space...

---

### Post by stchman on 2008-04-01
> **LesIsMore said:**
> Hi All-I am moving my Ubuntu install to a different machine and wondered if there was a way to have the partition it is on currently (it is on a partition of a dual boot Ubuntu and Windows machine) and re-format it so that I can use it for the Windows install.* Any help would be much appreciated.

So you want a Windows machine to be able to access and possibly modify an Ubuntu EXT3 partition?  There is a program called linux-reader.  There is no utility to my knowledge that allows a Windows machine to modify an EXT3 partition.

[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

It allows read only access to EXT3 partitions in XP or Vista.

It is not advisable to allow another OS to be able to write to a Linux system partition.

Linux has ntfs-3g but I do not allow Linux to have write privileges to the C: drive of a Windows partition.  You are asking for trouble.

If you want to have a shared partition for Linux and Windows and you don't need file sizes greater than 4GB you can use FAT32.

---

### Post by Duck2006 on 2008-04-01
> Linux has ntfs-3g but I do not allow Linux to have write privileges to the C: drive of a Windows partition

I use it all the time and it works very good.

---

### Post by Niniel on 2008-04-01
> **TeoBigusGeekus said:**
> Boot up with live cd, open gparted and format it as NTFS. Thus, window$ will recognise the free space...

Yes, you can either create a new partition this way, or, if you are feeling a bit more adventurous, you can delete all your Linux partitions (you should have at least root and swap) and then extend the Windows partition to include the free space. 
This could wreck your existing Windows installation if interrupted (say, by a power outage) or if some other error occurs, so you may want to make a backup first. 
On the other hand, I've done this - both shrinking and later expanding an NTFS partition - without any problems at all, so I think it's very safe. 

Or what you could also do is fire up Windows and use the Windows partition manager (Admin Tools/Computer Management/Storage/Disk Management) to delete the Linux partitions. Afterwards you can create a new partition/drive in the free space.

---

### Post by jken146 on 2008-04-01
Linux can read and write to NTFS partitions.  [http://fs-driver.org](http://fs-driver.org) has a Windows XP driver for ext2 (and therefore ext3) filesystems, which lets you read and write.

Linux may not be installed on a FAT or NTFS partition.

---

### Post by stchman on 2008-04-01
> **Duck2006 said:**
> I use it all the time and it works very good.

I am not saying that you cannot do it, I am saying it is inadvisable.  If you delete something important your Windows partition may not boot.

There is no reason to need write privileges to the Windows system partition.  It is a precaution I take.

---

### Post by Duck2006 on 2008-04-01
> **stchman said:**
> I am not saying that you cannot do it, I am saying it is inadvisable.  If you delete something important your Windows partition may not boot.

There is no reason to need write privileges to the Windows system partition.  It is a precaution I take.

Thats very true.

---

### Post by Niniel on 2008-04-02
> **stchman said:**
> There is no reason to need write privileges to the Windows system partition.  It is a precaution I take.

Of course there's a reason - you want/need to get to the files in the My Documents folder.

---

