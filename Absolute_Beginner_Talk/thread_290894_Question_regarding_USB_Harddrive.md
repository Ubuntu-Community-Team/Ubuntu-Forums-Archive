---
title: "Question regarding USB Harddrive"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by vince vega on 2006-11-01
I've recently switched to Linux after many years using windows. I have a large music collection that i store on a USB 2.0 hard drive. I was pleasantly surprised when i plugged it in today, and it suddenly appeared on my desktop! (I expected more work to be involved).

My question to all you experts is this: Can I safely add music to the USB drive, without messing anything up ?(This music means a lot to me)- Ive read a few posts about certain windows hard disks, stating that it is okay to read from them, But writing to them can cause problems. 

If this does turn out to be an issue, what steps should I take to protect my existing mp3 collection, while continuing to add to it, running Ubuntu.

Thank You in advance for your help.

-Vince

---

### Post by ewl1217 on 2006-11-01
Do you know what file system is used on the hard drive? If it's FAT, then you can go ahead and use it how you want. If it's NTFS, you can safely read from it, but writing to it is more involved and success isn't guaranteed. If you're not sure, or if it's NTFS, then someone else will need to help you.

---

### Post by vince vega on 2006-11-01
Honestly, I'm not sure.

---

### Post by annda on 2006-11-01
if you haven't installed any special NTFS drivers and can write to it, you're on the safe side, no matter what. that would mean permissions are right, ownership is right etc. you can use the drive to your liking.

you can find out the filesystem by typing mount in the terminal and identifying your HDD.

if you have any problems, take a look at those:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

any other questions - post them here.

---

### Post by jpeddicord on 2006-11-01
It *should* work fine - I had a USB stick from Windows XP and I could write to ti without any problems (other than it being a little slow).

---

### Post by mo79 on 2006-11-01
I second that. If you can write to the drive - it's safe to test - then you probably have the FAT system and can do read/writing with nothing else needed.
If you can't write to it, it's NTFS and you'll have to perhaps look into relevant tools.

---

### Post by vince vega on 2006-11-02
Thanks for the help! 

-- 

I just bought a new 500gb Seagate hard drive, how to I set this drive up to work with Ubuntu Linux? Does it need to be set up with a particular format? If so, what commands do I need to use?

---

### Post by podunk on 2006-11-02
About your music collection - back it up - OK? No matter what OS you use how careful you are - sheet happens!

To know for sure what file system you have on a disk you can open a terminal and type
```
sudo fdisk -l
```
Please note that -l is a lower case L not an i or pipe.

Or graphically
System>Administration>Disk Manager
Click on the drive in question, then on the "Partitions" tab for full details about your hard drives.

500 gigs is a lot of space! :) Just like any other OS you'll need to format and partition it. The default file system for Ubuntu is ext3.

---

### Post by mo79 on 2006-11-02
If you only want your drive to be used with Ubuntu, format it as EXT3. If you want to share with Windows make it FAT32. You could also use GParted to make the drive half EXT3, half FAT32. But if assuming you're kissing Mr Gates goodbye, go all EXT3. ;)

---

