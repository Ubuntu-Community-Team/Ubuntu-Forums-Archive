---
title: "How do I CD to a directory on a second drive?"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by OldDog11 on 2008-03-23
I am trying to use the cd command to change to a directory on a second mounted drive but I cannot see how to do this. Is it possible to do this and if so how?

---

### Post by GMachine_24 on 2008-03-23
Assuming the mount point of the second drive is called "beta" you would:

>cd /beta/directoryname

---

### Post by TeoBigusGeekus on 2008-03-23
Go to /media with Nautilus and see the name of your drive, say BACKUP.
Then just type in a terminal
```
cd /media/BACKUP/yourfolder
```

---

### Post by Dennis on 2008-03-23
Assuming you know the name of the drive for example - hda1, hda2, sda1, sda2 or whatever
cd /media/drivename

Edit: Too slow again :)

---

### Post by OldDog11 on 2008-03-23
My drive is called mymedia and the directory I am trying to change to is called Backup. I must still be doing something wrong because I keep getting the message saying No such file or directory.

I type the following: cd /media/mymedia/Backup
I have also tried cd /mymedia/Backup

Where am I going wrong?

---

### Post by aktiwers on 2008-03-23
Type "cd" and drag/drop the drive into the Terminal.

---

### Post by mikewhatever on 2008-03-23
Lets see what the mount points in /media are, <ls /media>.

---

### Post by TeoBigusGeekus on 2008-03-23
Are the names in the correct case?

cd /media/mymedia/Backup

is different from

cd /media/MyMedia/backup

and different from

cd /media/myMedia/backUp

and so on...

(Linux is case sensitive)

---

### Post by OldDog11 on 2008-03-23
I have been careful to get the upper and lower case correct. My volume is called mymedia and the mount point is media/mymedia, if that helps at all.

---

### Post by TeoBigusGeekus on 2008-03-23
Can you at least go to mymedia?
```
cd /media/mymedia
```

---

### Post by wolfen69 on 2008-03-23
```
cd /media/sda1
```
assuming that drive is sda1

do```
fdisk -l
``` to find out what drives are sda1, etc.

---

### Post by OldDog11 on 2008-03-23
Getting somewhere now! I have put in cd /media/mymedia and I have changed to this drive.

ls lists the directories on that drive but I still cannot get into ant of them.

---

### Post by OldDog11 on 2008-03-23
Finally sorted it out - thanks for all of your help!!

---

### Post by wolfen69 on 2008-03-23
.

---

