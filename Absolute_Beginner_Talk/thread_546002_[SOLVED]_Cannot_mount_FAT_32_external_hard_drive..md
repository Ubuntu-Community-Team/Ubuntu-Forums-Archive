---
title: "[SOLVED] Cannot mount FAT 32 external hard drive."
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by cwrann on 2007-09-08
I recently changed the file system on my external hard drive from nstf to FAT 32 on my external hard drive using gparted. now when I click on the external hard drive icon I get this message:

Cannot Mount Volume:
The volume uses fat32 file system which is not supported by your system.

I thought that ubuntu supported FAT 32.

---

### Post by mikeyphi on 2007-09-08
Did you make alterations to your fstab after the format change?
Look here for possible help:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

---

### Post by cwrann on 2007-09-12
I have used this guide quite a bit, unfortunately the link you gave me refers to an internal hard drive partition that has windows running on it. I have an external hard drive connected via USB. I used to be able to read it when it was formated as ntsf now that I have reforemated it to the more ubuntu friendly fat 32 it will not mount it at all.

---

### Post by cwrann on 2007-09-22
This did it:

```
sudo mkdir /media/usb

```

then:

```
sudo mount /dev/sdb1 /media/usb -o umask=000

```

---

