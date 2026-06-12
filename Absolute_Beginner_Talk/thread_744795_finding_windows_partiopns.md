---
title: "finding windows partiopns"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by articwolf939 on 2008-04-03
ok i just reinstalled ubuntu and i have a media drive that keeps all my music and videos on it so i can get to if from windows and ubuntu and normaly when i just start ubuntu it shows me my c: drive and my media drive but i cant figgure out why or how to find them cos it not showing them any idea? 

im using 7.10 ubuntu

---

### Post by Hobo Joe on 2008-04-03
In the 'Places' menu, there should be something like 'sda1' or 'hda1', the number depends on what partition Windows is installed on. From there you can access all your Windows files.

If it's not there, go to /media, and check all the drives/partitions that it shows in there.

---

### Post by articwolf939 on 2008-04-03
no i cant find it any other help fun advice i looked though places and i can find what ur talking about

---

### Post by Hobo Joe on 2008-04-03
I can't tell you exactly how to get there right now, becuase I'm not at my computer, so I'm just going from memory here.

Open the file browser, and it should have some shortcuts. One of them should be called '/', or 'root'. Navigate to that, and once there, find a file called 'media'. This will give you a list of all the drives/partitions on your computer.

---

### Post by sideburns on 2008-04-04
Try this: open your Home folder, then click on Filesystem.  This will get you to your root directory.  In there you may well see a folder named DRIVE_C, or something like that.  If you gave your C: drive a label in Windows, it will probably be named for that.  I had the same question after my sister installed Ubuntu on her Win2K box as a dual boot, and that's where it turned out to be.  HTH, HAND.

---

