---
title: "Chmod and chown not allowed"
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by sebas on 2006-02-21
I've just installed a new harddrive and partitioned it with gparted. I've mounted the partitions to directories in / but now I can't change the permissions of those directories or it's contents.

For example
I have a partition mounted to /docs. I want to store documents here per user that I can access on my windows laptop as well. The partition is a fat32 partition.

I have made a directory /docs/sebastiaan and now I want to change the ownership to my user "sebastiaan". Whatever I try I can't change the permissions, user or group of the directory. The ownership stays root, group root and 755 as permissions.

Samething for the /docs directory. Using nautilus doens't work either. I get the error message that it's not possible to change permissions, I'm running nautilus as root.

What do I do now :confused:

---

### Post by kaamos on 2006-02-21
Hello!

Look here: [http://ubuntuguide.org/#automountfat](http://ubuntuguide.org/#automountfat)

---

### Post by sebas on 2006-02-21
That didn't work. Mounting doesn't work. According to the syslog because isocharset=utf8 is a unrecognized mount option or missing value.

Removing the isocharset works as the partition is mounted and as a normal user I can create a directory.

But the problem now is that as a normal user I created a directory called sebastiaan. Which is created but with the owner as root and permissions at 777.
Altough I can read and write to the directory so can the whole world when they access my computer and I want to change the ownership of the directory to my own username and group so I can read and write to it but not anybody else.

Or is this not possible on a fat32 partition?

---

### Post by frodon on 2006-02-21
It's because FAT32 don't support unix rights and ownership so chmod and chown commands don't work with FAT32 FS.
However if you wish you can specify a owner when you mount the partition, see this post for details : [http://www.ubuntuforums.org/showpost.php?p=463583&postcount=12](http://www.ubuntuforums.org/showpost.php?p=463583&postcount=12)

---

