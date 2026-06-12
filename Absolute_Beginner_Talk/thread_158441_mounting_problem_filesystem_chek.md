---
title: "mounting problem filesystem chek"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by gagatz on 2006-04-11
Hello, I have the following situation on my computer: There is one physical drive with a windows partition and another physical drive with three partitions, one (ext3) containing the filesystem, one partition (virtual fat) containing loads of data and a third partition with nothing really on it (hdd3) on which back in a day i started a gentoo installation (ext3) which took some place of it, and by which i think, this partition was reparitioned into even smaller bits. However some days ago i thought it would be a good idea to reformat it since space was getting rare. So i formatted it virtual fat and the next time i booted the following error occured:

It booted until "-checking all filesystems" then it switched from the ubuntu style screen to the old dos style screen with black background and big white letters and told me:

fsck.ext3: Bad magic number in super-block while trying to oben /dev/hdd3
/dev/hdd3: The superblock could not be read or does not describe a correct ext2 filesystem.
If the device is valid and it really contains an ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt and you may try running e2fsck with an alternate superblock e2fsck -b 8193 <device>

* fsck failed. Please repair manually
* CONTROL-D will exit from this shell and continue system startup



Now as i retyped the error i can see how it is possible to load ubuntu again (simply press ctrl d) but still i have no clue of how this error could occure and how it can be wiped out. If you answer, please explain a bit more detailed, since i'm still not very versatile with this linux. Thank you

---

### Post by cleverselfreferentialname on 2006-04-11
You need to run fsck on it manually in order to fix this. You will need a linux liveCD, because its unsafe to run fsck on a mounted filesystem. From a terminal, run sudo fsck /dev/hda1 (assuming /dev/hda1 is the device name of the partition, the second disk is /dev/hdb. so the first partiton would be /dev/hdb1). If you have an SATA hard drive, its /dev/sda1 instead.

Cheers,
Paul

---

