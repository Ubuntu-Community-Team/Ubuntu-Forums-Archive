---
title: "file sharing windows + ubuntu?"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by kamoteQ on 2008-01-18
Hi all,

I am planning to dual boot windows xp + ubuntu gutsy on my computer when a question popped out of my mind...there would be instances that I would be using the same files on both OS's...now, is it possible these two OS's to share the same file?

Thanks in advance!

---

### Post by jflarm on 2008-01-18
We have ntfs-3g to be able to read and write on ntfs partitions, so if you want to use a file in Ubuntu Linux and XP you just put it on a NTFS partition. XP can't read ext2 or ext3 (linux) partitions, so this is the only way I know of.
....well, actually I think there is some third app out there that can enable you to see linux partitions while running xp.

---

### Post by rahimveron on 2008-01-18
You can access windows ntfs partitions from Gutsy as it has read/write access from defaults.
From Windows you can install explore2fs and access ext3(Linux) partition.
Welcome to UF and Ubuntu.

---

### Post by kamoteQ on 2008-01-18
Thanks for the quick replies!

---

### Post by rahimveron on 2008-01-18
Anytime :D

---

### Post by cosborn72 on 2008-01-18
The third-party program mentioned above is here.
[http://www.fs-driver.org/](http://www.fs-driver.org/)

Install it in windows.

I use it to access my ext 3 volumes from windows.  It works flawlessly.

Remember, 'though, that accessing linux from windows bypasses any protections that linux sets up to protect you.  Don't open the linux filesystem and start deleting files unless you know exactly what they are and what might be effected by deleting them.

The same is true when accessing NTFS from linux.

I would also recommend that all OS's on your system require a password to log in.

---

### Post by lswest on 2008-01-18
also, you could set up a small fat32 partition with those files, which can be read/written to by either OS.  However, the other possibilities are probably more than sufficient for it, just, as was said above, be careful what you delete^^

---

