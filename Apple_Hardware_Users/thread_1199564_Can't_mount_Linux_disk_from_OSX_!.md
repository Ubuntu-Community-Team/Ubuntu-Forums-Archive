---
title: "Can't mount Linux disk from OSX !"
date: 2009-06-29
forum: Apple Hardware Users
---

### Post by cosmicappuccino on 2009-06-29
Hi,

I've just set up my Macbook to triple-boot with XP, OSX, and 64-bit Jaunty. I'm using rEFIt to boot into whichever OS I want, and they're all working fine. However, the problem is that when I'm in OSX, I only see 2 disks on the desktop: Macintosh HD and the Windows one.

***What happened:***
The first time I booted into OSX after confirming Ubuntu was working, I found all three disks on the desktop, with the Linux disk called "Ubuntu". However, after this, I booted into XP (for the first time after the Ubuntu install) to check that that was also ok (it seemed fine). Then, I rebooted into OSX - but now I only get two disks on the desktop in OSX, despite several reboots into the various OS's.

***What I did to try to fix it:***
[LIST=1]
[*]I opened Disk Utility in OSX and looked for the third disk. It was there in the left-hand panel, but it was called "disk0s3" which was strange. When I selected it in the left-hand panel, I got the following info:
> Mount point: Not mounted
Format: MS-DOS (FAT32)
[*]I clicked the "Mount" icon in the top section of the Disk Utility window, to try to mount the disk. I got this message in a popup window:
> **Mount failed**
The disk "disk0s3" could not be mounted.
Try running First Aid on the disk and then retry mounting.
[*]So, I closed the popup, and clicked "Verify disk" in the First Aid tab. I got this popup:
> **First aid failed**
Disk Utility stopped verifying "disk0s3" because the following error was encountered:
Filesystem verify or repair failed.
[/LIST]

I'd really appreciate any advice... I'd really like to be able to access the files in the Linux drive from OSX. Thanks a lot!

---

### Post by Richardcavell on 2009-06-29
Hi,

Firstly, stop fiddling with your Linux partition from within OS X, or you'll break something.

Secondly, it is quite normal for your computer to behave this way.  OS X cannot read or write the Linux file system. The Linux file system is known as 'ext', and there are numbered variants - ext2, ext3, and ext4. They are all pretty similar.

OS X cannot interpret the Linux partition as anything other than an unused partition.

It is possible to use ext2 using a software package called ext2fs, but it's not very stable and hasn't been maintained well. If you're not a UNIX guru, I suggest that you don't use it. Most people who wish to transfer files between OS X and Linux use a simpler file system such as FAT32 to transfer files between them. You can set up a separate partition for this purpose, or use an external USB key that has been formatted as FAT32. Ubuntu can read your OS X partition but not write to it. But it will respect UNIX file and folder permissions, so it won't let you get into user's home directories, for example.

Richard

---

### Post by cosmicappuccino on 2009-06-29
Oh, ok - thanks very much Richard! :)

---

### Post by Seq on 2009-06-30
> **Richardcavell said:**
> Most people who wish to transfer files between OS X and Linux use a simpler file system such as FAT32 to transfer files between them. You can set up a separate partition for this purpose, or use an external USB key that has been formatted as FAT32. Ubuntu can read your OS X partition but not write to it. But it will respect UNIX file and folder permissions, so it won't let you get into user's home directories, for example.

Regarding UID and permissions: Mac OS starts user numbers at 500 (iirc so do the FreeBSD and OpenBSD) whereas Linux distros typically start at 1000. You can change your uid in one or the other to match up and avoid any issues. I usually create a dummy user when installing, then create my real user and specify my uid at that time.

Regarding filesystems: Ubuntu can actually write **un-journaled** HFS+ partitions fine. Mac OS (like every other OS) uses a journalled filesystem by default, and you probably don't want to change that. You could create an un-journaled case-sensitive filesystem on an external drive for moving data back and forth between OSX and Ubuntu, but remember it would work best if UIDs match.

As Richard pointed out, it would be easiest to just use Fat32 on an external drive (extra partition, or wherever). It puts the *lowest* in lowest common denominator ;)

---

### Post by cosmicappuccino on 2009-06-30
> **Seq said:**
> Regarding UID and permissions: Mac OS starts user numbers at 500 (iirc so do the FreeBSD and OpenBSD) whereas Linux distros typically start at 1000. You can change your uid in one or the other to match up and avoid any issues. I usually create a dummy user when installing, then create my real user and specify my uid at that time.

Regarding filesystems: Ubuntu can actually write **un-journaled** HFS+ partitions fine. Mac OS (like every other OS) uses a journalled filesystem by default, and you probably don't want to change that. You could create an un-journaled case-sensitive filesystem on an external drive for moving data back and forth between OSX and Ubuntu, but remember it would work best if UIDs match.

As Richard pointed out, it would be easiest to just use Fat32 on an external drive (extra partition, or wherever). It puts the *lowest* in lowest common denominator ;)

Thanks Seq! :) I think I'll go with the external drive like you and Richard said - but being a newbie and not knowing much about all this, your detailed explanation was really helpful for me :)

---

