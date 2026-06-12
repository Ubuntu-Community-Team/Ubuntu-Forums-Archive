---
title: "[SOLVED] File access"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by Coot2 on 2007-11-12
In my dual boot system (Dapper/XP), I show 2 volumes in the Computer-File Browser. The one contains my Ubuntu files, the other I assume contains my windows-created files. When I try to access them I get a message "unable to mount the selected volume".  Details are: error: device /dev/hda1 is not removable and error: could not execute pmount. What do I do to access these files while in the Ubuntu system? I have already created a file /media/windows. My system is NTFS. The command 
sudo /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
yields the message /dev/hda1: command not found.
???:confused:

---

### Post by taurus on 2007-11-12
Try using the **mount** command if you want to mount a partition.

```
sudo mount -t ntfs /dev/hda1 /media/windows -o nls=utf8,umask=0222
```
Make sure you have /media/windows first before you run the mount command.

```
sudo mkdir /media/windows
```

---

### Post by Coot2 on 2007-11-12
THanks, worked like a charm!

---

