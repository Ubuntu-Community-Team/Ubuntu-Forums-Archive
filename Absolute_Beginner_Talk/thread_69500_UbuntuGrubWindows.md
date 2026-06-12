---
title: "Ubuntu/Grub/Windows"
date: 2005-09-27
forum: Absolute Beginner Talk
---

### Post by whiterabbit on 2005-09-27
Hello everybody.

I'm trying to add a Windows option to my Grub menu and from the link provided, I can see how to do it albeit there are a couple of issues.

Under instruction 3, it assumes that /dev/hda1 is the location of my Windows partition(in this case, it's a HDD if that makes a difference) but from checking the partition table in my terminal my Windows NTFS partition is hdc1.  I don't know what to do beyond that point.  I can get the Windows option to show up in the grub menu but this is what comes up when selected......

```
root (hd0,0)
       filesystem type unknown, partition type 0xs
       save default
       makeactive

Error 12: Invalid device requested

Press any key to continue
```

Any help would be most welcome and appreciated, thanks! 

Here are the instructions I've been following.


> 1. Read General Notes

2. Read How to list partition tables?

3.
e.g. Assumed that /dev/hda1 is the location of Windows partition

4.

[quote]sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst

5. Append the following lines at the end of file

[I]title		    Microsoft Windows
root		   (hd0,0)
savedefault
makeactive
chainloader	+1[/I]

6. Save the edited file (sample)[/quote]

---

### Post by nocturn on 2005-09-27
I'm not entirely sure, but try with hd2,0

If I'm correct, the number after hd identifies the disk while the numbe after the comma points to a partition on that disk.

---

### Post by whiterabbit on 2005-09-27
Thanks for the suggestion but that doesn't seem to work either.  hd2,0 leads to a FAT partition which doesn't have an OS installed on it so it doesn't do anything.  hd1,0 on the other hand returns this....

root(hd1,0)
       Filesystem type unknown, partition type 0x7
       etc. 
       etc.

Here is what my partition list says(if it helps).....

```
Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4677    37567971   83  Linux
/dev/hdb2            4678        4865     1510110    5  Extended
/dev/hdb5            4678        4865     1510078+  82  Linux swap / Solaris

Disk /dev/hdc: 18.4 GB, 18480365568 bytes
255 heads, 63 sectors/track, 2246 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        2246    18040963+   7  HPFS/NTFS

Disk /dev/hdd: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        3754    30153973+   c  W95 FAT32 (LBA)
/dev/hdd2            3755        7476    29896965    f  W95 Ext'd (LBA)
/dev/hdd5            3755        7476    29896933+   b  W95 FAT32
```

I'm not sure what the HPFS is but that NTFS system is my D drive(Windows).

---

### Post by whiterabbit on 2005-09-27
It's all working just fine now.  A few cable modifictations and a full reinstall of XP/Ubuntu did the job. :)  Posting from Ubuntu now.  I love this OS.

Cheers for the help.

---

