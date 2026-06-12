---
title: "how to delete sources.list ?"
date: 2005-10-03
forum: Absolute Beginner Talk
---

### Post by tr6scott on 2005-10-03
I buggered up my sources.list file with the backports that are off line... I made a backup but I can't delete the file to rename the old one...

---

### Post by matthew on 2005-10-03
sudo rm /etc/apt/sources.list
sudo cp /etc/apt/sources.listbackup /etc/apt/sources.list

---

### Post by Mustard on 2005-10-03
For the layperson, the above commands are doing this;

sudo rm /etc/apt/sources.list 
(as a sudo(supersuser) remove the file sources.list from the directory /etc/apt/)

sudo cp /etc/apt/sources.listbackup /etc/apt/sources.list
(as a sudo(supersuser) copy the file in /etc/apt/ called soures.listbackup and create a copy of that file in /etc/apt/ called sources.list)

Your problem was one of permissions and file ownership.  All files in linux have permissions and are owned by a user of some kind.  Because you didn't have permission to edit the sources.list file as a normal user, you needed to do so as a superuser (who has a greater degree of freedom with regards to what they have permisssion to change)

---

