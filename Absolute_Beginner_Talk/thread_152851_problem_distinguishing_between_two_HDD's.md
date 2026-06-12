---
title: "problem distinguishing between two HDD's"
date: 2006-03-30
forum: Absolute Beginner Talk
---

### Post by spotdart on 2006-03-30
hey this is a pretty basic problem but it has caused me no end of trouble. I am running a system with two SATA hard drives (the other specs. are really irrelevant.) the probelm I run into is that I have one hard rive with windows on it, and the other is totally blank. obviously I want to create a partition on the hard drive I'm not using for windows. this is where I run into a problem, the hard drives are identical, in that they are both made by maxtor and have the same serial numbers, and since they're SATA I can't distinguish bettween master and slave. so when I;m asked which one to format both of them are exactly the same, and I can't tell which one I want to keep, or the one I want to  create the partition on, there is probobally a really simple solution to it, but I can;t find out what it is.](*,)

---

### Post by dcstar on 2006-03-30
> **spotdart]hey this is a pretty basic problem but it has caused me no end of trouble. I am running a system with two SATA hard drives (the other specs. are really irrelevant.) the probelm I run into is that I have one hard rive with windows on it, and the other is totally blank. obviously I want to create a partition on the hard drive I'm not using for windows. this is where I run into a problem, the hard drives are identical, in that they are both made by maxtor and have the same serial numbers, and since they're SATA I can't distinguish bettween master and slave. so when I said:**
> (*,)
Are you trying to create a partition on an already running Ubuntu system, or during install?

If the system already exists, go to:

System-Administration-Disks and you can select the disks and view what partitions are already on each of them to identify the correct one.

---

### Post by spotdart on 2006-03-30
I'm trying to create it during install, I don;t already have a ubuntu system running. I need a way to from windows or during the install to tell the difference bettween the two drives which I can't do right now because they both have the same name.

---

### Post by dcstar on 2006-03-30
[QUOTE=spotdart]I'm trying to create it during install, I don;t already have a ubuntu system running. I need a way to from windows or during the install to tell the difference bettween the two drives which I can't do right now because they both have the same name.[/QUOTE]
If you want to feel safer, disable your Windows drive in you BIOS (if you can), otherwise the "Expert" installation mode in Ubuntu may allow you to look at the existing partitions so you can then pick the right disk for install (not 100% sure on this).

---

