---
title: "Um... I CAN right to fat32... right?"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by Roasted on 2008-01-06
I have a fat32 external hard drive.
I mounted it to a folder in /media called externalhdd.
I granted 777 rights to externalhdd.
Yet it says I don't have permission to write to that drive.
WTF

---

### Post by PurposeOfReason on 2008-01-06
FAT32 can't be chown'ed or chmod'ed. You have to set it up that way in the fstab. A good place to start:

[http://wiki.archlinux.org/index.php/Writing_on_a_FAT32_partition_as_a_normal_user](http://wiki.archlinux.org/index.php/Writing_on_a_FAT32_partition_as_a_normal_user)

---

### Post by observative on 2008-01-07
For a more in depth understanding see this [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite) and this [http://linux.die.net/man/8/mount](http://linux.die.net/man/8/mount) and there is this popular thread to [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by insane_alien on 2008-01-07
basically, FAT32 sucks. use ntfs if it needs to be compatable with windows or ext3/reiserfs/XFS/JFS if it only needs to be used with linux.

---

### Post by philinux on 2008-01-07
As has been said you cant chown or chmod the device. But you can chown or chmod the mount point eg chown /media/diskx

---

### Post by stchman on 2008-01-07
> **Roasted said:**
> I have a fat32 external hard drive.
I mounted it to a folder in /media called externalhdd.
I granted 777 rights to externalhdd.
Yet it says I don't have permission to write to that drive.
WTF

That is interesting as most USB drives are FAT32 and you can write to them no problem.

---

### Post by observative on 2008-01-10
I had similar difficulties with one of my drives. Until I added "umask=007,gid=46" to my fstab I couldn't do much other than look at the files and folders. One of the links I gave up above has the details for the fat "options" for fstab. No matter how many times you change owner or mod, if the fstab file is not set correct, you won't be able to do it.

---

### Post by Roasted on 2008-01-11
I forget how, but I got it working.

I wanted FAT32 due to the fact that this external hard drive would be used with Windows 2000 Pro/XP/Vista/Ubuntu/Debian machines.

---

