---
title: "Ubuntu is not viewing the filename correctly [Resolved]"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by NaCl on 2007-01-29
i have a fat32 serving as a storage partition for both xp and ubuntu
i transferred some files with chinese characters to the fat32 partition using xp
when i go back to ubuntu, the characters were converted to ???
when i go back to xp, the characters were normal
how do i fix this?

also, that fat32 partition was formatted from a former ext3 partition
now i can't get the fat32 partition to automount to /storage
how do i fix this so i will mount to /storage automatically like it used to

thanks in advance

---

### Post by aysiu on 2007-01-29
One of [these threads](http://ubuntuforums.org/tags/index.php/chinese/) may help you with installing Chinese font support.

As for mounting the FAT32 partition, try this: ```
sudo nano -B /etc/fstab
``` Find the line for your FAT32 partition (let's just say it's /dev/hda2, but I have no idea what it is). Change it to read: ```
/dev/hda2 /storage vfat iocharset=utf8,umask=000 0 0
``` and delete any other line that refers to /dev/hda2 (or whatever it really is). Then save (Control-X, Y, Enter). Finally, reboot or ```
sudo umount /storage
sudo mount -a
```

---

### Post by NaCl on 2007-01-29
thanks a lot, it works now
i can see the chinese characters and it mounts automatically
i should study the lines

---

