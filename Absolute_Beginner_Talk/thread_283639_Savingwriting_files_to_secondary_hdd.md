---
title: "Saving/writing files to secondary hdd"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by trafaelwyr on 2006-10-24
First off, I'm new to the whole Linux OS.  Long story short, I was advised to give Ubuntu a try to see if I liked it.  So far it's been a bit of a challenge after having dealt with Windows for so long.  Here's the problem - I have 2 hdd, the smallest of which has the Linux OS on it.  The other hdd (250gb) is pretty much the slave drive.  When I've tried to save downloads to the 250gb drive, I receive an error message saying that I can't.  The hdd is NTFS.  How do I go about making this drive accessible to files I want to download?  Thanks in advance for any advice!

---

### Post by Kateikyoushi on 2006-10-24
You have to mount that partition with read and write permissions. To do so follow these instructions. [LINK]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access")

This might cause problems so it would be better to resize the bigger hard drives partition and make a fat or ext partition on it.
You can read and write ext partitions from windows with this driver. [LINK]("http://www.fs-driver.org/")

---

### Post by AntiFlash on 2006-10-24
long story short: NTFS write is not officially supported/developed in linux.  
Sneak attack version:  some distros have built in NTFS read/write support, but it has not officially sanctioned and is by no means stable.  if linux is your only OS, you might as well just go with a full linux supported file system like EXT3 or REISERFS (though EXT3 is the preferred/standard choice).

---

### Post by bodhi.zazen on 2006-10-24
> **trafaelwyr said:**
> The other hdd (250gb) is pretty much the slave drive.  When I've tried to save downloads to the 250gb drive, I receive an error message saying that I can't.  The hdd is NTFS.  How do I go about making this drive accessible to files I want to download?  Thanks in advance for any advice!

Yes, try this: [url=http://ubuntuforums.org/showthread.php?t=217009
]ntfs-3g (allows rw access to nts)[/url]

Alternates:[list=number][*]Make your slave drive FAT32.[*]Make your slave drive ext2.[/list]

BTW: Welcome to Linux.

---

