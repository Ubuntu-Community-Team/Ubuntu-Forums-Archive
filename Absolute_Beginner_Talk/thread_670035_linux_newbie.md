---
title: "linux newbie"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by Ronaldp113070 on 2008-01-17
hello all! im trying to intall ubuntu 7.10...... can anyone tell me what's the ideal partition for a 40GB harddisk... thanks and more power!!!

---

### Post by alwiap on 2008-01-17
do you want another operating system on it, like windows?  or just linux on the entire drive.

---

### Post by Pandemic187 on 2008-01-17
If you aren't installing Windows, you can just direct the 7.10 installation wizard to use the whole drive by choosing "Guided - use entire disk."

To give you some idea as to what is really going on, you'll basically have two partitions for your Linux OS. If I were to partition the drive manually, I would choose one 1 GB swap partition, and make the rest allocated to an ext3 partition, which is the main file system Linux uses, parallel to Windows' NTFS. The mount point for the drive will be "/" (minus the quotation marks), representing root. Your root mount point is similar to the C:\ drive in Windows as well.

---

### Post by Trott on 2008-01-17
If you don't want another OS on your computer, use guided install. It made my life so much easier when I installed it on a PC at school.

---

### Post by MaximusTG on 2008-01-17
I take it from your post, you are going for a single-boot? Just Ubuntu. In that case you should consider creating a separate /home partition. That way, if you screw something up in your system, you can always reinstall. In the reinstallation, you would then choose to format your / partition, and mount your existing /home partition as /home. After the install,  you will still have all your personal files and settings. If this sounds to hard to do (you would have to choose manual partitioning in the installer, you can use the option 'use entire disk' in the installer. That will erase your entire drive, and install Ubuntu. You can then use this guide:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

to move it to a separate partition. I couldn't find a guide to do this during install...

---

### Post by Ronaldp113070 on 2008-01-17
ill try to partition the entire disk manually just for ubuntu linux..... what's the ideal partition.... i want a 5Gb swap and the rest for "/" and /home... how do i do that

---

### Post by ugm6hr on 2008-01-17
> **Ronaldp113070 said:**
> ill try to partition the entire disk manually just for ubuntu linux..... what's the ideal partition.... i want a 5Gb swap and the rest for "/" and /home... how do i do that

Why such a large swap?  Recommended is 1.5-2x RAM, with a maximum necessary about 700-100MB.

From the LiveCD, I yould use GParted (System-> Administration-> Partition Editor).

Just delete all partitions, and then create your ext3 / partition as hda1 (or sda1) of about 10-15GB, then ext3 /home as hda2 of about 24-29GB, and finally /swap (swap filesystem type) of about 1GB as hda3.  Then apply all changes.

Once done, double click install on desktop, and assign the partitions in "Manual"

PS: the default guided installer always assigns /swap as an extended partition - not sure why - does anyone know a logical reason for this?

EDIT: Just realised that if you use suspend to ram with loads of open apps, then you might need a slightly bigger swap (but still not 5GB though).

---

