---
title: "fat32 partition auto recognizing"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by ep3w on 2007-06-06
I am dual booting with XP and feisty.  I have my linux partition/swap, my xp NTFS partition and i just made a fat32 partition to store my music, pictures etc. so i can share it between operating systems. Now when i boot feisty, the partition with XP(sda1) on it automatically shows up on my desktop and i can use it.  To see the fat32 partition, i have to go to places>computer then select it, type in my password then it shows up on the desktop as disk.  How can i get it to show up on the desktop from the start like my XP partition as sda3?

---

### Post by freebird54 on 2007-06-06
Under what name does it show up on your desktop?  I expect that adding an entry to your /etc/fstab file will work, but I don't know what name to give it - so I can't yet post an example entry!  Also - it would help if you pasted the output of
```

sudo fdisk -l
```

into your reply....

OK?

---

### Post by ep3w on 2007-06-06
Here is fdisk: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1936    15550888+   7  HPFS/NTFS
/dev/sda2            7561        9729    17422492+   5  Extended
/dev/sda3            1937        7560    45174780    b  W95 FAT32
/dev/sda5            7561        9522    15759733+  83  Linux
/dev/sda6            9523        9729     1662696   82  Linux swap / Solaris

Partition table entries are not in disk order

The XP partition that automatically comes up, is called sda1.  After i go to place>computer to get the fat32 partition to show up it is just called disk.  It should be sda3 i believe.

---

### Post by Dedoimedo on 2007-06-06
Hello,

See my answer to the other question:
[http://ubuntuforums.org/showthread.php?t=465768](http://ubuntuforums.org/showthread.php?t=465768)

The only difference is that you want to use the FAT32 partition (please read the post above).

/dev/sdXY /media/partition_name vfat iocharset=utf8,umask=000 0 0

Above, this is a general example.


Specifically, you need to these things:

sudo cp /etc/fstab /etc/fstab_backup

sudo mkdir /media/win_fat32 (or any other name you fancy)

sudo gedit /etc/fstab

Add this line:

/dev/sda3 /media/win_fat32 vfat iocharset=utf8,umask=000 0 0

If you are using localized install, you might want to use a different charset, but utf8 should work well.

Reboot for changes to take effect.

I have written about this and many other issues in detail:
[http://www.dedoimedo.com/computers/linux_commands.html](http://www.dedoimedo.com/computers/linux_commands.html)

Dedoimedo

---

### Post by freebird54 on 2007-06-06
Ok - here goes...

First - decide on a name you would LIKE it to come up as... perhaps Data?  Shared?  Media?  Whatever it is, I'll call it **disk** for the rest of this (with the bold),

First go to the /media directory

```
cd /media
```

Now IF the disk already shows up, do

```
sudo umount /dev/sda3
```

otherwise continue with making a mount point (a directory name, with nothing in it) for the new item

```
sudo mkdir **disk**
```

now return to your home dir

```
cd
```

and create a backup of your mountable drive config file:

```
sudo cp /etc/fstab /etc/fstab.backup_070606
```

and edit it:

```
gksudo gedit /etc/fstab
```

and add in a line like this:

```
/dev/sda3  /media/**disk**    vfat    iocharset=utf8,umask=000  0    0
```

save, exit and enter

```
mount -a
```

and **disk** should appear on your desktop, and default to appearing from then on.  OK?

---

### Post by ep3w on 2007-06-06
Worked perfectly! thanks a lot! only hitch was when i rebooted, the icons were on top of eachother. But it worked great!

---

### Post by Dedoimedo on 2007-06-07
Good job.
Always nice to hear a success story.
Dedoimedo

---

