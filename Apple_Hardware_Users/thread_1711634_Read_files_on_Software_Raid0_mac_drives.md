---
title: "Read files on Software Raid0 mac drives"
date: 2011-03-21
forum: Apple Hardware Users
---

### Post by hotwheelharry on 2011-03-21
I have a set of Mac software RAID 0 drives that my friend gave me for spring break. I need to access a file on the drive in the Extra folder on one of the drives. It contains some startup settings that need to be changed before I can boot it properly. I loaded up ubuntu and tried to access the drive but only the top level files are readable and when I try to access the Extra folder it says "permission denied." The info on the folder permissions tab is User ID: 501 and Group ID: dialout. Owner permissions = r/w, all other groups/users = none. How can I make Ubuntu read/write to this Extra folder? 

Can I remount with new permissions or something? It seems like a simple problem to solve.

---

### Post by hotwheelharry on 2011-03-21
I solved my problem.

sudo nautilus
#can access the files

sudo chmod -R 777 Extra
#makes the permissions right

touch Extra


Done!
Now I can read/write the files on each drive.

---

