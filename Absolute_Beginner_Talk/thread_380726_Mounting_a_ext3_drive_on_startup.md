---
title: "Mounting a ext3 drive on startup"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by Copperteeth on 2007-03-10
I have a harddrive partition i recently made into a ext3 partition that i use in windows and i want to use it in ubuntu.

fdisk tells me this:
```
  Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2366    19004863+   7  HPFS/NTFS
/dev/hda2            2367        3933    12586927+  83  Linux
/dev/hda3            3934        9715    46443915   83  Linux
/dev/hda4            9716        9964     2000092+   5  Extended
/dev/hda5            9716        9964     2000061   82  Linux swap / Solaris

```

the harddrive is hda3 and i want to mount it to my hda3 folder i made in /media. What would i put into fstab to get it to mount on startup.

---

### Post by taurus on 2007-03-10
```
/dev/hda3   /media/hda3   ext3   defaults   0   1
```
Then, don't forget to create a new mount point for it.

```
sudo mkdir /media/hda3
sudo mount -a
df -h
```

---

### Post by that guy on 2007-03-10
nano or vi /etc/fstab

add the line

/dev/hda3       /media/yourfolder    ext3    defaults        0       0

I believe the default format for Linux is ext3.

Also, check out 

[http://wiki.linuxquestions.org/wiki/Add_a_new_hard_drive](http://wiki.linuxquestions.org/wiki/Add_a_new_hard_drive)

---

