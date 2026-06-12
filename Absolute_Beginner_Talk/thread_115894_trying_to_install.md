---
title: "trying to install"
date: 2006-01-11
forum: Absolute Beginner Talk
---

### Post by kenny_munroe on 2006-01-11
i'm having problems installing version 5.10 .. computer is a pentium 11 350 it's partitioned with win98 on C and win2000 on E .. how do i install over the win2000

---

### Post by hillbilly on 2006-01-11
I assume that you want to remove win2k and install ubuntu in that free space !!
Pop in the installation cd, and proceed as directed. when you reach the partitioning phase of installation, select manual partitioning and then delete the partition contaiing win2k and either automatically partition or do a manual parition. (Since you already have two OS running on your system, i guess you do know the partitioning principles.)

---

### Post by manicka on 2006-01-11
You'll need to do an expert installation (manual partitioning) and delete the Windows 2000 partition with the installers partitioner, then create partitions for Ubuntu in that space.

You'll find Ubuntu very slow on that machine. I'd suggest a xubuntu install as an alternative.

[https://wiki.ubuntu.com/InstallingXubuntu](https://wiki.ubuntu.com/InstallingXubuntu)

Remember to backup anything vital :)

---

### Post by kenny_munroe on 2006-01-11
i have the ubuntu 5.10 disk ...but when i boot the computer the CD doesn't start..

---

### Post by hillbilly on 2006-01-11
[QUOTE=kenny_munroe]i have the ubuntu 5.10 disk ...but when i boot the computer the CD doesn't start..[/QUOTE]

Is your BIOS set to boot from CD first and then the hard disk ?

---

### Post by kenny_munroe on 2006-01-11
ok....what are the steps in doing that

---

### Post by manicka on 2006-01-11
It varies depending on your bios. On my machine you hole down the 'de'l key at startup, others you hold down f2. It normally tells you how do it at the initial boot screen.

Once in the bios look for the section where you can alter the boot device order. Change it to something like cdrom,floppy,hardrive

---

