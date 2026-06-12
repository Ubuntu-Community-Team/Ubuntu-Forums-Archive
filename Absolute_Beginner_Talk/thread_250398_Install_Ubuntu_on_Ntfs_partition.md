---
title: "Install Ubuntu on Ntfs partition"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by manojvekaria on 2006-09-04
I want to install ubuntu on a ntfs partition.

I got all three partitions ntfs. got windows on c. and some documents on D; and E:

I wana leave the windows partition alone. Want to make (D:) the documents folder for both ubuntu and Windows.

I wana also Install ubuntu on E: and make another partition so the programs of ubuntu can remain there.

Is there a way i can do this? I try to google it but i found ntfs -3g. i dono how to use it.

Please give a step by step instruction on how i will acheive all that.



I don wana delete anything in my computer.

Thanx in advance

---

### Post by meng on 2006-09-04
You can't install Ubuntu on an NTFS partition. Furthermore, Ubuntu should be installed on a partition that doesn't carry anything else; you said there were documents on your E:

I don't believe you can achieve every one of your conditions.

---

### Post by 3rr0r on 2006-09-04
I was under the impression that ubuntu would only install on a ext3 (not ntfs) partition.  If you want a partition for these 2 OS's to share, just make the 2nd partitoin fat32 that way both OS's can read/write to them.  

Sorry if this doesn't answer your question.  I was not too sure if this was what you were asking.

---

### Post by 3rr0r on 2006-09-04
HI meng!!:)

---

### Post by SkyNet2029 on 2006-09-04
Actually you can install Ubuntu on an ext2/ext3/xfs or jfs file system. Just not the NTFS file system. I can understand (barely) a desire to be consistent on file types used on a machine (again, barely), but even the old skool ext2 file system is superior to an NTFS file structure. As was previously posted, you would need to allocate an *empty* partition for Ubuntu to be installed in, of ext2, ext3, xfs, or jfs structure. Your need for a partition that both OS's can access can be accomplished by using a shared fat32 file system, although it too would be bare since it is not possible to revert/convert NTFS partitions to fat32, only fat32 to NTFS. An excellent site with far less technical and user-friendly instructions, walk-throughs, etc. is here:

[http://www.psychocats.net/ubuntu/index.php]("http://www.psychocats.net/ubuntu/index.php")

which should get you exactly where you want to be, minus of course the Ubuntu on an NTFS partition.

---

