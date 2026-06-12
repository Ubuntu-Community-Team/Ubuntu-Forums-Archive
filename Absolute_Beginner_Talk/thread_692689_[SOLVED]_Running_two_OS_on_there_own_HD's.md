---
title: "[SOLVED] Running two OS on there own HD's"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by dynamethod on 2008-02-10
Hi there, i had an unforutante incident last night and lost all my data, so ive had to reformat but this time i sort want the best of both windows and linux, so i have two maxtor IDE HD's, winxp is installed on one HD(29gig), id like to reinstall kubuntu onto the second IDE HD(40gig), can i do this and then just select the bbs bios up window to select which HD to run at boot up to access either of the OS's? or is there a simplar solution? (apart from partitioning one HD that is, i dont want to go down that road), or is my theory wrong? thanks in advance

---

### Post by dcstar on 2008-02-10
> **dynamethod said:**
> Hi there, i had an unforutante incident last night and lost all my data, so ive had to reformat but this time i sort want the best of both windows and linux, so i have two maxtor IDE HD's, winxp is installed on one HD(29gig), id like to reinstall kubuntu onto the second IDE HD(40gig), can i do this and then just select the bbs bios up window to select which HD to run at boot up to access either of the OS's? or is there a simplar solution? (apart from partitioning one HD that is, i dont want to go down that road), or is my theory wrong? thanks in advance

Just install Linux on the other disk.

---

### Post by Sugi on 2008-02-10
Yep.  That will work for you and even better.  After you get both OS installed on your machine.  Linux will setup MBR.  So, this means instead of going into your bios to set a harddrive order, the MBR will just ask you everytime you boot up the machine which OS will you like to run today.


NOTE:  Install XP on one harddrive first and then install kubuntu on the other harddrive secondly.  XP first and then Ubuntu.  It won't mess up boot recorders that way (at least thats how was for dapper and how I have been doing it for a while now.)

Sugi

---

### Post by dynamethod on 2008-02-10
excellent thank you guys v much

---

### Post by ugm6hr on 2008-02-10
> **dynamethod said:**
> excellent thank you guys v much

Just one thing though....

When installing Ubuntu - make sure you write GRUB to the MBR of the Ubuntu HD.

This is easiest achieved by making the Ubuntu HD the "master" (i.e. Windows slave) and also the primary boot device (or at least before the Widows HD) in BIOS.

That way - your Windows HD will work independently, even if you have to remove Ubuntu (and vice-versa).

---

### Post by TWO on 2008-02-10
I don't know how valid my next point is, but it might be worthwhile creating a partition which you can share between both OS. In that case, should one OS mess up, in theory that data should remain intact? (Somebody correct me if I'm wrong!!)

I have set up my HD this way in order to avoid a repeat of what happened to me last year in that WinXP suddenly broke down and after salvaging my data found that a lot of pictures and song files had been corrupted...

---

### Post by dynamethod on 2008-02-10
> **ugm6hr said:**
> Just one thing though....

When installing Ubuntu - make sure you write GRUB to the MBR of the Ubuntu HD.

This is easiest achieved by making the Ubuntu HD the "master" (i.e. Windows slave) and also the primary boot device (or at least before the Widows HD) in BIOS.

That way - your Windows HD will work independently, even if you have to remove Ubuntu (and vice-versa).


damn lol, i went ahead and installed kubuntu on the second IDE without taking your advice on board before hand, is it still possible to move GRUB to the MBR of the Kubuntu partition? or should i not worry too much?

---

### Post by dynamethod on 2008-02-10
One other thing, i have to large directorys currently sitting on the winxp HD, music mainly, is it possible to access the music directorys while using kubuntu to listen to the music? i tried but it gave me an error saying "hal-storage-fixed-mount-all-options refused uid 1000" thanks again

---

### Post by dynamethod on 2008-02-10
Ok i think this has something to do with fstab but being that the HD containing windows is ntfs, will this mount ok when im running Kubuntu and it will not hurt the win OS?

---

### Post by dynamethod on 2008-02-10
Here is the output of  sudo fdisk -l && cat /etc/fstab:

Disk /dev/sda: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00ff00ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3737    30017421    7  HPFS/NTFS

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x720a720a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4787    38451546   83  Linux
/dev/sdb2            4788        4998     1694857+   5  Extended
/dev/sdb5            4788        4998     1694826   82  Linux swap / Solaris

Disk /dev/sdc: 255 MB, 255852544 bytes
16 heads, 32 sectors/track, 976 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x0006669a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         976      249840    6  FAT16
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=5d9afdeb-ba23-45c3-b7ea-02c23da98f92 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=0ae86975-4c86-47a4-8a7a-d585b7aecd8b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by dynamethod on 2008-02-10
I have just edited my fstab so it now looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=5d9afdeb-ba23-45c3-b7ea-02c23da98f92 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=0ae86975-4c86-47a4-8a7a-d585b7aecd8b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
#/dev/sda1
/dev/sda1	/media/windows	ntfs	user,auto,exec


the bottom line being the windowsxp/HD mount

or shoudl i use the UUID from ls -l /dev/disk/by-uuid

which shows:

total 0
lrwxrwxrwx 1 root root 10 2008-02-11 10:26 0ae86975-4c86-47a4-8a7a-d585b7aecd8b                                                                                                       -> ../../sdb5
lrwxrwxrwx 1 root root 10 2008-02-10 21:26 4708-CD0D -> ../../sdc1
lrwxrwxrwx 1 root root 10 2008-02-11 10:26 5d9afdeb-ba23-45c3-b7ea-02c23da98f92                                                                                                       -> ../../sdb1
lrwxrwxrwx 1 root root 10 2008-02-11 10:26 808876B68876AA74 -> ../../sda1
xen@Z10N:/media$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2008-02-11 10:26 0ae86975-4c86-47a4-8a7a-d585b7aecd8b -> ../../sdb5
lrwxrwxrwx 1 root root 10 2008-02-10 21:26 4708-CD0D -> ../../sdc1
lrwxrwxrwx 1 root root 10 2008-02-11 10:26 5d9afdeb-ba23-45c3-b7ea-02c23da98f92 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2008-02-11 10:26 808876B68876AA74 -> ../../sda1


so therefore by using the UUID the fstab should be:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=5d9afdeb-ba23-45c3-b7ea-02c23da98f92 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=0ae86975-4c86-47a4-8a7a-d585b7aecd8b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
#/dev/sda1
UUID=808876B68876AA74	/media/windows	ntfs	user,auto,exec

or should i use the first fstab edit?

EDIT, just solved everything it all works fine, i went with the UUID entry for the fstab for the record

---

