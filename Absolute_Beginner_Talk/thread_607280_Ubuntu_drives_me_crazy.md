---
title: "Ubuntu drives me crazy"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by binzer on 2007-11-08
Hi,
Here is my grand problem I have been dealing with it full day. My ubuntu stops to boot after /etc/rc.local. It seems that there is something running in the background that stops the drive booting. I just tried to go around with "ctrl-c", rebooting, "init=/bin/bash", hardware test, etc... I threw all I have to bypass the problem. However, I can't!

I have some valuable data in the programme and need to fetch them before morning.

Plz throw your 2 cents on the solution. I hate to hear the word "Reinstall ubuntu" . I can't let my bloody files disappear.

Help, help, help....

---

### Post by Dr Small on 2007-11-08
If you need to get the files off, just bootup a livecd, copy your files, and try to fix the problem.
if all else fails, reinstall.

---

### Post by binzer on 2007-11-08
It seems my Pc failed to boot the ubuntu live cd . It fail to go beyond /etc/rc.local when I try to bootup the live cd.

More help........

---

### Post by Barge on 2007-11-08
No idea how to help you with the ubuntu install sorry, only new to this.

If you really need to get some files off though and either dual boot or have a windows box you can plug your hdd into, you can read the ext3 file system in windows and mount your linux drive with [Ext2 IFS for Windows]("http://www.fs-driver.org/") Its no permanent solution but may help for now.

---

### Post by spideygal on 2007-11-08
> **Barge said:**
> No idea how to help you with the ubuntu install sorry, only new to this.

If you really need to get some files off though and either dual boot or have a windows box you can plug your hdd into, you can read the ext3 file system in windows and mount your linux drive with [Ext2 IFS for Windows]("http://www.fs-driver.org/") Its no permanent solution but may help for now.

Nice tip, I am glad I was looking at this thread,I have been wondering how to access my Linux  files from Windows.

TIA


I copied the link and sent it to Gmail as I can acces that from both Windows and Ubuntu. LOL

---

### Post by Barge on 2007-11-08
Yep its software for Windows and will let you get access to your linux partition. You should be able to give it a drive letter in Drive Management, etc once you have it up and running. I've used it before, works well. 

It may not help the OP with their problem of course as they probably don't have a windows partition, but then again it might.

---

### Post by ByteJuggler on 2007-11-08
For rescue and recovery (if the Ubuntu LiveCD's dont work) I tend to use [TRK]("http://trinityhome.org/Home/index.php?wpid=1&front_id=12"). Very capable rescue and recovery CD.

---

### Post by dondad on 2007-11-08
Assuming that you are able to recover your data files, before you reinstall, set up a separate partition for your /home so that you can reinstall without losing your data the next time.

---

