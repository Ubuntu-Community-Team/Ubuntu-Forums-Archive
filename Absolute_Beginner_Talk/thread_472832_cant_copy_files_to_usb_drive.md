---
title: "cant copy files to usb drive"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by fast eddie on 2007-06-13
I have just plugged in my usb external drive to copy some files over to my windows machine but I get an error saying I dont have the correct permissions. Can someone please let me know what I have to do so I can copy the files over. They are .flac files if that makes any difference but I cant see why it should.

ta

---

### Post by Happy_Man on 2007-06-13
Have you checked the permissions? Go to /media/<name of drive>'s properties and check those.

---

### Post by skymera on 2007-06-13
or log in as root.
but not iddeal.

is it possible to do by CLI?

---

### Post by Songwind on 2007-06-13
What filesystem is the USB drive formatted with?

If it's NTFS you will have to set up your fstab to use "ntfs-3g" for read/write permissions.  The default ntfs driver only provides read access.

---

### Post by fast eddie on 2007-06-13
Thanks for the replies, I think it must be NTFS.

Can you point me in the direction of a good idiots guide of how to set up my fstab  :confused::confused::confused:

---

### Post by Happy_Man on 2007-06-14
An idiot's guide? To me, the best way to do it would be install ntfs-3g and ntfs-config. Easy as anything I've ever seen......

---

### Post by vanadium on 2007-06-14
A better way is to reformat the drive altogether to ext2 or ext3, the native Linux file system. For compatibility, you can use fat32.

Formatting goes like
```

sudo mkfs -t ext3 /dev/sda1

```
where sda1 needs to be replaced by the actual partition you want to format.

```

sudo fdisk -l

```

lists all drives and their partitions on your system. Make sure you pick the right one!

Replace ext3 with vfat to format fat32.

ntfs-3g officially is still beta, so only use it if you want to take (probably very little by now) risks.

---

### Post by Happy_Man on 2007-06-14
Actually, I recommend not using FAT32 at all. Windows has drivers available for it that will allow read/write to ext3 volumes available @ [http://fs-driver.org](http://fs-driver.org).

---

