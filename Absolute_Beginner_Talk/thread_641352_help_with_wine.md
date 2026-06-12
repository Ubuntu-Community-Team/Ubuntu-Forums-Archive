---
title: "help with wine"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by Quicksilver21 on 2007-12-15
i installed wine through syanptic and it installed successfully and everything and it show up in my apllications menu but it wont open and when i try to open it i get this error message:

wine: creating configuration directory '/home/stephen/.wine'...
Segmentation fault (core dumped)
wine: wineprefixcreate failed while creating '/home/stephen/.wine'.

wineserver: could not save registry branch to /home/stephen/.wine-eJCWsD/system.reg : No such file or directory
wineserver: could not save registry branch to /home/stephen/.wine-eJCWsD/user.reg : No such file or directory

so i tried creating the directory and then it said it couldnt make another directory.

---

### Post by nikoPSK on 2007-12-15
I would say remove wine:
```
sudo aot-get remove wine
```
then revove yiur folder, reinstall wine:
```
sudo apt-get install wine
```
update
```
sudo apt-get update
```
then run it. :KS

---

