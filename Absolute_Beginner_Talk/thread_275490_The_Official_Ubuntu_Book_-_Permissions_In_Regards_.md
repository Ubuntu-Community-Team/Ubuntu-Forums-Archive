---
title: "The Official Ubuntu Book - Permissions In Regards To External Storage Devices"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by Not the man I once was on 2006-10-11
Greetings All,

I have a question in regards to Permissions and Filesytems with an External USB Hard Disk. I have read The Official Ubuntu Book which I purchased on release and I believe there may have been an omission. I have the disk mounted and is viewable in my Computer section. The Disk is currently formatted with the NTFS Filesystem and I wish to format it to ext3. Am I correct in saying that I must unmount the Disk and format the Disk using the following command:

```
sudo mkfs.ext3 /dev/sda1
```After doing so, then must I remount the volume and modify the Permissions to allow access to the Disk itself and being able to write to the partition created using the following command:

```
cd /media
``````
ls -al
``````
sudo chmod a+w usbdisk
```The above was exactly what I'm industructed to do via The Official Ubuntu Book but on attempting to write to the Disk I found I couldn't and was only able to write to the Disk after restarting my Computer. Could I simply restart the X Window System? Should this be the case or has there been an omission with The Official Ubuntu Book?

I recommend everyone purchase this book, it's simply the most enjoyable book I've read this year, a must for every Ubuntu GNU/Linux user!

Regards,

Not the man I once was

---

### Post by Not the man I once was on 2006-10-13
Greetings All,

I'm disappointed at not being given a reply to my query but perhaps it is through fault of my own that this is the case. The situation has changed somewhat from my oringial query. I removed said Partitions from my External Hard Disk and now have a Hard Disk which is required to be Partitioned and given the Filesystem ext3.
Is it possible through the Ubuntu Live CD that I may Partition my External Hard Disk? I don't know whether this is possible given that the Live CD is used for Installation of the Operating System and my External Hard Disk isn't currently viewable come the File Browser, which is quite obviously because the Hard Disk doesn't have an Active Partition. Support with this matter is greatly appreciated.

Regards,

Not the man I once was

---

### Post by MWAAAHAAA on 2006-10-13
1. You said you have an external USB hard disk. This means that you probably should access it using the /dev/usb/* devices. The command you mentioned 'mkfs.ext3 /dev/sda1' will format the first partition on the first SCSI drive. You should probably change it to something like 'mkfs.ext3 /dev/usb/0'. Did you receive any error messages during the process? I find it strange that you were able to write to this disk after formatting, since the disk should still contain an NTFS filesystem, which is read-only for linux last time I checked.

2. If your disk is mounted with (user) write access to the /media/usbdisk folder, the commands you use to make that directory writable seem OK. You could omit the 'ls -al' as it just lists the contents of the current (/media) directory. Setting write permissions could then be as easy as 'chmod a+w /media/usbdisk'. How do you mount the disk?

3. Only used the live CD myself twice, but I think you can partition your harddisk as the necessary tools should be installed already. Tools to partition your harddisk are fdisk, cfdisk, parted, which are all CLI tools. I would recommend cfdisk. Since you are apparently new to Ubuntu, you might want something graphical and I think people talk about gparted alot. Never used it myself though.

4. Books are all nice and all and I use them a lot for all sorts of stuff, but when linux is concerned I found that the internet provides much more up to date, accurate, and complete information.

5. AFAIK linux completely ignores the "active" flag on any partition.

---

### Post by Not the man I once was on 2006-10-16
Greetings,

Thank you for your advice! I successfully formatted my External Hard Disk and can now access it. I've also given my External Hard Disk an Ubuntu Linux sticker that I recieved with my Ubuntu Linux CDs via ShipIt for posterity and to show it that I care for its well being, giving it an ext3 Filesystem will be relief to it considering the physical requirements of an NTFS Filesystem - A well deserved relief if ever there was one to bless your Storage Medium with!

:KS 

Thank you once again.

Regards,

Not the man I once was

---

