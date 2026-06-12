---
title: "How to mount a second hard drive?"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by mpooley on 2007-03-12
I have installed ubuntu to an empty 200gig HD and now i want to put my old windows drive back in so that i can shift my data over.

I have created a new folder /media/windows where i want to mount the drive and have tried this command to mount it 
sudo mount /dev/hda2 /media/windows -t ntfs -o nls=utf,umask=0222
and got this error message
mount: special device /dev/hda2 does not exist

Now i am stumped could someone please explain what i am doing wrong?

Thanks

Mike

---

### Post by kelbizzle on 2007-03-12
run 
```
sudo fdisk -l 
```
to find out where the drive is located. 

then following these steps you should be good. 
[http://ubuntuforums.org/showthread.php?t=380682](http://ubuntuforums.org/showthread.php?t=380682)

---

### Post by Kateikyoushi on 2007-03-12
That command tries to mount the second partition of the first hard drive, seems you do not have such.
To list your partitions type this to terminal, if you post the output we can tell what do you have to change to mount it.

```
sudo fdisk -l
```

---

### Post by Strider on 2007-03-12
/dev/hda refers to your current HD.  /dev/hda2 points to a partition on /dev/hda, which probably doesn't exist.

/dev/hdb would most likely be your second hard disk.  Replace /dev/hda2 with /dev/hda1 and try to mount again.  Should work.

From a console window type the following "dmesg | grep hd".  This should return a list of accessible devices.

Some other commands to try to verify your HD was recognized by the system:

ls /proc/ide
ls /dev/hd*

Hope that works.

-Mike

---

### Post by mpooley on 2007-03-12
Thankyou all for your responses
The output from Fdisk is
Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24415   196113456   83  Linux
/dev/sda2           24416       24792     3028252+   5  Extended
/dev/sda5           24416       24792     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5656    45431788+   7  HPFS/NTFS
/dev/sdb2            5657       14946    74621925    f  W95 Ext'd (LBA)
/dev/sdb5            5657       10553    39335121    7  HPFS/NTFS
/dev/sdb6           10554       14946    35286741    7  HPFS/NTFS

---

### Post by mpooley on 2007-03-12
quick update I tried
sudo mount /dev/sdb /media/windows -t ntfs -o nls=utf,umasdb

and got

mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or other error

---

### Post by mpooley on 2007-03-12
Hey!! Thanks all! 
I followed one of the links and worked this out:) 
mike@mike-desktop:/$ sudo mkdir /media/windows_disc1
mike@mike-desktop:/$ sudo mkdir /media/windows_disc2
mike@mike-desktop:/$ sudo mkdir /media/windows_disc3

mike@mike-desktop:/$ sudo mount /dev/sdb5 /media/windows_disc2/ -t ntfs -o nls=utf8,umask=0222
mike@mike-desktop:/$ sudo mount /dev/sdb1 /media/windows_disc1/ -t ntfs -o nls=utf8,umask=0222
mike@mike-desktop:/$ sudo mount /dev/sdb6 /media/windows_disc3/ -t ntfs -o nls=utf8,umask=0222
and that works fine!:)  and i think i even understand it a bit more (even though i dont know why the HD is labelled SDB instead of Hda2?)
now all i need to do is alter my fstab and i will be ok
I know how to edit this file but should i just copy the above commands to it? including the mkdirs??

thanks again:KS 

Mike

---

### Post by Kateikyoushi on 2007-03-12
It is not exactly the same as entering the commands to the fstab. Look here. [LINK]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only")

Should look like this

```
/dev/sda5   /media/windows_disc2 ntfs  nls=utf8,umask=0222 0    0
```

---

### Post by mpooley on 2007-03-12
eek!
I edited Fstab and got errors -
I backed it up but i dont know how to restore it?

Thanks
Mike

---

### Post by Kateikyoushi on 2007-03-12
You can edit it again, or list your etc folder to see how did you rename it, or list your current fstab to show us what might be wrong.

```
ls /etc
cat /etc/fstab
```

---

### Post by mpooley on 2007-03-12
Hey! What a great response from you all. Thanks again for your help.
I really do want to dump windows forever:) 

well I fixed my fstab and its all working sweetly:) 
I wish i could say the same for my printer and fax but i'm sure i'll get there in the end.

Thanks all

Mike

---

