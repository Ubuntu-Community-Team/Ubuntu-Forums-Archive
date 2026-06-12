---
title: "Install complete!!!  Next Question for Ubuntu guru's."
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by soonercntry on 2006-12-11
I have now joined the Ubuntu family.  I'm pumped up about it too!

Quick question:  I have a bunch of files on my hdd that has MS XP on it which I would like to move to the hdd that I formatted for Ubuntu / Linspire use.  I am not able to see the C: and D: Drives, which have my data that I want to see.  Maybe it's that I'm not used to the file system in Ubuntu yet, but a file search isn't helping me either.  

Any assistance is greatly appreciated!  :D

---

### Post by Famicommie on 2006-12-11
Ubuntu doesn't automatically load up your ntfs partitions. You have to manually tell it to "mount" them. If you follow these instructions, it will automatically mount your windows partition from boot.

This is stolen from the system docs that come with Ubuntu:

1. Make a directory where the partition can be made available ("mounted"):

```
sudo mkdir /media/windows
```

2. Next, back up your disk configuration file and open the file in a text editor with administrative privileges:

```
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab
```

3. Append the following line to the end of the file:

```
/dev/hda1 /media/windows ntfs umask=0222 0 0
```

> Replace /dev/hda1 with the correct device name for your partition.

If your Windows partition uses the FAT32 filesystem, replace ntfs with vfat in the above command.

If you have a FAT32 filesystem, it is also safe to allow read-write access. To do this, change the value of umask to 0000.

4. Save the edited file.

5. The changes will take effect when the computer is restarted.

6. ?????

7. PROFIT!

I did this and it worked like a charm. The mounted drive will be available right on the desktop.

Also, I really recommend going through the system documentation, it's a huge help. System -> Help -> System Documentation

---

### Post by tiptip on 2006-12-11
[http://ubuntuforums.org/showthread.php?t=311560](http://ubuntuforums.org/showthread.php?t=311560)

---

### Post by quarkhirad on 2006-12-11
> **soonercntry said:**
> I have now joined the Ubuntu family.  I'm pumped up about it too!

Quick question:  I have a bunch of files on my hdd that has MS XP on it which I would like to move to the hdd that I formatted for Ubuntu / Linspire use.  I am not able to see the C: and D: Drives, which have my data that I want to see.  Maybe it's that I'm not used to the file system in Ubuntu yet, but a file search isn't helping me either.  

Any assistance is greatly appreciated!  :D

Okay no probs 

If u find it difficult or not so easy to modify fstab file. Then here is a solution. Also note that each time u reboot into linux u will have to mount them again.The only way to get rid of doing this process each time u boot into linux  is to modify the fstab file. 
just look at reply no 5 of the below thread their i have given a detail way of mounting hardisk.


[http://ubuntuforums.org/showthread.php?t=310590&goto=newpost](http://ubuntuforums.org/showthread.php?t=310590&goto=newpost)

---

### Post by soonercntry on 2006-12-11
Alright... I did as Fammicommie directed, but apparently not to perfection.

I am not showing the drives.  I was somewhat confused about "Replace /dev/hda1 with the correct device name for your partition". 

I entered the following different device names with no luck:
C: /media/windows ntfs umask=0222 0 0
D: /media/windows ntfs umask=0222 0 0

I tried this with both caps and non caps.

I also tried placing a / and \ behind the letters to see if that was the trick.  Nothing.  Am I thoroughly misinterpreting what device name it's looking for?

---

### Post by igknighted on 2006-12-11
c:/ amd d:/ have no meaning in linux, so forget them completely.  You need the Unix drive designations (/dev/hda1 and /dev/hda2 probably if you are using an IDE hard drive)

---

### Post by taurus on 2006-12-11
Paste the output of this command from a terminal here!

```
sudo fdisk -l
```

---

### Post by soonercntry on 2006-12-11
> **taurus said:**
> Paste the output of this command from a terminal here!

```
sudo fdisk -l
```

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7649    61440561    7  HPFS/NTFS
/dev/hda2            7650        9728    16699567+   f  W95 Ext'd (LBA)
/dev/hda5            7650        9728    16699536    7  HPFS/NTFS

Disk /dev/hdb: 100.2 GB, 100204167168 bytes
255 heads, 63 sectors/track, 12182 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         140     1124518+  82  Linux swap / Solaris
/dev/hdb2             141        2091    15671407+  83  Linux
/dev/hdb3            2092        4041    15663375   83  Linux
/dev/hdb4            4042       12182    65392582+  83  Linux

---

### Post by Crocodylus Pontifex on 2006-12-11
So then what you would want to type is 
```
/dev/hda1 /media/windows ntfs umask=0222 0 0
/dev/hda5 /media/windows ntfs umask=0222 0 0
```
As a side note you will probably want to make 2 different folders in your mount folder so that you can have a seperate one for each of your drives. I'm not sure if it will work if you mount 2 seperate drives to the same folder, but it might.

---

### Post by soonercntry on 2006-12-11
I replaced C: and D: with /dev/hda1 and /dev/hda2.

I can now see my files from my C and D drives.  You guys rock.  

It's NTFS, so I can't write to them, but I'm hoping to get all important doc's and pic's transferred to my home partition and then get rid of M$XP in the very near future (gotta ween my wife off of it).  Then I can format and partition the drive that my M$ crap is on and have plenty of room for Linux OS's.

---

### Post by soonercntry on 2006-12-11
Correction.... /dev/hda5  

Good catch.

---

### Post by Crocodylus Pontifex on 2006-12-11
Also, there are numerous projects all over the net for basically anything you want to do. This site has information on how to write to NTFS from Ubuntu. Most of your questions are only a google search away.

[http://ubuntuos.wordpress.com/2006/08/02/howto-write-to-windows-ntfs-drive-from-ubuntu-ntfs-3g/]("http://ubuntuos.wordpress.com/2006/08/02/howto-write-to-windows-ntfs-drive-from-ubuntu-ntfs-3g/")

---

