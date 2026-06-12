---
title: "Problem changing permission of my Windows NTFS partition"
date: 2006-03-13
forum: Absolute Beginner Talk
---

### Post by big_croc on 2006-03-13
Hello,

I recently installed Ubuntu (with Win XP HOME already as my first OS)...basically a dual boot.
Now, I want to be able to access my music files and etc. which is in my NTFS windows partition.
My Win XP NTFS Partition (/dev/sda1) is mounted on /media/sda1/

Now, as a user I cant get permission to read the partition and I cant even change it when Im logged in as root.
I logged in as root and opened nautilus and tried to change permissions from there but it says "Permission cannot be changed because it is a read-only disk"

Any other suggestions?
Thank you

---

### Post by kaamos on 2006-03-13
Hello!

Try this -> [http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

Also note that ntfs is (safely) read-only from linux.

---

### Post by animesh on 2006-03-13
i do not the reason behind not able to read....but you cannot write on NTFS partition and should not try to. Best is to convert that partition to FAT 32 on which you can read as well as write

---

### Post by big_croc on 2006-03-13
yeah I dont care much for writing on that partition
Playing music from that partition would be only "reading" though right?

---

