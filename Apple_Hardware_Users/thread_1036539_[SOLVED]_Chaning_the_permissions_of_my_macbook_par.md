---
title: "[SOLVED] Chaning the permissions of my macbook partition"
date: 2009-01-10
forum: Apple Hardware Users
---

### Post by rifak on 2009-01-10
hey everyone, i am trying to be able to mount, read, and write to my macbook partition. i can mount and then read only the files/folders in the main directory but i cannot create folders or save anything to it. i am wondering if there is a way to be able to change my macbook partition to allow for this. ie, changing the permissions of the whole thing or at least to one folder to be able to save to that partition. thanks

---

### Post by RobSoko315 on 2009-01-11
I've the same problem, so if you find a solution, please post back here, thanks.  I've heard its possible if any only if your mac partition isn't journaled. 

-Rob

---

### Post by bryonak on 2009-01-11
You can't write on a journaled HFS+ partition.

Your options are:

- Move everything to your Linux partition (it's native format is ext3). You can mount ext3 "as ext2" in OSX.

- Make a new partition to share the files between the systems, which should be either ext2 or ext3. (or you could use FAT32, though that one isn't really great)

- Backup everything, then format your OSX partition to HFS+ with journaling turned off. Then reinstall OSX and restore from backups.
You won't miss much without journaling if it's a typical desktop user case.

- Put up with not being able to write and use it as read-only.

---

### Post by RobSoko315 on 2009-01-11
> **bryonak said:**
> You can't write on a journaled HFS+ partition.

Thanks.

Just out of curiosity, why can't Linux write to HFS+?

---

### Post by Rog-Mahal on 2009-01-11
To be clear, HFS+ is not the problem, *journaled* HFS+ is. [Here is some information about journaling.]("http://support.apple.com/kb/HT2355?viewlocale=en_US") [This Mac forum]("http://forums.macrumors.com/showthread.php?t=406260") also discusses the topic. It doesn't completely answer your question, but I think it's a start.

---

### Post by rifak on 2009-01-12
thanks guys. i figured it out.

first, in mac, i turned off journaling by simply command lining:

diskutil disableJournal disk0s2

it required no formatting or anything. this allows me to do anything in my mac hard drive from ubuntu. awesomeeeee.

i then installed ext2fs to my mac, which allows me to mount my linux hard drive and do anything to it. niiiiice

now i have access to my whole comp, from both partitions, without worrying about how much space i alloted to either one.\\:D/

---

