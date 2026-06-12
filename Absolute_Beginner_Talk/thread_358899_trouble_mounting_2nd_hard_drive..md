---
title: "trouble mounting 2nd hard drive."
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by pirata on 2007-02-11
I've only just switched over from windows to Ubuntu (dapper drake) and have just tried to mount my 2nd hdd which contains all my data. I tried to follow the instructions for mounting windows partition given on psychocats and used the fdisk -l command to locate the current mount points:

Disk /dev/hda: 20.4 GB, 20496236544 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2398    19261903+  83  Linux
/dev/hda2            2399        2491      747022+   5  Extended
/dev/hda5            2399        2491      746991   82  Linux swap / Solaris

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14946   120053713+   7  HPFS/NTFS

I then tried to create a new mount point as directed, and then edit the fstab file but I'm not sure what I'm doing here... can anyone explain to me a bit more simply what I need to do at this point, as I wasn't sure what the differences meant between the 'before' and 'after' examples in the edit fstab step... 
Thanks!

---

### Post by taurus on 2007-02-11
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/hdb1   /media/hdb1   ntfs   nls=utf8,umask=0222   0   0
```
Save it.  Then create a new mount point and mount it.

```
sudo mkdir /media/hdb1
sudo mount -a
df -h
```

---

### Post by pirata on 2007-02-12
Great, thanks very much. Now it's mounted I need to browse its contents and save new stuff on it and I can't figure out how to do that at the moment...(did I mention I'm new to this?!) Please can you tell me how I can set that drive up to be the default location for new files to be saved in, or at least so it's there as an option when I go to 'save as'. 
Cheers!

---

### Post by taurus on 2007-02-12
You cannot write/save to ntfs filesystem unless you install ntfs-3g driver for it.  Right now, it's a read-only filesystem.

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

