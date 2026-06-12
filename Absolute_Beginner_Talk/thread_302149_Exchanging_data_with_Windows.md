---
title: "Exchanging data with Windows"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by Verminox on 2006-11-18
Currently I have an NTFS partition for Win XP and the other for Kubuntu 6.06 LTS.

What is the best way (by default or by using third party applications) to exchange data between the two partitions?

I tried reaching /dev/hdc1 from Konqueror but it gave me an error, so I guess that's not the best way to do it. And Windows doesn't even know that there is more to the hard drive than my ntfs partitions, so there isn't a question of reaching the linux files anyway.

Suggestions?

---

### Post by gareththegeek on 2006-11-18
The problem is that afaik linux's ntfs drivers can only read an nfts partition, they can't write to it and windows won't have anything to do with linux's file formats.

I am using a dual boot with winxp and ubuntu and I exchange files between them via a fat32 partition because both windows and linux can read and write to fat32.

My disk is laid out like this:

+------------+-------+------------+------------+
| NTFS WINXP | FAT32 | LINUX EXT3 | LINUX SWAP |
+------------+-------+------------+------------+

So I have edited my /etc/fstab file to automatically mount the fat32 partition on boot up by adding this line:

/dev/sda2	/media/sda2	vfat	iocharset=utf8,umask=000	0	0

/dev/sda2 is my sata fat32 partition...

I dunno if this helps...

G!

---

### Post by Verminox on 2006-11-18
I have a spare 10 GB NTFS partition (Windows drive D:) which I don't use (It is completely empty right now).

If I format that to FAT32 will it serve as a data exchange point?

---

### Post by localuser on 2006-11-18
> **Verminox said:**
> If I format that to FAT32 will it serve as a data exchange point?

Both Windows and Linux can R/W to FAT32 so that should work for you.

---

### Post by davidsolar on 2006-11-18
I also use a Fat32 partition as an exchange point. It works like a charm, but there is one nagging limit of FAT32 and that is the max file size. Anyone know if that limit is physically possible to change one sunny day in the future?

---

### Post by sinpalabras on 2006-11-18
hi i have a /home partition on my system, so i keep all my data there and if i´m in windows i can read and write ext3 partition from there whit this app EXT2IFS [http://www.fs-driver.org/](http://www.fs-driver.org/) download and install (on windows) and make your home partition look like another disck (ej: E:).by

---

### Post by sinpalabras on 2006-11-18
here is the way to do it [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome). Good luck

---

### Post by Sunnz on 2006-11-18
You can get a Windows plugin that lets you read write Linux (ext2/3) partitions from Windows:

[http://www.fs-driver.org](http://www.fs-driver.org)

That would be the best way as you can go over 4GB using ext files system.

---

### Post by Verminox on 2006-11-18
Cool, thanks. I'll try fs-driver.

---

### Post by Verminox on 2006-11-20
Ok so I formatted one of my drives to FAT32 via Windows.

However, when I try to access it via Kubuntu (Konqueror) it tells me that it is not mounted. I right-click and choose "mount" and it says "Can't find /dev/hdc5 in /etc/fstab or /etc/mtab".

What do I do now?

---

### Post by stimpack on 2006-11-20
it should appear in the /media directory, as should your ntfs for that matter.

---

### Post by Verminox on 2006-11-20
Nope, cdrom is the only thing that is present in the /media directory.

In media:/ however I can see my Linux partition, my NTFS partition, my FAT32 partition and my Floppy Disk Drive. Of these only the Linux ext3 partition is moutned and accessible. I get the same error with the other 3 devices.

---

### Post by stimpack on 2006-11-20
create a directory called fat32 in /media

add:

/dev/hda6       /media/fat32    vfat    defaults,utf8,umask=007,gid=46 0  1

to /etc/fstab, hda6 will be replaced with your own partion, I have *no* idea what gid=46 is, this was done when I installed kubuntu.

Now thats my limits, beyond that, I dont think i can help :).

---

### Post by Verminox on 2006-11-20
thanks, but I found [this]("http://www.linuxforums.org/forum/suse-linux-help/44268-suse-can-i-view-files-my-winxp-drive.html") thread before your posting and I can access my FAT32 filse now. 

Now to enable mp3 support...

---

### Post by haiku99 on 2006-11-20
a crude yet effective way is to use a USB flash drive as a swap space, this is how I do it, XP and Ubuntu have no problems reading and writing to it

---

