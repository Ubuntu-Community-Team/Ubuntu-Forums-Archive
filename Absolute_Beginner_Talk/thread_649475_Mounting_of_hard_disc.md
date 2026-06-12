---
title: "Mounting of hard disc"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by yvsmadhav on 2007-12-25
I am having winxp, win98se and Ubuntu on my hard discs. I am having photos and songs stored in winxp that is Fat 32. How to access those while booting into Ubuntu?

---

### Post by PmDematagoda on 2007-12-25
Open the fstab file for editing using:-

```
sudo gedit /etc/fstab
```

Then add a line like this:-
```
/dev/locationofdrive /media/nameoffolder vfat defaults 0 0
```

The "nameoffolder" which is to be replaced by "something" is where the folder where the drive is to be mounted, you can make one using:-
```
sudo mkdir /media/something
```
You may replace "something" with whatever you want:).

---

### Post by Rocket2DMn on 2007-12-25
If you need us to help you out with the details, post the output of
```
sudo fdisk -l
cat /etc/fstab
```
Also, please use gksudo for graphical applications (like gedit) instead of plain sudo - there is a major flaw that can occur and ruin your system with sudo running graphical apps (rare, but possible).

---

