---
title: "Partition question"
date: 2006-05-08
forum: Absolute Beginner Talk
---

### Post by morganpatrick on 2006-05-08
Hello,

I installed ubuntu about a month ago and in doing so wrecked my windows partition, and this morning, after having shut down properly last night, i started up my computer and it just couldn't find the linux kernel. How rare is this occurence?

Anyway I installed ubuntu again, using my last partition, the windows recovery partition. Here's what I have now:

partition 1, root
partition 2, damaged, inacessible ntfs partition
partition 4, /home (was running root before the crash)
Swap partition
Partition 5, /media/sda5, windows virtual FAT

Now first I really need to be able to access that damaged ntfs partition. How can i fix it and access it from ubuntu?

2) is it possible for me to retrieve data from partition 4 even though it's been formatted? i dont know how good data recovery is with ext3.

A thousand thanks...

---

### Post by garner_nc on 2006-05-08
If it was me, and I wanted to save the data on your ntfs partition, I'd try a new hard drive first. You've had a lot of failures here to be just random happenings. Replace your current drive, install dual boot with Windows XP and Ubuntu. Run it a week or so to make sure everything works correctly. If it fails, your problem could be your hard-drive control.  If you get reliable service for a week or preferably two, only then would I re-install the old drive as a secondary slave and see if Windows can rescue your old ntfs partition.

   If your current drive has mechanical problems, the more you use it, the more likely ALL will be lost.

   Just my  2 cents.

All the Best,
Doug White

---

### Post by morganpatrick on 2006-05-09
Thanks, I took your advice and now I'm running on yet another version of ubuntu. I'm completely off the other drive.

I can see that drive from here but I can't get any information off of it. where should i go from here?

I have one partition that's ext3, that had all my new ubuntu documents before i reformatted it as the /home folder, and then never wrote to it. Is there i chance I can recover this partition?

Then there's the ex-ntfs partition with my most crucial data on it.

Also there's another partition which is fat32 and also has some of my old data on it.

So there's the mess. Should I start with Gparted or.... I just want to do this as delicately as possible so I don't screw the drive up even worse. 

Thanks in advance.

---

### Post by morganpatrick on 2006-05-10
alright, anybody listening,

so i used ddrescue to get an img file backed up. it seemed to be a success; however, this volume is part of a clipped partition, and I thought ddrescue was supposed to be able to read this. anyway, here's where i am. Keep in mind i'm a linux beginner. this is based on the instructions given here: [http://ubuntu.wordpress.com/2006/01/21/rescue-data-from-failing-partition/](http://ubuntu.wordpress.com/2006/01/21/rescue-data-from-failing-partition/)

```

registrant@Registered:~$ sudo touch /dev/loop1
Password:
registrant@Registered:~$ sudo losetup /dev/loop1 /home/registrant/bk1/drive-back up.img
ioctl: LOOP_SET_FD: Inappropriate ioctl for device
registrant@Registered:~$ $sudo modprobe loop
FATAL: Error inserting loop (/lib/modules/2.6.12-10-386/kernel/drivers/block/loo p.ko): Operation not permitted
registrant@Registered:~$ sudo -i
root@Registered:~# modprobe loop
root@Registered:~# losetup /dev/loop1 /home/registrant/bk1/drive-backup.img
root@Registered:~# mount -t ntfs /dev/loop1 /media/ntfs
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@Registered:~#

```

alright, so i ran dmesg, and i'll spare you the whole list but this seemed important:

```

[4295502.854000] loop: loaded (max 8 devices)
[4295562.024000] NTFS driver 2.1.22 [Flags: R/O MODULE].
[4295562.055000] NTFS-fs error (device loop1): read_ntfs_boot_sector(): Primary boot se ctor is invalid.
[4295562.055000] NTFS-fs error (device loop1): read_ntfs_boot_sector(): Mount option er rors=recover not used. Aborting without trying to recover.
[4295562.055000] NTFS-fs error (device loop1): ntfs_fill_super(): Not an NTFS volume.

```

So that's where I am. I have an img file of the damaged ntfs filesystem, and it won't mount. Isn't ddrescue designed to remedy this?

I should mention that i nicked almost 20 of my 110 gigs on this partition, leaving 80gigs of (presumably) salvagable data.

---

