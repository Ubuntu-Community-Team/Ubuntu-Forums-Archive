---
title: "How To Take Control of an NTFS Partition"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by rzlorayes on 2007-05-11
Hello and Good Morning (or Evening as the case may be)! 

I´m a newbie to Linux and I recently installed Ubuntu 7.04 as a dual boot with Windows XP. I have a separate, dedicated NTFS partition for my files. 

I can´t seem to save or transfer files to this  partition when I using Ubuntu as I get a message saying I don´t have permissions to write to this drive/partition. What do I do?

Thanks  very much!:)

---

### Post by Bachstelze on 2007-05-11
You definitely shouldn't use NTFS as a data storage partition since Linux cannot safely write to it.

---

### Post by Terl on 2007-05-11
Have you installed ntfs3g?  If not it is available through synaptic.  Also get the ntfs3g configuration tool.  It makes it easy.  When you run the tool you get to name the partitions and make them read/write.

---

### Post by Jazztux on 2007-05-11
Hi,
you can try to get root privileges, accessing partition with superuser privileges. ;)

---

### Post by aysiu on 2007-05-11
This tutorial (with screenshots) will help you out:
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

---

### Post by Ek0nomik on 2007-05-11
This will get you started:

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)
[https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite](https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite)

However, if you don't need files > 4GB, than I would suggest converting it to FAT32 until the Linux support for NTFS increases.

This program will take care of everything for you in a very small amount of time.  I use NTFS-3G and I haven't experienced any problems yet.

Here is a thread where someone else made use of the links I just gave you:  [http://ubuntuforums.org/showthread.php?t=439046](http://ubuntuforums.org/showthread.php?t=439046)

---

### Post by rzlorayes on 2007-05-11
Thank you Terl. I´ll certainly try that. I´ll Google it and see where I can download it.

---

### Post by aeiah on 2007-05-11
by default, NTFS is not writable. what most people used to do and a lot still do, is to create a FAT32 partition and keep files on there, since this can be read and written to in both windows and linux. recently, the ntfx-3g drivers have reached a stage where they are (in theory) reliable enough to make writing to NTFS possible. its in synaptic, as has been mentioned.

---

### Post by rzlorayes on 2007-05-11
Thanks to everyone! You are all great!

---

### Post by aysiu on 2007-05-11
> **rzlorayes said:**
> Thank you Terl. I´ll certainly try that. I´ll Google it and see where I can download it.
Or just follow the tutorial I linked to--save yourself some Googling!

---

### Post by Terl on 2007-05-11
> **rzlorayes said:**
> Thank you Terl. I´ll certainly try that. I´ll Google it and see where I can download it.

No problem.  The other advice was also good in that NTFS is not the best choice if you want to read/write.  I use ntfs3g and swap files back and forth but if I need to write I have a fat32 set up also as it is more reliable.  

You can also get a program that will let windows read an ext3 file.  I forget what it is called though.

---

### Post by Bachstelze on 2007-05-11
> **Terl said:**
> You can also get a program that will let windows read an ext3 file.  I forget what it is called though.

[http://www.fs-driver.org](http://www.fs-driver.org)

Definitely the best... well, the least bad, way to go IMO.

---

