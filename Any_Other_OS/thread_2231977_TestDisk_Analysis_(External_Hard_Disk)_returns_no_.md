---
title: "TestDisk Analysis (External Hard Disk) returns no partition"
date: 2014-06-29
forum: Any Other OS
---

### Post by steve_dyson on 2014-06-29
After doing deep search on external USB HD i am getting this;



[ATTACH=CONFIG]254325[/ATTACH]



What should i do next?

I have attached disk management screen shot and disk F is coming up as RAW. It is coiming up as 100% free but its 250GB HD, and 18GB has been used.
--------------------------------
OS: windows 8.1 64 bit
HD: external size 250 GB

---

### Post by tgalati4 on 2014-06-29
So now you have to use *photorec* (which is part of *testdisk*).

```
man photorec
```

This will scan the entire drive and attempt to recover individual files with random/useless filenames and put them in random/useless directories--500 files per directory.

Good luck.

---

### Post by steve_dyson on 2014-06-29
thanks for your reply. photorec is running now.

---

### Post by oldfred on 2014-06-29
You have not used 18GB. Hard drive sizes in GB and GiB are most of the difference.
 It looks like you may have one partition, but it is not showing any format.
If in Windows as RAW it is unformatted or not seen correctly as NTFS.

       MB vs MiB
[http://en.wikipedia.org/wiki/Binary_prefix](http://en.wikipedia.org/wiki/Binary_prefix)
[http://www.osforge.com/news/001337.html](http://www.osforge.com/news/001337.html)
Then when you format it, the ext4 is journalized so it reserves space for the journal. This improves performance and allows error correction for the cost of a small amount of space. Also reserves 5% space for superuser.
[http://blog.flexion.org/index.php/2010/01/07/recovering-reserved-space-ext4/](http://blog.flexion.org/index.php/2010/01/07/recovering-reserved-space-ext4/)
1 Gigabyte (GB) = 1,000,000,000 bytes.
1 Gibibyte (GiB) = 1024x1024x1024 = 1,073,741,824 bytes
160 GB (gigabytes) = 149.01 GiB (gibibytes)

sudo parted -s /dev/sda unit GB print
sudo parted -s /dev/sda unit GiB print

Did you have data on the drive?

---

### Post by steve_dyson on 2014-06-29
yes, i do have data on drive around 12GB to 15GB.

---

### Post by steve_dyson on 2014-07-07
UFS Explorer is showing all my files but i will have to pay for license to recover all files.

I have run chkdsk and its recovering orphand files from last 30 hours as shown in attached image.

What should i do?

---

### Post by tgalati4 on 2014-07-07
Those files look like icons or windows graphics for a program.  Probably not very useful.

Didn't *photorec* find all of your important files?

Orphaned files are probably pieces of files near the physical damage on the platters.  They could also be deleted files, which you don't need to recover, since this was not an accidental erasure incident.  Or was it?

---

### Post by steve_dyson on 2014-07-08
I normally take USB out of port without ejecting it properly. Now i have learnt the lesson.

---

### Post by tgalati4 on 2014-07-08
It helps to put a piece of tape on it with a marking:  "Please Unmount this before Removal!"

If moving large blocks of files, you also need to wait for all of the writing to get finished before pulling the plug.  It can take longer than you think.

---

