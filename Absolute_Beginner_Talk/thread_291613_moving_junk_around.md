---
title: "moving junk around"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by band-aid on 2006-11-02
Ok this is an extremely noobish question so I figured I'd better put it in here. I've got a bit of experience in linux so I'm not completely new but this whole gnome thing is throwing me for a loop in this one area. I've to my three hard drives mounted and am able to read files and stuff off of them. The problem is I want to be able to copy all the files from one folder into another folder using the GUI. I'm not able to get into anything root like in anything but the terminal so I cannot change the permissions of the files or copy them efficiently. I could sudo cp in the terminal but the file names can be quite long and complicated and I'm lazy. Thanks for the help.

---

### Post by PriceChild on 2006-11-02
You *could*:
```
gksudo nautilus
```
Please be careful with this and close it as soon as you're finished!

Don't move important system files etc.

---

### Post by llamakc on 2006-11-02
You can open Nautilus as root privileges with:

gksudo nautilus

---

### Post by band-aid on 2006-11-02
ok that worked well but I have another problem, the disks have been mounted as read only. Is there a way I can temporarily change them to read/write without remounting them?

---

### Post by CatKiller on 2006-11-02
> **band-aid said:**
> ok that worked well but I have another problem, the disks have been mounted as read only. Is there a way I can temporarily change them to read/write without remounting them?

It depends. If the filesystem is of a type that you can write to - anything but NTFS, largely - then you can use the **mount -o remount** option. I got that from **man mount**, and that will tell you more about how to use it.

---

### Post by band-aid on 2006-11-02
oh yea..... they are ntfs lol.
I completely forgot about that. sorry to have wasted your time...

---

