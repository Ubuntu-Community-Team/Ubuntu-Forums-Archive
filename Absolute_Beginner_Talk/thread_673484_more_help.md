---
title: "more help"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by CarRamrod on 2008-01-20
I have the computer booted as a liveCD.   when i try to look in my harddrive is says  "Cannot mount volume"    what does that mean?

---

### Post by JoshuaRL on 2008-01-20
The Live CD has it's own file system mounted through the CD.  There are options to mount the HD to the Live CD, but usually you only try that as an option to fix a broken system because it involves work from the terminal.  What exactly are you trying to do?

---

### Post by CarRamrod on 2008-01-20
Some how a system registry file was deleted on my laptop and now windows wont load. I got advise to get Ubuntu and run is as a liveCD and then i can retrieve my files i need for school. The thing is i have never used a linux OS.  So im not exactly sure what im doing.   Any help would be much appreciated.

---

### Post by banewman on 2008-01-20
What is the command you are using?
sudo mount /path/to/file
is what you're after - where /path/to/file is where the partition is in the file system
e.g. sudo mount /dev/sda1
If it is a ntfs windows partition then you'll need the program - ntfs-3g - from synaptic that you can download while using the live cd.
:)

---

### Post by frup on 2008-01-20
Are you using the latest Ubuntu 7.10 CD or an older cd?

---

### Post by Scarath on 2008-01-20
> **CarRamrod said:**
> Some how a system registry file was deleted on my laptop and now windows wont load. I got advise to get Ubuntu and run is as a liveCD and then i can retrieve my files i need for school. The thing is i have never used a linux OS.  So im not exactly sure what im doing.   Any help would be much appreciated.

this happened to me a while back when i was playing with debian, i left my computer to go eat a sandwich, got back, turned it on and XP worked, wierd eh? 

dont panic, there are plenty of ways to fix ur windows install with ur install disk (i only know this  about XP btw), just google it, lots of HOWTOs out there :D

---

### Post by CarRamrod on 2008-01-20
yea im doing that now

---

