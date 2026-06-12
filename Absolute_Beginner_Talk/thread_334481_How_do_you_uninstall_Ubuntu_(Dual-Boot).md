---
title: "How do you uninstall Ubuntu? (Dual-Boot)"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by VoXoM on 2007-01-09
Tried it out. All the wireless problems aren't for me. Don't like it. How do you remove it?

---

### Post by scrooge_74 on 2007-01-09
Did you try this? [https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

For removing Ubuntu just use your XP CD to remake the MBR and then you can fdisk the partition in which you have ubuntu so you can reformat it and use it in XP

Sorry to hear you are leaving

---

### Post by VoXoM on 2007-01-09
> **scrooge_74 said:**
> Did you try this? [https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

For removing Ubuntu just use your XP CD to remake the MBR and then you can fdisk the partition in which you have ubuntu so you can reformat it and use it in XP

Sorry to hear you are leaving

I just don't have the time to spend hours trying to fix simple things. Linux just isn't for me. Also, care to explain a little more about how to do? Will I be able to keep my data?

---

### Post by scrooge_74 on 2007-01-09
First question: where is your data?

If you use your XP CD it will only erase the master boot record and eliminate grub which is the program that let you dual boot.  That way your XP install wont be affected, since I doubt you want to reinstall XP.

When you have XP running solo you can then if I remember well use the XP CD to fdisk the partition where ubuntu is sitting and convert it back to NTFS of FAT32, that way it will seem you have to drives installed in your PC after you are finish

---

