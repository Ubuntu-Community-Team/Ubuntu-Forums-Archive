---
title: "[SOLVED] change volume label"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by il-luzhin on 2008-03-19
how does one change volume label?

---

### Post by ruy_lopez on 2008-03-19
> **il-luzhin said:**
> how does one change volume label?

```

e2label /dev/hdaX <new label>

```

Replace /dev/hdaX with the device you want to change. Use "df" if you don't know the device.

Running "e2label" without a label, shows you the current label.

---

### Post by Rocket2DMn on 2008-03-19
It depends on your filesystem, scroll down in this link, there is a section about labeling - [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by il-luzhin on 2008-03-19
luzhin@kerenin:~$ e2label /dev/sde1 exHDD
e2label: Bad magic number in super-block while trying to open /dev/sde1
Couldn't find valid filesystem superblock.

---

### Post by ruy_lopez on 2008-03-19
> **il-luzhin said:**
> luzhin@kerenin:~$ e2label /dev/sde1 exHDD
e2label: Bad magic number in super-block while trying to open /dev/sde1
Couldn't find valid filesystem superblock.

e2label is for ext filesystems.

---

### Post by il-luzhin on 2008-03-19
maybe i should start again.  I want dev to mount to /media/exHDD, but it doesn't, it mounts to /media/Media and BU.  So I thought I'd just rename volume.  

I know my dev ID but thought fstab only worked during bootup.  I am wrong?

Filesystem NTFS btw

---

### Post by Rocket2DMn on 2008-03-19
Changing the label won't help if there is an fstab entry.  If you modify your fstab, you can remount the partition first by unmounting it then, running
```
sudo mount -a
```

---

### Post by ruy_lopez on 2008-03-19
> **il-luzhin said:**
> 
I know my dev ID but thought fstab only worked during bootup.  I am wrong?

You can mount a fstab partition any time. Just run "mount /path/mountpoint" and it should mount (assuming your fstab entry is correct).

To mount to a different mountpoint, create a folder, and change the "fstab" mountpoint to the path of the new folder.

---

### Post by il-luzhin on 2008-03-19
thnx folks

---

