---
title: "Tar syntax"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2006-08-20
Hi the following is suppose to backup my system, but when I hit enter, the terminal just gives me a new line and does nothing. 

Basically, i need to backup everything accept 2 folders, windrives and stuff and both are in root, and I want the file created in /stuff. 

Could some one please tell me what I'm dong wrong?

> tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/stuff --exclude=/mnt --exclude=/sys --exclude=/windrives /stuff

---

### Post by matthew on 2006-08-20
You were really close. Somewhere along the line the syntax changed. You need to put the file to create and it's location first, then what you want archived last after the exclusions like this:
```
tar cvpzf /stuff/backup.tgz --exclude=/foo /
```Also, if you are archiving things stored in places other than your /home folder you will need to be root, so for your specific example this should work.```
sudo tar cvpzf /stuff/backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/stuff --exclude=/mnt --exclude=/sys --exclude=/windrives /
```I also like to append a date on mine so I would call the file /stuff/backup20060820.tgz, but that's personal preference.

---

### Post by matthew on 2006-08-20
You were really close. Somewhere along the line the syntax changed. You need to put the file to create and it's location first, then what you want archived last after the exclusions like this:
```
tar cvpzf /stuff/backup.tgz --exclude=/foo /
```Also, if you are archiving things stored in places other than your /home folder you will need to be root, so for your specific example this should work.```
sudo tar cvpzf /stuff/backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/stuff --exclude=/mnt --exclude=/sys --exclude=/windrives /
```I also like to append a date on mine so I would call the file /stuff/backup20060820.tgz, but that's personal preference.

---

### Post by RudolfMDLT on 2006-08-20
:) Thank  you ! Appreciate it!

---

