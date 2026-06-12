---
title: "gparted"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by robalcorn on 2008-03-15
I tried using gparted and deleted a second drive and created "new" should it be set as a primary or extended and what is the difference between ext2 and ext3? I tried both and can't write to it or get it to auto mount. I also seemed to have lost the ability to see the 3rd drive containing xp in linux but grub still see's and allows me to boot into it.

---

### Post by NightwishFan on 2008-03-15
I can explain the difference between ext2 and ext3. Three uses a journal to help prevent data corruption. I use two because it writes less. I advise you use ext3

type this into a terminal and post the result
```
sudo fdisk -l
```

---

### Post by robalcorn on 2008-03-15
Here's the output

alcorn@alcorn-desktop:~$ sudo fdisk -l

Disk /dev/hdc: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1bdf1bde

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        3648    29302528+   7  HPFS/NTFS

Disk /dev/hdd: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x76b9ce87

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       14946   120053713+  83  Linux

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6c27897d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30024   241167748+  83  Linux
/dev/sda2           30025       30401     3028252+   5  Extended
/dev/sda5           30025       30401     3028221   82  Linux swap / Solaris
alcorn@alcorn-desktop:~$

---

### Post by Diabolis on 2008-03-15
In orde to mount partitions, ubuntu uses UUID numbers. I don't really know what does that mean, but they are like id numbers for each partition. Since you made changes to your partitions and created a new one, the UUIDs changed and the old ones are no longer recognized. You can check which is the actual information with this command:
```
blkid
```

Then you just have to update the info in your fstab file by opening it with this command:
```
sudo gedit /etc/fstab
```

---

### Post by robalcorn on 2008-03-16
Well not sure what i am doing here but here is the output from blkid:

alcorn@alcorn-desktop:~$ blkid
/dev/hdc1: UUID="AA38930C3892D723" TYPE="ntfs" 
/dev/hdd1: UUID="c14578df-8c6f-4237-b0d8-e9732549f605" TYPE="ext2" 
/dev/sda1: UUID="b863d12b-b8ab-498b-b633-3bdc15b5fc5a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="24b59561-82a5-4027-a5ed-265c7fe8711e" 
alcorn@alcorn-desktop:~$

and here is what fstab looks like:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b863d12b-b8ab-498b-b633-3bdc15b5fc5a /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc1
UUID=AA38930C3892D723 /media/hdc1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hdd1
UUID=c14578df-8c6f-4237-b0d8-e9732549f605/ ext2
# /dev/sda5
UUID=24b59561-82a5-4027-a5ed-265c7fe8711e none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
none /proc/bus/usb usbfs devgid=120,devmode=664 0 0

what I also cant figure out is if i formatted as ext3 why does it show as ext 2? also cant figure out how to get it to auto mount and give me write privilages.

---

### Post by Diabolis on 2008-03-16
I think that you need this line:
```
# /dev/hdd1
UUID=c14578df-8c6f-4237-b0d8-e9732549f605/ ext2 **defaults,errors=remount-ro 0 1**
```
you only have part of it, so add the bold text.

You should follow NightwishFan recommendation.

More info: [http://gentoo-wiki.com/HOWTO_Mount_MS_Windows_partitions_(FAT,NTFS](http://gentoo-wiki.com/HOWTO_Mount_MS_Windows_partitions_(FAT,NTFS))

---

### Post by robalcorn on 2008-03-16
Thanks I added the bold you suggested but still no go. I will read on the link you sent see if i can figure it out. I am still confused as to why it is showing as an ext2 when gparted shows it formatted as ext3?

---

### Post by Diabolis on 2008-03-16
I think that after following the link I posted you'll be able to figure it out if not let us know.

---

### Post by Diabolis on 2008-03-17
You can chage the owner of any file or partition by using the command **chown**. 

You can change the permissions of any file or partition by using the command **chmod**.

If you add the **sudo** word, it will be run as root. Every time you use sudo, commands are executed as if you were logged in as root. sudo will enable root user for about 15 minutes. if you use the word  **su**, root will be enabled for unlimited time. You won't really need to log in as root or use **su**. Since **sudo** will let you do whatever you want and then it will lock up your pc automatically after a period of time. 

You can read the manual pages by typing this:
```
man chown
man chmod
```

More about chmod and chown:
[http://www.ahinc.com/linux101/permission.htm](http://www.ahinc.com/linux101/permission.htm)

---

### Post by robalcorn on 2008-03-17
Thanks I finally get it now lmao. Guess I needed more of that coffee I keep seeing here on the forum.

---

