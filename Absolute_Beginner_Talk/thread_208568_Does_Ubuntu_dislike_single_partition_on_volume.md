---
title: "Does Ubuntu dislike single partition on volume??"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by Average_Joe on 2006-07-03
Thanks for reading.  I started an XP install from scratch on a new hard disk, with intention to dual boot Ubuntu from this disk.  I was successful, but one Ubuntu install feature still has me puzzled.

_What I did:_
1)  Brand new freshly NTFS formatted hard disk, fully formatted into a single partition, and installed Windows XP to it.
2)  Used Ubuntu 6.06 LiveCD (desktop 386) to attempt to install Ubuntu.  I chose the option that would automatically resize and move the Windows partition, and squeeze in Ubuntu partitions.  This seemed to be the option for newbies, so I chose that one, and let her rip.
3)  A short time later the Ubuntu install reported that it was unable to resize and move the partition.  The install was thus cancelled.

My question is why?  It would indeed seem that this particular option was ready-made for my situation, yet it couldn't complete the operation.

I did resolve the problem, but I won't detail it right here in this original post, so as to keep the conversation flow in one direction.  Thanks, experts!

---

### Post by rum and monkey on 2006-07-03
I'm no expert, and I don't have the answer, but the same thing happened to me. When trying to resize the main partition of my external harddrive (no operating system was on it) it gave me some crazy error (in the program I was using) Just thought I'd tell you, and of course, bring your thread to the top again :-)

---

### Post by bukwirm on 2006-07-03
Try resizing your NTFS partition with gparted (availible on the LiveCD), then, during the install, choose the option about using all free space for Ubuntu. I think the installer can't resize NTFS partitions.

---

### Post by Average_Joe on 2006-07-03
[QUOTE=bukwirm]Try resizing your NTFS partition with gparted (availible on the LiveCD), then, during the install, choose the option about using all free space for Ubuntu. I think the installer can't resize NTFS partitions.[/QUOTE]


bukwirm -- That's exactly what I did to resolve the problem (although I didn't describe my resolution earlier purposefully).  If the installer cannot resize NTFS partitions, then yep, that is exactly the problem/issue.  Thanks for the answer.

---

### Post by az on 2006-07-03
[QUOTE=bukwirm]I think the installer can't resize NTFS partitions.[/QUOTE]
It certainly can and has been able to for about two years, now.

The installer is very careful when partitioning.  It is, in fact, paranoid and will balk before it takes the risk of losing your data for you.

Common things you can do to treat this are to free up a little more space and to defragment your ntfs partition before you install ubuntu.

So, in short, what happened to you is not what is supposed to happen, but can happen from time to time.  Considering the ntfs partitioner is reverse-engineered, and that probably most people who use the forums dual boot windows and ubuntu, it's still pretty impressive.

Another thing that I have noticed is that the *windows* installer cannot properly handle linux filesystems.  If you have a few linux partitions on a drive and try to install windows Xp on it without deleting all of the "foreign" partitions, you can end up with a successful install and a bootable windows, but a partition table that is no longer usable by any partition tool that I know of.  Strange.

---

### Post by Apple 101 on 2006-07-04
[QUOTE=azz]Another thing that I have noticed is that the *windows* installer cannot properly handle linux filesystems.  If you have a few linux partitions on a drive and try to install windows Xp on it without deleting all of the "foreign" partitions, you can end up with a successful install and a bootable windows, but a partition table that is no longer usable by any partition tool that I know of.  Strange.[/QUOTE]That has never happened to me...

---

### Post by lamego on 2006-07-04
> Another thing that I have noticed is that the *windows* installer cannot properly handle linux filesystems. If you have a few linux partitions on a drive and try to install windows Xp on it without deleting all of the "foreign" partitions, you can end up with a successful install and a bootable windows, but a partition table that is no longer usable by any partition tool that I know of. Strange.

Have you tried fdisk on Ubuntu ?

The inability from Windows to recognize Linux partitions does not interfere with the partition table as far as I have experienced.

---

