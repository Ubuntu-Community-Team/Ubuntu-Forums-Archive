---
title: "Installed NTFS3g, now need permission to read/write to external drive."
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by marco123 on 2007-05-13
hi.

Is there a terminal command to give me permission to read/write and delete from my external hard drive?

I've installed ntfs3g and enabled it, just need permission now. :) 

Any help greatly appreciated, all the searches I've pulled up point to installing the ntfs3g driver, but I've already done that. :)

---

### Post by taurus on 2007-05-13
How did you mount that external harddrive?  Did you mount it by hand or was it automounted when you plugged it in?

```
df -h
```

---

### Post by marco123 on 2007-05-13
Automatically mounted when i reinstalled.

---

### Post by taurus on 2007-05-13
Can you post the output of that command?

---

### Post by marco123 on 2007-05-13
Filesystem            Size Used Avail Use% Mounted on
/dev/sda1              53G  2.2G   48G   5% /
varrun                502M  104K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
procbususb            502M  112K  502M   1% /proc/bus/usb
udev                  502M  112K  502M   1% /dev
devshm                502M     0  502M   0% /dev/shm
lrm                   502M   33M  469M   7% /lib/modules/2.6.20-15-generic/volatile
/dev/sdb1             299G   71G  228G  24% /media/VAULT

---

### Post by taurus on 2007-05-13
Try something like

```
sudo umount /dev/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/VAULT -o locale=en_US.utf8
ls -la /media
```

---

### Post by marco123 on 2007-05-13
It unmounted, but on the second command it came back with an error -

fusermount: failed to access mountpoint /media/VAULT: No such file or directory
FUSE mount point creation failed
Unmounting /dev/sdb1 (VAULT)

---

### Post by taurus on 2007-05-13
```
**sudo mkdir /media/VAULT**
sudo mount -t ntfs-3g /dev/sdb1 /media/VAULT -o locale=en_US.utf8
ls -la /media
```

---

### Post by marco123 on 2007-05-13
says -

mkdir: cannot create directory `/media/VAULT': File exists

---

### Post by taurus on 2007-05-13
Try

```
sudo mount -t ntfs-3g /dev/sdb1 /media/VAULT
ls -la /media
```

---

### Post by marco123 on 2007-05-13
The mount commands don't seem to like me,lol.

I'm sure last time I did something about sudo owning the file?

---

### Post by taurus on 2007-05-13
What is the exact error message now?

What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by marco123 on 2007-05-13
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6992    56163208+  83  Linux
/dev/sda2            6993        7296     2441880    5  Extended
/dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568641    7  HPFS/NTFS

---

### Post by marco123 on 2007-05-13
Found it, was sudo chown mark /media/VAULT. :) 

Thank you for helping me.

---

