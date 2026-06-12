---
title: "Folder share between WinXP and Ubuntu?"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by feistyfirsttimer on 2007-06-12
Hi, I have just installed Feisty on my PC, it's now a dual-boot along with Windows XP.  I did the "standard" dual-boot installation - it automatically did the partitions so half my 20GB Hard Drive has XP and the other half Feisty.

I'd like to have a folder that both OSes could read - so I could, for instance, put my MP3 collection in it, and be able to listen to my sounds no matter which OS I'm working in.

Is it possible to set such a folder up now?  Or is it too late because I've already installled both OSes?  If it is possible - how do I do it, how do I access it, etc.

---

### Post by Inxsible on 2007-06-12
You can install ntfs-3g and read and write to those drives via Linux.
Go to Applications --> Add/Remove. Search for ntfs and install it. Then after installation, go to Applications--> System Tools --> NTFS Configuration Tool and enable read and write support for internal and external drives.


OR

You could also mount your Linux drive in Windows and give it a drive letter. You will need to install [FS-Driver]("http://www.fs-driver.org") in Windows to be able to access ext3 drives

---

