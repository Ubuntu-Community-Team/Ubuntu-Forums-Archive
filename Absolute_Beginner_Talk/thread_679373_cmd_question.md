---
title: "cmd question"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by antisocialist on 2008-01-26
ok i have a question about one of the forbidden commands

DO NOT RUN THIS COMMAND!!!!!!!!!!!!!
sudo rm -rf /dir/to/dir/ will completely delete everything on the selected space with sudo rights, and reformat it to ext3 right? i have a 1tb xternal formatted to ntfs and want it on ext3 so will that command work to do it?

---

### Post by Rocket2DMn on 2008-01-26
If you want to reformat a drive you should be using GParted.  You can't change the filesystem type on a drive by using the rm command anyway.  You can use GParted from the live cd or install it to Ubuntu with
```
sudo apt-get install gparted
```
You just can't modify your mounted partitions, so you can download and use GParted to mess with external hard drives just fine.

The reason we say not to use the "sudo rm -r" command is because people sometimes blindly follow directions and that command is extremely dangerous when not used correctly since it will delete EVERYTHING.

---

### Post by st33med on 2008-01-26
It will not reformat the drive, but it will wipe off everything. For that, you need Gparted:
```
sudo apt-get install gparted
```

---

### Post by nick_h on 2008-01-27
To put a filesystem on a drive you can use the *mkfs* command.

For the manual page, type:
```
man mkfs
```

---

