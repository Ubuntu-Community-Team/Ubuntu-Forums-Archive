---
title: "Grub Error 22"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by Aspra on 2007-11-27
I am dual booting windows and Ubuntu and I deleted my Ubuntu  partition and swap partition within windows. But grub still comes up and has a error 22 and it wont do anything.I cant go to windows. Its no big deal if i cant fix it besides reinstalling everything but id like to know if i can anyway. If i did something stupid my bad, but i didn't have anything important on the computer so its no big deal just would like to know how to fix it without having to reinstall windows.

 Thanks.

---

### Post by angryfirelord on 2007-11-27
GRUB requires a menu.lst file. Since you deleted your Ubuntu partitions, you deleted that file, so GRUB doesn't know what to do.

If you have a Windows XP disc, you can boot into the recovery console and type **fixmbr** so you can boot into Windows again.

---

### Post by candtalan on 2007-11-27
It sounds like you had installed using wubi inside windows? Anyway I think the boot manager becomes grub if I understand it correctly. All that has happened I think is that the master boot record (MBR) has been changed from what windows expects to a dual boot, controlled by the linux files now deleted. All you will need to do is run a windows command such as mbrfix (you will need to check this exactly) and windows boot conditions will reset to their normal file.
Maybe use google to find more detail information?

---

### Post by Aspra on 2007-11-27
I installed Ubuntu normally. I just deleted the partition that Ubuntu is on from the disk manager. Needed to do something 7.10 was horrible screen was screwed up. ( I have a HP ze5500 laptop.) so i wanted to start clean. thanks for your help hope i don't mess it up anymore. Im guessing I type this in the command?

---

### Post by limac on 2007-11-27
grub error 22 pops up when there is no operating system installed in your computer.

---

### Post by Aspra on 2007-11-27
I googled it and this came up [http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)

So all i have to do is type fixmbr?

---

### Post by meierfra on 2007-11-27
Yes, if you have a Windows CD. Check out this link

[http://ubuntuforums.org/showthread.php?t=616540#2]("http://ubuntuforums.org/showthread.php?t=616540#2")

---

### Post by Aspra on 2007-11-27
All fixed. thanks guys.

---

