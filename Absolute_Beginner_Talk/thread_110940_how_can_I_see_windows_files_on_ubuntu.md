---
title: "how can I see windows files on ubuntu"
date: 2006-01-01
forum: Absolute Beginner Talk
---

### Post by yenisuvari on 2006-01-01
I have installed ubuntu. Now i can not see windows files on ubuntu. They are on the hda1. Should not they be in the mnt folder in ubuntu? I checked the mnt folder but i found nothing. What is wrong?

---

### Post by aysiu on 2006-01-01
See the fourth link of my sig.

---

### Post by randal on 2006-01-01
wait... I really want to help... but I'm not sure if this one would.
In other distros, windows partition is usually mounted by default to /mnt but based on my experience in Ubuntu, since I manually set partitions, you have to specify the mount point.

try:
mount --type vfat <device> <directory>

I don't know about the --type option but just check the man page for mount, I think you'll find something close to it.

There is, I think, another way to have your windows partition mounted. I'll assume you're with Gnome.

click on system, then to administration, then to some "disk manager" (If I remember correctly, it has a hard disk icon). You'll be asked about your root password. Go to tab where you'll see all the partitions in your system. There you can set the FAT32 mount point.

---

### Post by ubuntu_demon on 2006-01-01
I moved this thread from the hoary customization section.

So yenisuvari you are using hoary right ?

---

### Post by yenisuvari on 2006-01-01
Thank you very much for all replies.

---

