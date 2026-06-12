---
title: "Low Disk Space"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by badhabit on 2008-04-14
The problem I had is I didn't allocate enough space when I installed Ubuntu. I'm running Windows Xp inside VirtualBox. Gotta love that program for those of us who are just changing over.Anyway here's the problem I had. It was showing I had low disk space even though I had 171 GB of free space on the drive. What I did was make a folder on the drive where I have tons of free space. Then I copied the folder named .VirtualBox over to the new folder. Once you get it copied over you can delete the one in the home folder. That will free up lots of space. Then you will have to open VirtualBox up and click file/Virtual Disk Manager. Once you get that open click Add. It will open up a menu. Go to the folder you made and copied over the .VirtualBox folder. Open it, go to the VDI folder and right click on your .vdi file. Mine is named Win Xp.vid Now chose properties and copy the Location link. Mine is /host/Linux Programs/.VirtualBox/VDI. Go back to the select a hard disk inage file and paste it in the look in box. It should bring up the image(s) Click on the one you want to add and click open. Now just follow the instructions on adding a new Image. Once you get to the Virtual Hard Disk part of it us Existing! Chose the one you want to use and it should work just fine. Before you delete anything make sure it will work from the new location though. I hope this was helpful. I could have used it but with a bit of head scratching I figured it out.
BH

---

### Post by estaticd on 2008-04-14
Or you could use gparted to free up some space and jostle around partitions.  :)

---

### Post by badhabit on 2008-04-16
I know about the Q-parted but this way works as well. Took me a few minutes the first time but, after the first time it takes less than one min to do. In the end same results too.

---

