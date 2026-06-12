---
title: "Problem Using Partition Magic"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by rookshop on 2007-07-07
Hi,
I just used the 'Install New Operating System' available in Partition Magic 8.0  to make a new partition for Ubuntu 7.04. I also created a SWAP partition at the beginning of the drive. I then installed Ubuntu on the new partition. Ubuntu works fine but when I choose Windows XP from the boot menu it gives me a BSOD. 



I found this in the help file in Partition Magic:
"Important (Windows NT 4.0 only): If NTLDR.EXE is installed or moved beyond the 64K boot code boundary, Windows NT will fail to boot. NTLDR.EXE is usually located near the beginning of the partition in which it is installed. When you create partitions using PartitionMagic, if NTLDR.EXE is not located within the 2 GB boundary, the OS will not boot. If you hide a Windows NT boot partition, you must manually edit the Windows NT boot initialization file (BOOT.INI) to point to a new Windows NT boot partition. This can be done by opening the file in a program such as Notepad and resaving it with the same file extension." 


I think it is because of the SWAP partiton at the beginning of the drive that has created the problem though I cant be sure. Is my XP installation lost.  I am a total noob at this and any help will be appreciated.

Thanks in advance....   :D

---

### Post by tchoklat on 2007-07-07
Not necessarilly, though Windows does like to reside at the start of the disk. You may try "Ulimate Boot Disk" it can be downlaoded as an ISO and restore your MBR.
 
Hope this is of help!
 
It is easier to use the partitioner that comes with the Ubuntu disk to set the partitions.

---

### Post by rookshop on 2007-07-07
UBCD has a bunch of tools. I dont know which one to use. I think I might do more damage than good. Please help...

---

### Post by tchoklat on 2007-07-07
I am not at my Linux desktop currently, but from memory burn the ISO to CD and boot into it. You need to select an option to repair the windows bootloader. That should allow you to boot into windows, then reinstall Ubuntu using GPartEd the partition manager in the Live CD.

---

### Post by tchoklat on 2007-07-07
...ALSO try Super Grub Disk it is quite easy to use. 
See [http://supergrub.forjamari.linex.org/?section=features](http://supergrub.forjamari.linex.org/?section=features)
The option you want is "Fix Boot of Windows".

---

### Post by rookshop on 2007-07-08
I did that and now windows boots fine. Is there a way to select which operating system to boot at startup?

---

