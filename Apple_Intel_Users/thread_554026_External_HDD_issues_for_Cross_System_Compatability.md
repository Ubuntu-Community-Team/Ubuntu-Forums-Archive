---
title: "External HDD issues for Cross System Compatability"
date: 2007-09-18
forum: Apple Intel Users
---

### Post by hunterjhill on 2007-09-18
Hello,

I am going to be switching to OSX from Windows in a month or so, but in the meantime, I am running a laptop with Ubuntu ( I was hoping for Native HFS support).

I have a 1TB external hard drive, that current hosts all my data in HFS+, I am using Macdrive to access my information from my Windows Machine. But, I am leaving to UCSB on friday, and all I will have is a laptop, running linux.

I would like to know how I should go about reading and writing Data to my external drive. 

Should I reformat it into a more friendly cross platform file system? If so, which one? 

Or how can I go about writing to this disk without a mac on my Ubuntu Laptop?

I really like this OS, but I need to be able to write data.

Thanks  for your help.

---

### Post by cyberdork33 on 2007-09-18
> **hunterjhill said:**
> Hello,

I am going to be switching to OSX from Windows in a month or so, but in the meantime, I am running a laptop with Ubuntu ( I was hoping for Native HFS support).

I have a 1TB external hard drive, that current hosts all my data in HFS+, I am using Macdrive to access my information from my Windows Machine. But, I am leaving to UCSB on friday, and all I will have is a laptop, running linux.

I would like to know how I should go about reading and writing Data to my external drive. 

Should I reformat it into a more friendly cross platform file system? If so, which one? 

Or how can I go about writing to this disk without a mac on my Ubuntu Laptop?

I really like this OS, but I need to be able to write data.

Thanks  for your help.

FAT32 for compatibility. Read/Write for hfs+ is built into the linux kernel. You will get errors trying to mount a hfs+ volume with write privs if journaling is enabled.

---

### Post by hunterjhill on 2007-09-18
Thanks, also I seem to remember there being limits to the size of fat32 partitions?  Is there anyway to get around this? 

For some reason I thin the limit is 25gb? But I think my friend had a fat32 drive that was 130gb. 

I would like to keep my partitions as large as possible, due to the amount of video I have on them.

Thank you.

---

### Post by cyberdork33 on 2007-09-18
> **hunterjhill said:**
> Thanks, also I seem to remember there being limits to the size of fat32 partitions?  Is there anyway to get around this? 

For some reason I thin the limit is 25gb? But I think my friend had a fat32 drive that was 130gb. 

I would like to keep my partitions as large as possible, due to the amount of video I have on them.

Thank you.
You can make FAT32 as large as you like (although it seems that some partitioners do have a limit.) Keep in mind that filesize is limited though.
[http://en.wikipedia.org/wiki/File_Allocation_Table#FAT32](http://en.wikipedia.org/wiki/File_Allocation_Table#FAT32)

You might also just try using NTFS since there is much better support for it with ntfs-3g now.

---

### Post by hunterjhill on 2007-09-18
Can Mac OS read NTFS?

---

### Post by cyberdork33 on 2007-09-18
> **hunterjhill said:**
> Can Mac OS read NTFS?

I thought you were saying that you were going to use windows... There is MacFUSE, although it may be a little troublesome.

[http://www.macosxhints.com/article.php?story=20070220150856279](http://www.macosxhints.com/article.php?story=20070220150856279)

---

### Post by hunterjhill on 2007-09-18
> **cyberdork33 said:**
> I thought you were saying that you were going to use windows... There is MacFUSE, although it may be a little troublesome.

[http://www.macosxhints.com/article.php?story=20070220150856279](http://www.macosxhints.com/article.php?story=20070220150856279)

I'm sorry for the confusion, I was using windows, now I'm on a linux laptop, awaiting the next Mac OS build so I can buy an iMac.

Being able to transverse between the 3 OS's will be very helpfull. As I type, I am prepping my hard drive for format.

Whatever File system is easiest to use on all three systems is what I am looking for.

---

### Post by cyberdork33 on 2007-09-18
> **hunterjhill said:**
> I'm sorry for the confusion, I was using windows, now I'm on a linux laptop, awaiting the next Mac OS build so I can buy an iMac.

Being able to transverse between the 3 OS's will be very helpfull. As I type, I am prepping my hard drive for format.

Whatever File system is easiest to use on all three systems is what I am looking for.
easiest is fat32 since it is supported by all filesystems out of the box... but with the noted limitations.

---

