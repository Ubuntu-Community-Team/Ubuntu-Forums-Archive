---
title: "dual boot ubuntu and windows"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by kachelle on 2006-10-04
When I boot up my computer, i want the option of either choosing windows xp or ubuntu. However, when I select Windows xp I get the following message:
---------------------------------------------------------
Booting ‘Microsoft Windows XP Professional’

Root (hd0,0)
Filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1
---------------------------------------------------------

How do i go about correcting this issue? i can open window files from within the Ubuntu; so i know the operating system is still there. Please give me step by step a i am trying to familarize myself with the commands.

---

### Post by anaconda on 2006-10-04
You are supposed to use 
Rootnoverify (hd0,0)
instead of
Root (hd0,0)

With the Rootnoverify grub doesn't try to "open" the filesystem, which it cant do with ntfs partitions anyway.. And it doesn't need to "open" it when you are using chainloader..eg. giving the control to windows boot loader..

having said this I know many people, who succesfully use the Root -option to load windows.

---

### Post by glenduncanscott on 2006-10-04
Don't know if this is any help to you, but I've found it's bailed me out a few times locating Windows XP. Check out [Graphical Boot Manager]("http://gag.sourceforge.net/"), very easy to use. You can also find this GAG and other useful apps on [Ultimate Boot CD]("http://www.ultimatebootcd.com/") :)

---

