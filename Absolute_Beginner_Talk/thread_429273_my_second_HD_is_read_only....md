---
title: "my second HD is read only..."
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by solipsist_hero on 2007-05-01
Hi,

My second hard drive with all my music & data on it is read only. Does anyone know how I can change this?

Thanks

---

### Post by jfinkels on 2007-05-01
> **solipsist_hero said:**
> Hi,

My second hard drive with all my music & data on it is read only. Does anyone know how I can change this?

Thanks

If it is a NTFS partition, you may need the NTFS-3g driver. Search the forums for more info on the ntfs-3g driver. It will give you read-write permissions on ntfs partitions.

---

### Post by alienexplorers on 2007-05-01
I tried NTFS-3g to access and write to a NTFS partition and it got screwed up badly.  I eventually ended up reinstalling Windows with a FAT32 partition which is safer to use with Ubuntu.

---

### Post by mahiyar on 2007-05-01
My experience with ntfs-3g is not so nasty. Try this how to [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009) , however in feisty no need to add any changes to sources etc, ntfs-3g is available in repositories, just download whatever you want.

---

### Post by [ITA]ArgH on 2007-05-01
i'm a noob but i could install ntfs 3g with no much difficulty... 
Just have to run  windows twice to have it run chkdsk on my two hd and now it works great! :guitar:

---

