---
title: "How to back up your Ubuntu files"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by RobotoWorks on 2007-12-09
I want to delete my Ubuntu that way I can go back to XP, and dual boot Ubuntu from there, since Ive been told you need Windows first in order to dual boot, right now Im on Ubuntu 7.10, how do I backup my Ubuntu files? That way when I install Ubuntu again, all my stuff will still be there/

---

### Post by finer recliner on 2007-12-09
back up your home directory and any system configuration files you think are important (i.e. /etc/X11/xorg.conf). your home directory contains most of your personal settings for most of your applications. 

i like to use tar to backup my files. i know there are other applications available that are made specifically for backing up files.

```
man tar
``` for more information

---

### Post by thelatinist on 2007-12-09
```
tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/media --exclude=/sys /
```

This will gzip all everything to a single archive.  It excludes virtual folders that change with each session and mounted partitions and external drives.  You can burn that to a DVD or back it up to a network share.  When you are ready to restore it, use:

```
tar xvpfz backup.tgz -C /
```

Before you boot your system, be sure to recreate the folders you excluded:

```
mkdir proc
mkdir lost+found
mkdir mnt
mkdir media
mkdir sys
```

---

