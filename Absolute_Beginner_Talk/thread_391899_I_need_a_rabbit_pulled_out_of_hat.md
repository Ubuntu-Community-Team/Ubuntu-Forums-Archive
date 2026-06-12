---
title: "I need a rabbit pulled out of hat"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by J11Gyro on 2007-03-23
Uninstalled VMWare but virtual machines remain and I cannot delete them. How do I get permission to delete the sys files for vmware that I found in search? 116 files using 18.9gig of space I cannot use. Other things are starting to be effected now, I guess because mem allocation and so forth.

---

### Post by raja on 2007-03-23
What do you mean by the sys files. The virtual machines itself can just be deleted without any problems.

---

### Post by J11Gyro on 2007-03-23
Every VMware file and folder I have found has a lock symbol on it and I am unable to delete or move to trash. I at least have not found a way yet, to get rid of them and correct the disk usage. So many apps are not working now I might end up doing reinstall of Ubuntu anyway but would like to avoid it if possible.

---

### Post by raja on 2007-03-23
You can delete them from the terminal with sudo to get administrator status. Otherwise, do ```
gksudo nautilus
```, then navigate to the folder and delete it. If it only a virtual machine you dont want anymore, it is safe to delete it.

---

### Post by Hendrixski on 2007-03-23
the lock could mean that the average user doesn't have permissions to modify these files (delete counts as modify).

your best bet is to, in the comand line, navigate over to that directory and type 
```
 sudo rm FILENAME
```
of change the permissions on the file by typing
```
 chmod FILENAME 777
```
and then deleting it from the GUI.

Hope that helps

---

### Post by J11Gyro on 2007-03-24
well not sure what happened now but will not even boot into recovery so here we go with new install. thanks for all the help again, this is a good learning experiance for sure:lolflag:

---

