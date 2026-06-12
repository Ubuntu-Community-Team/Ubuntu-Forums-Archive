---
title: "partitioner help"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by anxi3ty on 2008-01-31
I am trying to use a burned copy of: "hardy-dvd-i386.iso 29-Jan-2008 12:27  3.6G" from: "http://cdimage.ubuntu.com/dvd/current/" to install ubuntu to a 150 gig sata drive. The first time i tried to install it from the "Start or install Ubuntu" selection of the menu, but the default desktop resolution that it uses doesnt agree with my monitor for some reason. Well, no biggie Ill just use the text based install option I thought. That seemed to be working untill I got to the partitioner section of the install. I recognises both my sata#1 and #2 drives just fine. So i selected to use guided partitioning and selected the entire sata #2  drive, but when it starts to format the partitions it stops and says: "Failed to remove conflicting files. The installer needs to remove operating system files from the install target, but was unable to do so. The install cannot continue." I do not understand how a drive with no os and is 100% unallocated can have so called operating system files on it. Im stuck at that and cant figure it out.

---

### Post by dannyboy79 on 2008-01-31
if you're sure that the you had the drives right then the installer is getting confused. boot to the live cd, then check the hard drive's contents by looking at it through nautilus, it's a file browser. use gparted to recreate partitions or erase them if neccessary. then re try to install.

---

### Post by anxi3ty on 2008-01-31
Okay thanks, I'll try that. Im sure i have the rite drive because the other one is a 120 gig and that has xp pro installed on it. I even checked the 150 in disk management from windows to make sure the drive was 100% unallocated.

---

### Post by anxi3ty on 2008-01-31
The live cd freezes on me bout 30 seconds after the desktop comes up. So i tried to just rebooting and disconecting the primary sata hd which seemed to fix the partitioning error. Now the install steps "Select and install software" and "Build LTSP chroot" both fail. I guess it just wasnt meant to be. Oh well.

---

