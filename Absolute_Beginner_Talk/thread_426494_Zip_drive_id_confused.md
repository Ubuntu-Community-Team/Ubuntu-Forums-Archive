---
title: "Zip drive id confused"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by olddoser on 2007-04-28
In fstab internal zip drive is hdd when I try to mount the drive "hdd4 doesn't exist".
How come two different id  hdd and hdd4?

Maybe the drive is smoked and everyone (including me) is getting confused.

Ideas?:confused:

---

### Post by olddoser on 2007-04-29
bump....any ideas

---

### Post by olddoser on 2007-04-30
bump....again

---

### Post by mikeyphi on 2007-04-30
I think maybe the fstab should read hdd4...however this guide may shed some light on the problem:

[https://help.ubuntu.com/community/IomegaZIPDrive?highlight=%28drive%29%7C%28zip%29](https://help.ubuntu.com/community/IomegaZIPDrive?highlight=%28drive%29%7C%28zip%29)

---

### Post by olddoser on 2007-04-30
Thanks Mike
Sorry to many things to do.
Changing fstab to read hdd4 did not fix the problem but did give me only 2 floppy icons in the tray (should only be 2)  Still working with the guide you suggested, ajdusting for Dapper Gnome. 
Thanks for the response.

---

### Post by olddoser on 2007-04-30
Just to update the problem seems to be with the disk mounting icons in the tray as I can mount the internal zip drive in terminal, read, and eject.  Have not tried to write yet.  Next question is where does the info come from for the disk mount icons in the tray?  Can't be fstab as it is correct.

anyone ?    Thanks

---

### Post by spur on 2007-04-30
What does your fstab read? You need a mount point as well and may have to create something like /media/zip and then in fstab direct hdd4 to it.
I am about to fix this on my 7.04 amd64 system and will post how I do it for you. I have fixed this before on a few linux systems so am pretty confident of a positive outcome.[img]http://yelims4.free.fr/Ordinateur/Ordinateur07.gif[/img]

---

### Post by spur on 2007-04-30
First you need to 
> sudo nautilus if you want to access every thing you need through a graphical interface.
Go to /etc and find  'fstab' open it to edit (click twice).
add a line thet reads > /dev/hdd        /media/zip      auto    rw,user,noauto    0       0 then
go to /media and add a folder called zip and change the permissions to allow users to read and write..
This should give you read write and an icon for the zip. If you have a windows formated zip you will need to change the hdd to hdd4 as the windows partitioning of the disk puts all the files on the fourth partition. 
:lolflag:

---

### Post by olddoser on 2007-05-01
Thanks Spur  Will give this a try.  Being able to mount zipdrive in terminal I can live with until I can do as you say and get it to play nice.
Thanks again

---

### Post by spur on 2007-05-01
No worries, I have worked mine out on 7.04 and have two zips mounting well on hdd for ex2 formatted zips and hdd4 for fat formatted. For the fat formatted use vfat instead of auto in the line in fstab. ( I forgot that bit before). If you use fat32  or auto it will say it doesn't recognize it.

---

