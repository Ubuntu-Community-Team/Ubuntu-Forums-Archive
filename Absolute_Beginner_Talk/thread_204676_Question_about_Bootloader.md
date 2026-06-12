---
title: "Question about Bootloader"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by zxcvbnm on 2006-06-27
Hi, I recentley had to reinstall windows..(Don't you hate it)....And I am now missing my bootloader.......So I was wondering if I put Ubuntu's install disk in and skipped to the part of the bootloader would i be able to install just the bootloader.

Thanks

---

### Post by Dr. Nick on 2006-06-27
look here

[https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?highlight=%28reinstall%29%7C%28grub%29]("https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?highlight=%28reinstall%29%7C%28grub%29")

Ive never tried that method before, but I know its possible to restore grub without going back through the install


oops just reread your post, you have a install cd, not live apparently. Its still possible Ill pst how in a sec

EDIT

Here is the mother of all grub restore wiki pages
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by taurus on 2006-06-27
For Dapper Drake, the install CD is also a LiveCD...  Otherwise, you can also use the alternate CD to see if you can install GRUB again.

---

### Post by John Jason Jordan on 2006-06-27
Help! Can't boot! Spent the past six hours and no go!

The problem: I had Dapper-64 installed in an unused portion of the hard disk as a test platform (hda3). Breezy was still installed onn hda2. Hda1 is swap. I was satisfied with Dapper-64, so I decided to do apt-get dist upgrade from Breezy. Bad idea. Hopelessly borked. So, from the new test Dapper-64, I reformatted hda2 and installed Dapper-64 on it fresh. Except I have been wanting to try Reiserfs, so I formatted it Reiserfs before installing Dapper-64 on it. All was well for a while, but while trying something I managed to get it very badly screwed up -- so badly that I decided to start over. And I was not happy with Reiserfs, so I booted to the test version of Dapper-64 and used it to reformat hda2 as ext3. And then, rather than install Dapper on it, I used a rescue CD to copy all the files from the test setup to hda2. I did this because the test setup was already configured exactly the way I wanted it -- a couple days spent tweaking it. 

So then I went to reboot and I get a grub "error 17." Googling I quickly discovered that this means "the partition is there, but the file system is not recognized." I'm pretty sure I know what happened. Grub is expecting to see Reiserfs there instead of ext3. As long as it remains ext3 I'm going to get "error 17." 

I've read [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
and I spent about two hours trying everything there, but nothing works.

How do I fix this?

---

### Post by zxcvbnm on 2006-06-28
A n00b question......What dev/hda is the MBR on? Is there away i can find out?

---

### Post by Dr. Nick on 2006-06-28
What method are you trying to use for recovery, The mbr is the very front of the drive. 

If you are looking for the X for grub-install /dev/hdaX  it will vary depending on your partition scheme

> 
To GRUB, numbers begin with 0, and letters are expressed numerically, also beginning with 0. 
 For example, /dev/hda1 is "hd0,0" to GRUB. Similarly, /dev/hdb3 is "hd1,2". 


So if you have a windows partion at the front of the drive it will be /dev/hda1 or hd(0,0) and if you have your ubuntu right after it, it would be /dev/hda2 or hd(0,1) etc...

Hope that helps some

---

