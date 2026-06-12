---
title: "Noob Question"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by EminoX on 2007-06-05
Hello.

I've recently installed Ubuntu 7.04 Feisty Fawn on an old HDD.  I don't have internet connection and wanted to install a program that could play DVDs. I want to use a CD-RW disk to tranfer the files from this computer to the other HDD.  When i mount the CD i get three files

autorun.inf

udfrchk.exe

udfrinst.zl

What do these mean?  The files that i downloaded on to disk don't show up?

---

### Post by LaRoza on 2007-06-05
Are you sure you actually burned the files to the disk? Try reading the disk with another computer or OS.

-edit Didn't Feisty already have a file burning app?

---

### Post by jfinkels on 2007-06-05
> **EminoX said:**
> Hello.

I've recently installed Ubuntu 7.04 Feisty Fawn on an old HDD.  I don't have internet connection and wanted to install a program that could play DVDs. I want to use a CD-RW disk to tranfer the files from this computer to the other HDD.  When i mount the CD i get three files

autorun.inf

udfrchk.exe

udfrinst.zl

What do these mean?  The files that i downloaded on to disk don't show up?

Looks like the disc you tried to use to burn your own files already had files on them!

Make sure your disc is blank next time you try to burn something.

---

### Post by mikewhatever on 2007-06-05
Don't know what program you were trying to install, nor what those files are. For dvd playback, you  need the following packages installed:
[libdvdcss2]("http://medibuntu.sos-sts.com/repo/pool/feisty/free/i386/libdvdcss2_1.2.9-2medibuntu2+build1_i386.deb")
[libdvdread3]("http://mirrors.kernel.org/ubuntu/pool/universe/libd/libdvdread/libdvdread3_0.9.7-2ubuntu1_i386.deb")

---

### Post by EminoX on 2007-06-05
> **LaRoza said:**
> Are you sure you actually burned the files to the disk? Try reading the disk with another computer or OS.

The computer i'm on now can read the files that i saved to the disk.

They may be from the formating process.  I used Roxio Easy CD Creater 5 on the win xp O/S.

---

### Post by Crafty Kisses on 2007-06-07
> **mikewhatever said:**
> Don't know what program you were trying to install, nor what those files are. For dvd playback, you  need the following packages installed:
[libdvdcss2]("http://medibuntu.sos-sts.com/repo/pool/feisty/free/i386/libdvdcss2_1.2.9-2medibuntu2+build1_i386.deb")
[libdvdread3]("http://mirrors.kernel.org/ubuntu/pool/universe/libd/libdvdread/libdvdread3_0.9.7-2ubuntu1_i386.deb")

Those are the best ones, and if you want to burn DVD's you can use K3B.

---

### Post by Alterax on 2007-06-07
autorun.inf and an .exe file tips me off that the DVD program is for Windows, not Linux.  You may be able to run the .EXE file through wine, but I have severe doubts if this will be any good even if it does work (since the software MPEG-4 codec that the player would utilize would be pretty complex with lots of direct calls to the hardware.)  So if it does work on a Linux system, it will probably be very choppy.


The autorun.inf file is a Windows-specific information file that just tells the computer what to do when you put the disk in the drive if your Windows system has autorun enabled (BAD idea, since it's not difficult to remaster a Windows disk and change up the .inf to do all kinds of interesting/mean things.)

--Alterax

---

