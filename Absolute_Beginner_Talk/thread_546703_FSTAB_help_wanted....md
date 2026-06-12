---
title: "FSTAB help wanted..."
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by keithkiss on 2007-09-09
I want to make a fat32 partition writable.  How would I do this?
Thanks ;)

Here is my fstab entry.

/dev/hda5 / ext3 noatime 1 1
/dev/hda7 /mnt/fat32 vfat umask=0 0 0
none /proc proc defaults 0 0
/dev/hda6 swap swap defaults 0 0

I can read the files from the fat32 partition but not write.

Thanks for any help

---

### Post by Steve1961 on 2007-09-09
See this link for instructions:

[http://easylinux.info/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://easylinux.info/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

---

### Post by vanadium on 2007-09-09
From what I see, you should need to add the option iocharset=utf8 (allows to correctly handle "foreign" characters) and complete the umask (I am not sure the umask is necessary because vfta cannot handle permissions!). Thus, your line should become

/dev/hda7 /mnt/fat32 vfat iocharset=utf8,umask=000 0 0

Anyway, while this will correct your mounting, it won't solve your permisions problem. For that, you need to change the permissions of your mount point:

sudo chmod 777 /mnt/fat32

This will allow the owner (probably root), the group (probably root) and all others (you as user, any other user, anyone who can connect to your system over the internet ....) to read/write/execute on the drive.

If you want to be much more restrictive (i.e. you can write, but other users can 't), then you must take ownership of the mount point and restrict permissions for others:

sudo chown $USER:$USER /mnt/fat32
sudo chmod 700 /mnt/fat32

(you can type $USER as is: it will expand to your actual username).

I am being a bit verbose here for you (and others) to learn a bit more about it and in particular to show that, on a Linux system, *you* (as root) are in charge and make the decisions.

---

