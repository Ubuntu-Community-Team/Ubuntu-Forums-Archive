---
title: "hard drive question."
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by rck_hitokiri on 2006-08-17
i download torrents for a hobby and i want to copy these files to my other ntfs hardrive, how do i do that? cauz i cant copy and paste files from my ubuntu to my ntfs HD. thanks

---

### Post by moma on 2006-08-17
Normally Linux can only [COLOR="Red"]read[/COLOR] from NTFS filesystems.

You have 2 options.
1) Burn your torrents on a CD and boot into Windows where you can copy the files to.

2) Install **ntfs-3g** driver which will allow [COLOR="Red"]read/write[/COLOR] on NTFS filesystems.
Study this: [http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g](http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g)
You will need ntfs-3g and FUSE (userspace filesystem module).  Ntfs-3g is OK.

---

### Post by aeiah on 2006-08-17
edit: someone beat me to the link i posted :p

---

### Post by Johan! on 2006-08-17
Install [THIS]("http://www.fs-driver.org/") driver in Windows.
It wil enable Windows to read and write to the Linux partition :)

---

### Post by catlett on 2006-08-17
The safest way is to install the ext2 driver for windows. This will allow windows to access your linux partition.
This way you can download the torrents to your linux partition. Thern boot into XP and copy the torrentsd from your linux partition to your XP partition. The ext2 driver is safe and willl not risk any of your partitions. NTFS support is reverse engineered. They do not have the source code for NTFS because it is owned by microsoft. Therefore it is still questionable if everything is accounted for. When I use the fuse module to write to windows, I always ghet an error and windows runs a check disk and it fixes quite a few things before it boots me in. 
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by givré on 2006-08-17
> **catlett said:**
>  When I use the fuse module to write to windows, I always get an error and windows runs a check disk and it fixes quite a few things before it boots me in. 

Are you using the latest version of ntfs-3g (20070811). It is true that this not a perfect driver because they work on a close source, but they made a lot of improvement, and now it's work quite well. It's not enough stable to say it's totaly safe, but report of corruption of data is quite exceptionel now.

But That's right that it's always better to recommand ext2 driver for window when it's possible, just don't devalue the hard work of some people

---

### Post by jrjr on 2006-08-17
.

---

### Post by catlett on 2006-08-17
> **givré said:**
> Are you using the latest version of ntfs-3g (20070811). It is true that this not a perfect driver because they work on a close source, but they made a lot of improvement, and now it's work quite well. It's not enough stable to say it's totaly safe, but report of corruption of data is quite exceptionel now.

But That's right that it's always better to recommand ext2 driver for window when it's possible, just don't devalue the hard work of some people

No I haven't used the lates ntfs-3g. Have you? Is it there yet? I have been waiting. I only caution because I had to go into windows once with fuse (I couldn't remove an app from wiondows and it was causing issues. I finally uised fuse and got it out) after I did the deletions when I booted into weindows it did a disk check and found multiple errors.
But I would be really happy if they finaly got it.

---

### Post by givré on 2006-08-17
Check that [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)
It's for testing purpose only but it's work quite well, and better & better every release.
I wouldn't say that they got it, but the reach a really good point. :)

---

