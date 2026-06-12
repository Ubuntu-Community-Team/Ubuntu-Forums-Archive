---
title: "Turn off Windows 7 permissions for ntfs so drive can be shared"
date: 2013-02-16
forum: Any Other OS
---

### Post by nosehat on 2013-02-16
Hi all,

I'm posting this to Absolute Beginners even though I've used Ubuntu for a while, because this seems like a noob-ish question.

My main computer dual boots Ubuntu 12.04 and Windows off its OS drive, and it also has an internal NTFS formatted data drive shared by the two OSes.  I've also got a bunch of external drives for backup and archival storage, all of which are formatted NTFS.  I've chosen NTFS because 1) easy sharing between OSes, and 2) large file sizes.  I boot Ubuntu 95% of the time, but keep Windows around for a few tasks, like editing MP3 tags.

For years I've had Windows XP on my Windows partition, but I've recently upgraded to Windows 7.  The problem I've encountered is that WIndows 7 apparently introduced the concept of file permissions on NTFS file systems (XP didn't do this).  From what I've read on the web, it seems like W7 uses a different method of storing these permissions than Linux.  I discovered this problem tagging mp3 files on an external drive in W7:  In a directory of podcasts downloaded years ago, I was able to modify some of the files just fine, but W7 didn't let me modify others due to the new permission system.  There seemed to be no rhyme or reason to what was allowed and what wasn't.

**My question:  Is there a way to turn this behaviour off in Windows 7?**  I am reluctant to start modifying permissions on my files and directories from inside Windows 7, because I am afraid that might mess up my ability to access the files from Ubuntu.  I can't easily experiment either, since I've got TBs of archived and backed up data stored this way--if I have to back up all of this to experiment, I'll have to buy a lot of extra storage for backups of my backups.

Again, this seems like a noob-ish question to me.  I realize I'm late to the game with Windows 7, but surely there's an easy way to share large files without hassle, and without danger of one OS corrupting the permissions/file system for the other.

Thanks in advance,

Nosehat

---

### Post by cariboo on 2013-02-16
Moved to Other OS Talk as it seems to have more to do with Windows than it does with Ubuntu, seeing as Windows doesn't understand Linux permissions.

---

### Post by nosehat on 2013-02-17
OK, thanks, if you think it will be more likely to get a response here.

Surely it's not uncommon for someone who uses Ubuntu to need to share files with a Windows environment, so I can't be the only one with this issue.

---

### Post by Erik1984 on 2013-02-17
As far as I know file permissions you set in Ubuntu on an NTFS-partition have no effect on Windows. But I could be wrong here ;) What can be a problem (I know from my experience with a similar setup as you) is if you used certain characters in your file/directory names that are illegal in NTFS on Windows but can be written by Linux. Examples are "?" and ":". If you try to access such a file on Windows you get an error.

---

### Post by nosehat on 2013-02-18
Thanks for your reply, Euroman.  You are right about the disallowed characters for MS--I've run into that problem before.  

But that's not the issue I'm facing with Windows 7.  It's specifically a permissions issue.  In the case of the mp3 files, I can access them and play them, but Windows 7 tells me I lack the permissions to modify them.

---

