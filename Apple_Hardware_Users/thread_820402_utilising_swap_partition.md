---
title: "utilising swap partition"
date: 2008-06-06
forum: Apple Hardware Users
---

### Post by senuxis on 2008-06-06
Ubuntu is not loading the swap partition. Please help.

---

### Post by ilrudie on 2008-06-06
What do you mean it is not loading the swap partition?  To enable swap if its disabled run 'swapon -a'.

If what you meant to say was Ubuntu is not using any swap then thats a good thing.  It means you have enough ram to run all your programs without having to swap program's memory onto disk.  It also means Ubuntu probably has enough space to cache commonly used files in ram instead of having to read them off the disk all the time.  If thats not the case let me know and I will see what I can do to help.

---

### Post by ajgreeny on 2008-06-06
Have you installed another linux distro after ubuntu?  If you have, it may have formated the swap you've been using and changed its UUID so it does not mount at boot time.  This didn't happen in older ubuntu versions as the fstab file worked using /dev/hd* nomenclature, not UUIDs.

Find out what your partition UUIDs are by using ```
 ls -l /dev/disk/by-uuid
``` and copyf the swap partition UUID alphanumeric string.  You can then backup your fstab file with ```
sudo cp /etc/fstab /etc/fstabbak
```and then edit your fstab with ```
gksudo gedit /etc/fstab
```changing the old UUID to new.  Now ```
sudo mount -a
``` should get it back and running.

You could even go back to fstab using the /dev/hd* naming system, which still works, but as an exercise in understanding linux partitioning, I thought it worth giving you the whole works.

---

