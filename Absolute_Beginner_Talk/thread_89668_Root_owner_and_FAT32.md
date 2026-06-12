---
title: "Root owner and FAT32"
date: 2005-11-13
forum: Absolute Beginner Talk
---

### Post by topic58 on 2005-11-13
Hi, I got a problem. Have just made my partitions into FAT32 from NTFS. But now everything is owned by root. I tried "sudo chmod 777" om some documents. Now I am able to save, change and empty those documents. But still sudo is the owner of everything. I have also tried "sudo chown -R document". But that can 't be done for some reason. Not even a friend (very good on terminal) can help out. But he told me that there is a difference between FAT32 och ext3. Not all comands work in vfat. Someone out there who can help me out. I want to change owner on my entire partition, for example hdd5.
I also got an other problem with my USB2-hardrive Lacie: when I still had NTFS I copied everything to that disc, no problem. But then trying to copy everything back to my new FAT32 (made in GParted) I got I/O-error. Nothing to be done at all. So I had to use an old disc with windows XP. No problem with copy everythiong to my new partitions from XP. Any ideas here someone? :(

---

### Post by topic58 on 2005-11-13
When mounting one of my vfat partitions I write like this in terminal:
"sudo mount /dev/hdd5 /media/hdd5/ -t vfat -o iocharset=utf8,umask=000"  I have also tried changing umask to both =222 and =0222. The lock on the file disapear but I still can't write in the file. Root is still the superior owner...
I don't want to automount my vfat. Just mount it in terminal when I want to use it.

---

