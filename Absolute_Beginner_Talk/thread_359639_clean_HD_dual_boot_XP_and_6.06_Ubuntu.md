---
title: "clean HD dual boot XP and 6.06 Ubuntu"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by J11Gyro on 2007-02-12
Ok, Two clean hard drives, 1st 80 gig second 40. I plan on using 80 for XP windblows and the 40 gig for Ubuntu. Is there any special order or anything I need to do special to create Dual boot system so the system will boot up to a screen that gives family a choice on which os to use?

---

### Post by geek_Man on 2007-02-12
Nope. You should be all set. Just make sure that you install Winblows first, then Ubuntu.

---

### Post by purplearcanist on 2007-02-12
Yep, Windows always needs to be installed first or it will not work.  When Ubuntu is installed, it will automatically install GRUB on your computer, which will give you the choice of Windows or Linux at startup.

---

### Post by J11Gyro on 2007-02-12
Will I get a choice on install for which drive I want to use for Ubuntu? Reason I ask this is the last install I did with Ubuntu on win98se Box I got no menu for a choice and lost alot of my 98se install. Hence the reason for XP.

---

### Post by xxl3w on 2007-02-12
I'm also wanting to dual boot winXP and ubuntu. I already have XP installed and I have a 200gb harddrive partitioned into two partitions. I'm planning on resizing the second partition so I have enough for Unbuntu and a swap partition. There's no issues with GRUB? Will it automatically recognize and add an option to boot XP? I remember in my LILO/slackware days, it wouldn't write over the boot sector correctly and it wouldn't boot, it'd get stuck with "LI.."

---

### Post by geek_Man on 2007-02-12
Grub should do it.

---

### Post by J11Gyro on 2007-02-13
Well something is not going right, have installed XP 3 times and same for ubuntu on 2nd drive and nothing works, I am not getting drive choice on Ubuntu install for some reason.

---

### Post by Big_Croc7 on 2007-02-13
You should see a screen where you pick where to install Ubuntu; you won't be asked for the drive though, as technically you don't need to install all of Ubuntu to the same partition, or even the same physical disk.  If you pick the 'manual partition' option during the install you will be presented with a screen asking you which partitions to use (after configuring them with the partition editor GParted).  Here you will probably want to pick something like:

/                                         hdb1
/home                                 hdb2
/media/windows                   hda1

where hda refers to the first hard disk, hdb to the second and the numbers refer to the partitions. (These will be replaced with sda & sdb if you're using SATA or SCSI drives.)

---

### Post by xpod on 2007-02-13
You shouldn`t need to be re-installing your XP even if the Ubuntu install is failing somehow.
You just need to reset your MBR with either your XP cd or a bootdisk of some sort with "fdisk" on it.

Use "fixmbr" from the recovery console of an XP cd or "fdisk /mbr" with a bootdisk with fdisk.

---

### Post by J11Gyro on 2007-02-13
I am wondering if the XP hd has to be ntfs. I have it as Fat32. The other box I have Ubuntu on is running just fine. I am trying to get dual boot on this one to not only save space but give family a choice for the time being. Tried fixing the mbr with both XP cd and Fdisk but no avail.

---

### Post by J11Gyro on 2007-02-16
Don't know what I did this time different but it seems to have worked

---

### Post by J11Gyro on 2007-02-16
Heh working like a champ now, thanks for the help all and if XP continues to boot right will be good to go

---

