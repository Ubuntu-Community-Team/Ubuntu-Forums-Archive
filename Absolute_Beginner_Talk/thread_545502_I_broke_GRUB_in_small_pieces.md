---
title: "I broke GRUB in small pieces"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-09-07
I have 2 hard drives. Both linux, Master is Feisty, Slave is Dapper. I wanted to swap primary  Slave for a Windows disk.

Read two post (see work by LHA)

[http://ubuntuforums.org/showthread.php?t=179902&highlight=grub](http://ubuntuforums.org/showthread.php?t=179902&highlight=grub)
[http://ubuntuforums.org/showthread.php?t=275728&highlight=grub](http://ubuntuforums.org/showthread.php?t=275728&highlight=grub)

and added the section about Windows:

cd /boot/grub
sudo cp menu.lst menu.lst_backup
sudo gedit menu.lst

title           Windows
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

I tried to reboot only disk that showed up was Windows and it wouldn't boot. Went to livecd, edited grub to remove above section. Tried to reboot. Now only the grub menu comes up, It could be edited, but I don't know what belongs there.

Meanwhile, the menu.lst file shows NO sda only sdb devices. HELP!

---

### Post by jamvegan on 2007-09-08
What is the current contents of your menu.lst, and what is the output of the following?
```
sudo fdisk -l
```

Also, just to make sure that I'm understanding correctly: when you try to boot you get the normal looking GRUB menu, with one or more operating systems listed, but they will not boot?

---

