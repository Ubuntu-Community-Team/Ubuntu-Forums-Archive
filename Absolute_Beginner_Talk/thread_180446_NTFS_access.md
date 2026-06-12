---
title: "NTFS access"
date: 2006-05-22
forum: Absolute Beginner Talk
---

### Post by the gnome on 2006-05-22
Hi,

I just installed Breezy 5.10 and mostly everything seems to be working fine.  In my current set up I have my old WinXP installed on the primary master HDD and Ubuntu as the primary slave (both on the same cable using the primary slot).

Right now all Ubuntu "sees" is my second hard drive with the ubuntu install.  I'd like to ween myself completely off windows so I'd like to access my files on the primary drive.

How can I do this?

---

### Post by xtacocorex on 2006-05-22
Try this wiki: [https://wiki.ubuntu.com/MountNtfsOnBoot?highlight=%28ntfs%29](https://wiki.ubuntu.com/MountNtfsOnBoot?highlight=%28ntfs%29)

Edited for bad grammar on my part

---

### Post by frodon on 2006-05-22
Here you will find how to mount your NTFS/FAT32 partitions : [http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

---

### Post by Ecthelion on 2006-05-22
If you want to read from your ntfs you just have to change a line in fstab:
```
sudo gedit /etc/fstab
```

Then change the line about your ntfs into:
DONT CHANGE /dev/hd**, leave that like it is in your fstab

> /dev/hda1       /media/windows     ntfs nls=utf8,umask=0222 0 0

If you don't want your ntfs mounted as windows, don't copy /media/windows either

If you do want your NTFS mounted as windows, then you have to save your fstab and do this:
```
sudo mkdir /media/windows 
```

Then do 
```
sudo mount -a
```

And then you can go and browse your NTFS. You can't write to it this way.
To write you have to put in anothr line, I don't know which, but remeber:
WRITING TO NTFS ISN'T 100% SAVE

That's of course a warning, you can do it and in most cases there's no problem but still be warned

PS. If you still can't browse your NTFS after you did this, just restart your pc... that should do the trick

EDIT: I'm too slow, 2 answers before mine *sigh*

---

### Post by the gnome on 2006-05-22
Thanks all, I'll definitely be giving those a whirl!

---

