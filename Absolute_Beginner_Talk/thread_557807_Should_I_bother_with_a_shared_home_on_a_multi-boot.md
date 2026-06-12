---
title: "Should I bother with a shared /home on a multi-boot setup?"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by Overbyte on 2007-09-23
I'm planning to do a multi-boot setup (XP, Vista, Feisty, OpenSUSE, and Gutsy), and I've heard that by having all the /home's of your Linux systems mounted on the same single partition, you need to fuss around with group IDs and symbolic links. I've read the posts and it seems that I'm afraid that it can mess things up a lot (some got their accounts locked out). Should I bother with this or just use the classic "shared FAT32 partition" setup which every OS can use and just mount the /home's of the respestive OSes into the same place as / is mounted to?

Thanks in advance!

---

### Post by pheeror on 2007-09-23
You can used shared fat32,ntfs or ext2/3. All of these work in both windows and linux. I'm not sure, but reiserfs is maybe accessible from windows too. That's not the problem. 
Problem is shared /home. You can ensure consistency of UID/GID throughout linux systems without significat afford. Problem lies in different format of ~/.* files and different versions of progams. On the other hand, you can risk it and it'll probably work fine.

---

### Post by fumduck on 2007-09-23
I am sharing /home and swap between 7.04 32 and 7.04 64 Fiesty  No problems so far....

---

### Post by Ozeuss on 2007-09-23
> **Overbyte said:**
> I'm planning to do a multi-boot setup (XP, Vista, Feisty, OpenSUSE, and Gutsy), and I've heard that by having all the /home's of your Linux systems mounted on the same single partition, you need to fuss around with group IDs and symbolic links. I've read the posts and it seems that I'm afraid that it can mess things up a lot (some got their accounts locked out). Should I bother with this or just use the classic "shared FAT32 partition" setup which every OS can use and just mount the /home's of the respestive OSes into the same place as / is mounted to?
Thanks in advance!
like pheeror said- the problem might be in configuration files that might be identical i all distros. ext3 is a better file system than FAT, and you can access it from windows, so you would be better of using it as a shared partition anyway.
I don't think there would be much of a problem sharing /home between feisty and gutsy. You might still share /home with Suse, just use a different user (so different conf files, for good and bad).

---

