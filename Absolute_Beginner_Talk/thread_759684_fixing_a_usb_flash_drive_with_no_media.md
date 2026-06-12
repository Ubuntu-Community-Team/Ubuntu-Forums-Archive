---
title: "fixing a usb flash drive with no media"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by drcarlos024 on 2008-04-19
i had my flashdrive plugged into a computer but i didnt think it read it so i unplugged it.  Next thing i know is that it DID could read it and i had accidentally unplugged it while running.  Ever since then, the flash drive's been unreadable! I tried it on ubuntu and it says that there probably isnt any media on it.  Is there any way to fix this? Maybe install new media on it?

---

### Post by drascus on 2008-04-20
yup this disk does not have a file system on it or the file system has become corrupted. you will loose all your data but there is a way to fix it. First open a terminal. Applications->accessories->Terminal. Type this command 
> fdisk -l
there should be some lines that appear. 
here is what I get
> Disk /dev/sdb: 1031 MB, 1031274496 bytes
32 heads, 62 sectors/track, 1015 cylinders
Units = cylinders of 1984 * 512 = 1015808 bytes
Disk identifier: 0x00000000

see where it says Disk /dev/sdb? dev/sdb is where the disk is located that is important so you might want to jot it down. 
now type this 
> sudo mkfs.vfat "/dev/sdb"(replace what's in quotes with what you jotted down from fdisk command but don't include quotes or you will get an error) 
enter your password. It will then say this is an entire device not just a partition continue anyway? type y hit enter. What this will do is format the device to the vfat file system which is usable on both linux and windows. after it is done close the window. then unplug the drive and plug it back in. It should now work. 

good luck

---

### Post by Don1500 on 2008-04-30
I just want to mark this page for later.

---

### Post by persianprez on 2008-05-01
just reformat it without the fancy mumbo jumbo:KS

---

### Post by Don1500 on 2008-05-05
> **persianprez said:**
> just reformat it without the fancy mumbo jumbo:KS

A plain vanilla format doesn't always work.
But I did get it to work with this answer. And I went to the manufacturer of my drive (PQI) and they had a download that will do it automatically from Windows. This download MIGHT work for other brands, but I haven't tried it.

Here is a link to the FAQ's that direct you to the download:
[http://www.pqi.com.tw/faq.asp](http://www.pqi.com.tw/faq.asp)

(Use the answer to FAQ #1 or #2: "My USB Flash Drive does not work, it says, there is no disk in the drive, please insert disk to drive "X".")

---

### Post by rectec794613 on 2008-07-17
When I type in sudo mkfs.vfat /dev/sdb it says> mkfs.vfat 2.11 (12 Mar 2005)
mkfs.vfat: Will not try to make filesystem on full-disk device '/dev/sdb' (use -I if wanted)

What do I do?:confused:

---

