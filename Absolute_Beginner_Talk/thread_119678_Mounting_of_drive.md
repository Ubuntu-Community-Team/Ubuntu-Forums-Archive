---
title: "Mounting of drive"
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by kedarm on 2006-01-20
I installed UBUNTU on my comp a few days ago, and now have two OS (the other being Windows XP). However, I cannot access any of my Windows files while running UBUNTU, nor vice versa.
I've heard that we are to 'mount' the drive, but do not know how to go about doing it!

HELP!

---

### Post by dueY on 2006-01-20
```
sudo mkdir /media/windows 
```
```
sudo gedit /etc/fstab
```

Add ```
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
``` to the file.
But replace hda1 with wherever your Windows partition is.  This will make it so your Windows partition will be mounted everytime you run your Ubuntu.

---

### Post by Mustard on 2006-01-20
You can do those commands using the terminal, which is found in the Applications>>Accessories menu on your desktop.  It will ask you to enter your user password when you do the ones containging the 'sudo' command, as that is the 'superuser do' command for administrative tasks.

---

