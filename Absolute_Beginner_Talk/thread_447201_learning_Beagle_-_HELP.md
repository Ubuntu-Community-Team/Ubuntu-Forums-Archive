---
title: "learning Beagle - HELP"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by Korrontean on 2007-05-17
Hi there.

I've installed Beagle, and I've read this :confused::(:(:(:confused:on its official website:

> ENABLING EXTENDED ATTRIBUTES:

Extended attributes are used by Beagle to keep track of which files have been indexed and which need to be re-indexed. There is an sqlite-based fallback which is very slow, so it is highly recommended that you do use extended attributes.

Patches for 2.4 kernels which do not include extended attributes by default can be found at [http://acl.bestbits.at/download.html#Kernel](http://acl.bestbits.at/download.html#Kernel).

Your kernel will need support for extended attributes on the filesystem you are indexing. If you are using XFS or JFS, extended attributes are always enabled and you can skip this section and move on to Installing prerequisites. For Reiser3, ext2 and ext3 filesystems, the default kernel config does not enable the attributes.

For ext2 filesystems, the kernel option for attributes is CONFIG_EXT2_FS_XATTR. For ext3, it's CONFIG_EXT3_FS_XATTR. For Reiser3, it's REISERFS_FS_XATTR.

To set extended attributes, you should add the user_xattr property to the relevant file systems in your /etc/fstab file. For example:

/dev/hda3     /home     ext3     defaults,user_xattr     1 2

You can then remount the affected partitions as follows:

# mount -o remount /home

Also note that neither Reiser4 nor NFS support extended attributes, so the sqlite-based fallback will be used by default.

Once this is complete, you can move onto the next step: Installing prerequisites.
Retrieved from "http://beagle-project.org/Enabling_Extended_Attributes"

Can anyone translate it to beginner language? Do I really need to do this all? I'm using Ubuntu Dapper Drake.

:)THANK YOU VERY MUCH:)

---

### Post by dbera on 2007-05-17
For the start, no. You can safely skip this step about extended attributes.

---

### Post by Korrontean on 2007-05-18
Thanks, Dbera.:):):)

---

