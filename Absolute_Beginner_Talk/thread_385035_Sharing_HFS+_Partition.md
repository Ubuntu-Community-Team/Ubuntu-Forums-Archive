---
title: "Sharing HFS+ Partition"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by poochy on 2007-03-15
I mounted my boot partition (HFS+) in the terminal but i have a permission problem. I changed the UId in Ubuntu but I do not know how to navigate to the files and folders from the terminal... is there a guide or something?

---

### Post by cyberdork33 on 2007-03-15
just google a basic linux commands page...
[http://www.reallylinux.com/docs/basic.shtml](http://www.reallylinux.com/docs/basic.shtml)

"ls" lists files in the current folder
"cd" changes directories.

I mount my OSX partition on a folder I created called /OSX, so when I open a terminal, I type the command:

```
cd /OSX
```

After I change directories, I list all the files and folders in in the directory by typing

```
ls
```

You will probably have issues with permissions on the files in your HFS+ filesystem because it uses similar methods to set permissions as in linux, and ubuntu reads teh permissions as set in the other OS.

---

