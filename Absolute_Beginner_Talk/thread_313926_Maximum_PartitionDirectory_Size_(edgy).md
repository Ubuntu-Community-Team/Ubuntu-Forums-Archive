---
title: "Maximum Partition/Directory Size (edgy)?"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by klayn on 2006-12-06
Hi all,

I have an 250 gig external HD, and I use it to keep mostly music and movies. I'm currently using about 100 gigs on it now, and I recently encountered an error where edgy was telling me that I couldn't copy any more to it because it was full. I'm just curious: do any of you know if there's a maximum partition or directory size for ubuntu? Or what else might be causing this error? 

I went around it by dividing the disk into 4 partitions, and each of them seem to work fine now, even though I still would like to know why I was receiving that error...

Thanks in advance...

---

### Post by ingo on 2006-12-08
Which file system are you using? A quick fs followed by a double tab comes up with the following file system tools:

ingo@dicker:~$ fs
fsck           fsck.ext2      fsck.minix     fsck.nfs       fsck.vfat      fsview
fsck.cramfs    fsck.ext3      fsck.msdos     fsck.reiserfs  fstobdf
ingo@dicker:~$ fs

Use the appropriate one to check your external hd.

---

### Post by po0f on 2006-12-08
klayn,

Ubuntu (or Linux) doesn't have a maximum partition size, it's dependent on the filesystem used.

ext3 has an upper limit of 16TB for maximum filesystem size (with custom patches).  I think Ubuntu uses the default 2TB limit.

"Running out of space" could mean "running out of inodes", which means it can't create any more files.  There's plenty of space left, the filesystem just can't index them properly.

---

### Post by klayn on 2006-12-08
It was formatted fat32 by default, and since I want to access it on other computers as well as my own, I left it formatted this way. There weren't too many files on it, but I did have movies (approx 1 gig each), and it gave me an error message of "disk full" after about 80 gigs were filled. 

I divided it into 4 partitions now, leaving the first one fat32 and making the other 3 ext3, and now I'm not having any problems. Just out of curiosity, is there anything else that can cause this error?

---

### Post by ingo on 2006-12-08
The following is straight off Microsoft ([http://support.microsoft.com/kb/314463):](http://support.microsoft.com/kb/314463):)

> You cannot format a volume larger than 32 gigabytes (GB) in size using the FAT32 file system during the Windows XP installation process. Windows XP can mount and support FAT32 volumes larger than 32 GB (subject to the other limits), but you cannot create a FAT32 volume larger than 32 GB by using the Format tool during Setup. If you need to format a volume that is larger than 32 GB, use the NTFS file system to format it. Another option is to start from a Microsoft Windows 98 or Microsoft Windows Millennium Edition (Me) Startup disk and use the Format tool included on the disk.

Translated it says: FAT32 stinks to high heaven, don't touch it. Actually, I'm surprised your 250GB drive didn't start spluttering as soon as you hooked it up!

Seriously, ext3 or for 1GB files reiser might be the way forward. The former can even be read by windowze if you put this little tool on your external: [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html) 

All you have to do then is put it on XP and you're off (or so I'm told)

HTH

---

### Post by klayn on 2006-12-09
Thanks!

---

### Post by ingo on 2006-12-09
let us know whether it works :)

---

