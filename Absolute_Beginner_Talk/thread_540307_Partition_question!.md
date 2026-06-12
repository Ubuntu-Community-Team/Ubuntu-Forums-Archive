---
title: "Partition question!"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by fantasyspirit91 on 2007-09-01
Okay, I recently installed Ubuntu on a seperate harddrive with 250 gigs without any partitions. But now, my HDD that has Windows installed has only 9 gigabytes left of space. So I want to create a partition on my seperate harddrive so I can save stuff in Windows. Is this possible?

Also, the harddrive with Linux cannot be seen in Linux, it's not visible. Would it become visible again if I create that partition? 

I don't know if this makes any sense, so if it doesn't, I'll try to explain my problem again. Thanks a lot.

---

### Post by wolfen69 on 2007-09-01
"Also, the harddrive with Linux cannot be seen in Linux, it's not visible. Would it become visible again if I create that partition?"   

this does not make sense. please explain again.

---

### Post by fantasyspirit91 on 2007-09-01
When I click My Computer on Windows, the hard drive that has Ubuntu installed does not show, only the hard drive that has Windows installed shows up. 

If I created a partition on the Linux Hard drive, would that empty space show up in Windows?

---

### Post by laidback on 2007-09-01
Use Gparted, System>Preferences>Gnome Partition Editor, which is in fact Gparted. You cannot alter a partition that's mounted in Linux so you'll need to Unmount (umount in command line) the partition before changing it. There is an option in Gparted that'll do this for you or simply from the desktop, right click the drive icon, select unmount. Don't understand the second question, sorry.

---

### Post by trucker33377 on 2007-09-01
when i set up my 2nd HD windows didnt see it until i put a windows partition on it . when i reopened windows it was there and i formatted it from windows should work out

---

### Post by shearn89 on 2007-09-01
Windows cannot read ext3 partitions without installing extras. Linux cannot read NTFS partitions without installing extras. Both of these two formats are the default for whichever OS can read them (windows = ntfs, linux = ext3).
Therfore, to be able to read stuff from windows off the 250gb HD, you'll have to **use the livecd** to edit the linux partition. You can do it other ways, but it is easiest to use the livecd. Just don't start the install process!

---

### Post by fantasyspirit91 on 2007-09-01
I tried using the LiveCD, but it kept giving me problems, such as uncorrected errors and no "root" or something.

What I want to do with the empty partition is be able to store stuff using Windows because my Windows harddrive only has 9 gigs left. So I want to have about 30 gigs for Linux and the remainder for Windows. I'm just making it clear. 

Is there some sort of tutorial that can help me? Thanks again.

---

### Post by Majorix on 2007-09-01
See [this]("http://www.fs-driver.org/") driver under Windows to be able to see your Linux partition.

---

### Post by fantasyspirit91 on 2007-09-01
Cool, that driver lets me write onto my Linux drive in Windows. That was exactly what I wanted to do.

Thanks for all of your help guys. I appreciate it. =]

---

