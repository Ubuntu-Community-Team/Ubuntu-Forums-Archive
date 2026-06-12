---
title: "Read only partition"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by darco on 2007-08-16
ok, I am getting frustrated here. I am running 7.04. I have a slave drive that is partitioned in two. I can access both partitions fine but one partition is some how read only while the other is Read-write. I have tweaked my FSTAB file and this morning after a boot up, I was able to delete one particular file but now when I right click any file on that partition, the move to trash is greyed out. 
My fstab shows this for the drive in question.
 /dev/hdb5               /mnt/win                auto rw,users,umask=000 1 0              
/dev/hdb7               /mnt/xp                 auto rw,users,umask=000 1 0

After you make FSTAB changes do you have to reboot or just run mount -a?
I have tried to run the chmod 777 -R command but says its a read only file, ran the chown but it still reports owned by root,...
Running from the terminal I get:
 rm -r Cloak
rm: cannot remove `Cloak': Read-only file system


Any help would be appreciated!

thxs
darco

---

### Post by matthew.lns1 on 2007-08-16
Any chance you used the NTFS file system on that partition? If you did Linux can only read NTFS, not write to it.

---

### Post by darco on 2007-08-16
VFAT for both partitons.....how would I confirm this, thru fdisk -l?
thxs

edit..fdisk reports both are fat32

---

### Post by Arwen on 2007-08-16
sudo apt-get install ntfs-config:
it enables write in an ntfs partition if its your case

---

### Post by Arwen on 2007-08-16
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite")
in my fstab I have "/dev/sda3 /media/sda3 vfat  iocharset=utf8,umask=000  0    0" for a vfat(fat32) partition.

---

### Post by darco on 2007-08-16
Ya, I think that did it.....do I need to update my fstab as it still show what I posted previously. Also I left the partition in the MNT folder since thats how I always done it, will this be a prob? 
thxs for the help
darco

---

### Post by Chaotic Thought on 2007-08-16
Here's a trick for DOS/Windows partitions: to turn off the "executable" flag on all the files, add the flags **umask=0111,dmask=0000**  the "0111" on umask strips off the "x" bits on the files but leaves it on directories (which is what you probably want).

And the OP asked if you have to reboot when you change **/etc/fstab**: No, but you have to remount the partitions; to do this issue **mount -o remount**  and then the partition (if it's in your fstab, you can give **mount** either the device name or the directory name)

---

### Post by Arthur Archnix on 2007-08-16
> rm -r Cloak
rm: cannot remove `Cloak': Read-only file system
If that was your exact command, prefacing it with sudo might solve the problem.
```
sudo rm -r Cloak
```

---

