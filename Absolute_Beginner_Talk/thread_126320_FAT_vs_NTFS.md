---
title: "FAT vs NTFS"
date: 2006-02-06
forum: Absolute Beginner Talk
---

### Post by Algorab on 2006-02-06
Hello everyone,
I'm just about to install Ubuntu  and dual boot it with windows on my computer. I would like, however, to consult the forum before proceeding: should I reformat my windows NTFS to FAT32? Will that make it easier in any way for the OSs to communicate? Will there be side effects?

Thank you for your help!

---

### Post by Leo_01 on 2006-02-06
There is no way install linux on a NTFS partition as MS owns it.
if you wanna dual boot i suggest to use ext3 file format as it is much better and it defrags itself after 30 boots...

---

### Post by Cyril on 2006-02-06
NTFS is much more advanced then FAT32.  As such I would not install windows on FAT32 however as mentioned linux will not install on NTFS.  Ext is better than NTFS but windows won't install on ext.  What I would do is partition the hard disk.  One partition NTFS of windows and the other ext for linux.  Ubuntu would be able to read your windows files but would be unable to write to the windows parition.  Likewise witht the right tools you can view the files on your ubuntu parition within windows but you will not be able to create or edit files.

---

### Post by Perfect Storm on 2006-02-06
Perhaps use some partition with FAT32 so you can move files from both OSs.

---

### Post by Algorab on 2006-02-06
Wow, thanks everyone. Just let me see that I got it all right...
One NTFS partition for Windows XP
One FAT32 
and one Ext3 for Ubuntu...

Does that seem reasonable? :D

---

### Post by Perfect Storm on 2006-02-06
Sounds correct ^^

---

### Post by Algorab on 2006-02-06
Great! Thank you! *off to install Ubuntu*

---

### Post by lha on 2006-02-06
[QUOTE=Algorab]Wow, thanks everyone. Just let me see that I got it all right...
One NTFS partition for Windows XP
One FAT32 
and one Ext3 for Ubuntu...

Does that seem reasonable? :D[/QUOTE]

To be precise, you want to create a small (a couple of hundred mbs) swap partition for Ubuntu in addition to that ext3. Other than that, sounds good.

---

### Post by joey111 on 2006-02-06
what u also could do (in case u want to omit the fat32 partition, but i wouldn't recommend) get the [www.fs-driver.org](www.fs-driver.org) and install it in windoof;
u r then able to view and modify ur linux partitions from windows and wouldn't need the fat32 partiton for data exchange or u combine both solutions;\\:D/

---

### Post by joey111 on 2006-02-06
what also could be helpful:
if u partition that way (modify if u need) from the beginning:
/boot- 100 Mb (ext2)
ext3 for all others
/        -1Gb 
/var -2Gb
/tmp- 900 Mb (more if u want to burn dvd, and your cache uses /tmp then 5 Gb or so)
/usr- (as u need->downloaded programs
/swap-double ram (about)
/home- rest (a lot of space)
well
then 
-primary partition might be Windoof Xp system (ntfs, 4 Gb)=hda1,
on an extended partition u could store the rest:
-a fat32 partition where u store the rest of windows (programs, data or make a second fat32 partition)=e.g. hda5
then 
-the  named above e.g. hda6-...

---

### Post by cotcot on 2006-02-06
Here is a link about how to arrange the fstab to get windows available on boot :
[http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

---

### Post by Algorab on 2006-02-06
Wow, So much help! Thanks everyone!

---

