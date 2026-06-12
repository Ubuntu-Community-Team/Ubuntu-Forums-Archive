---
title: "[SOLVED] NFTS Disk"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by sunseeker888 on 2008-03-16
HI Folks

I have a 2.5 inch hard drive NTFS format. Ubuntu has mounted it, and I have transferred all my files. I have used ntfs configuration tool to try to make it read/ write. Password is prompted, but no partitions is detected, it goes directly to option NTFS write external / internal drive, which I selected external. In my desktop sdb5 is mounted, properties access files only. I have done sudo bash diskmounter too, still no windows or mac drives detected. Anyone has an idea how to force a write options, it is clearly mounted as I can extract all the files.

Cheers

Irwin:confused:

---

### Post by Nikhil Gohil on 2008-03-16
u probably need to change permissions of the drive to read and write.
```
chmod 777 harddisk path
eg.
chmod 777 /dev/sda1
```

---

### Post by sunseeker888 on 2008-03-16
Problem solved went thru the ntfs manual configuration and had to edit fstab. 


Thanks :guitar:

---

