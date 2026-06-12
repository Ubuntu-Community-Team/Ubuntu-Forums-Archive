---
title: "permission help"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by rburkartjo on 2008-02-09
i have no idea how to do
i need to delete some files from my weekly backups. it backs up my home folder once a day i am using home user backup

when i try to delete some i get the message
can not move var/backup to trash because you do not have permission to change it or its parent folders.

---

### Post by overdrank on 2008-02-09
> **rburkartjo said:**
> i have no idea how to do
i need to delete some files from my weekly backups. it backs up my home folder once a day i am using home user backup

when i try to delete some i get the message
can not move var/backup to trash because you do not have permission to change it or its parent folders.

HI and have you tried the command ```
gksudo nautilus
``` you can use the alt, F2 keys to use this command. This should give you the permission.

---

### Post by rburkartjo on 2008-02-09
yea tried but no luck

---

### Post by fenian on 2008-02-09
> WARNING THE RESULTS OF THE FOLLOWING ARE IRREVERSABLE 

If you want to totally delete (as in gone forever never coming back) /var/backup you can run this command...
> 
sudo rm -R  /var/backup

like I said be careful to type the correct path so you dont delete any directories you need.

---

### Post by rburkartjo on 2008-02-09
i dont want to delete the all of var/backup just some of the files in that folder 
is there a way of doing it with sudo rm

---

