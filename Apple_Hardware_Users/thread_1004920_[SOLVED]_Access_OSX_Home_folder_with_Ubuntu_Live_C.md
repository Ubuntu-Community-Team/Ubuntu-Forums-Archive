---
title: "[SOLVED] Access OSX Home folder with Ubuntu Live CD"
date: 2008-12-07
forum: Apple Hardware Users
---

### Post by Ricardobrusd on 2008-12-07
Hi,
I am trying to backup to DVD some files in a problematic OSX partition using a Ubuntu Live CD (7.10 Gutsy Gibbon), however I cannot access my home folder.

My OSX partition is HFS+ Journaled, and I can`t modify any files. Also, I cannot access OSX or install Ubuntu. 

I saw some threads about creating a UID that matches the OSX`s User ID , but I don`t know if it`s possible using a Live CD and is not clear to me how it should be done.

If it`s not possible to access this files, can Gparted copy my entire partition to a external hard drive? Will those files be accessible in OSX ?

Thanks for the attention (and sorry for any grammatical error )

---

### Post by cyberdork33 on 2008-12-07
the files in your home folder are "owned" by a different user than the Ubuntu LiveCD user. Therefore, the permissions on the files do not allow that other users access. 

You can start a root nautilus window to access the files:
```
sudo nautilus
```

---

### Post by Ricardobrusd on 2008-12-07
> **cyberdork33 said:**
> the files in your home folder are "owned" by a different user than the Ubuntu LiveCD user. Therefore, the permissions on the files do not allow that other users access. 

You can start a root nautilus window to access the files:
```
sudo nautilus
```
I've alredy tried the "sudo nautilus", but I can't access my OSX partition within it. The partition is mounted on my desktop, but doesn't apear on nautilus.

Am I supposed to mount the partition again?

---

### Post by Ricardobrusd on 2008-12-08
Let me clarify what I meant. 

I am able to mount my Macintosh HD, my iPod and my external dvd drive on my desktop and on the file browser.

But when I use the command "sudo nautilus", I cannot "see" or mount any of those volumes within the file browser window, even if they are mounted on the desktop.

I'm not very experienced with Ubuntu, so I might be misunderstanding something.

Help would be greatly appreciated ( and is urgently needed :lolflag: )

---

### Post by lovelyvik293 on 2008-12-08
The ubuntu can not access the HFS+ volume.For the HFS+ you need a ubuntu package named as HFS plus.

---

### Post by tiresia on 2008-12-08
The HFS+ package shoul be already present in the LiveCD.
Your MacOSX HD should be mounted in /media
It should be /media/disk or /media/disk1 according to your partition map
Just check if you see it with ```
ls /media/disk
```
What do you want to do? Do you want to back up some files?

---

### Post by cyberdork33 on 2008-12-08
> **Ricardobrusd said:**
> Let me clarify what I meant. 

I am able to mount my Macintosh HD, my iPod and my external dvd drive on my desktop and on the file browser.

But when I use the command "sudo nautilus", I cannot "see" or mount any of those volumes within the file browser window, even if they are mounted on the desktop.

I'm not very experienced with Ubuntu, so I might be misunderstanding something.

Help would be greatly appreciated ( and is urgently needed :lolflag: )

Mounted drives are mounted in /media so you have to navigate to /media in your root nautilus window. Also, note that you will likely need to open two root nautilus windows one for the source and one for the destination.

> **lovelyvik293 said:**
> The ubuntu can not access the HFS+ volume.For the HFS+ you need a ubuntu package named as HFS plus.
hfs+ access is enabled by default in Ubuntu.

---

### Post by aysiu on 2008-12-08
In a live CD environment, it may not matter much, but you should get in the habit of using *gksudo* (and not *sudo*) for graphical applications. The proper command is ```
gksudo nautilus
``` Even if you mount the drive and locate it in /media, you will not be able to modify files, even as root. Linux is not, as far as I know (and I've done extensive Googling on this topic) able to write successfully to HFS+.

You will, however, be able to deal with the files on a read-only basis and should be able to copy them to an external drive and then burn them to DVD on another computer.

---

### Post by cyberdork33 on 2008-12-08
> **aysiu said:**
> in a live cd environment, it may not matter much, but you should get in the habit of using *gksudo* (and not *sudo*) for graphical applications. The proper command is ```
gksudo nautilus
``` even if you mount the drive and locate it in /media, you will not be able to modify files, even as root. Linux is not, as far as i know (and i've done extensive googling on this topic) able to write successfully to hfs+.

You will, however, be able to deal with the files on a read-only basis and should be able to copy them to an external drive and then burn them to dvd on another computer.

+1, but it is that it cannot write to *journaled* hfs+ partitions which this poster is likely dealing with.

---

### Post by tiresia on 2008-12-08
> **aysiu said:**
>  Even if you mount the drive and locate it in /media, you will not be able to modify files, even as root. Linux is not, as far as I know (and I've done extensive Googling on this topic) able to write successfully to HFS+.

Actually Linux can write on HFS+ but not on HFS+ Journaled. You can disable Journaling from inside MacOSX.
In Linux (with parted) you are able to shrink a HFS+ Volume, but you can't generate a HFS+ File System.

---

### Post by cyberdork33 on 2008-12-08
> **tiresia said:**
> Actually Linux can write on HFS+ but not on HFS+ Journaled. You can disable Journaling from inside MacOSX..

:) i edited my post

---

### Post by pxwpxw on 2008-12-08
I ckecked and found that for unjournalled hfsplus, I had to manually mount it on /mnt  then it was writeable, but not when automounted on /media.

---

### Post by tiresia on 2008-12-08
> **pxwpxw said:**
> I ckecked and found that for unjournalled hfsplus, I had to manually mount it on /mnt  then it was writeable, but not when automounted on /media.
This is strange. I can do it, from a Terminal and starting Nautilus as root.

---

### Post by Ricardobrusd on 2008-12-09
I finally could access my files ! I`m so relieved. :cool:

Thank you so much for the help.

---

### Post by tiresia on 2008-12-09
Great! Please, mark this thread as solved.

---

