---
title: "Accesing windows partition"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by japc126 on 2008-02-28
How can I configure the windows partition so that amarok can acces it easily? right now, I can only access it if I punch in my admin code...

---

### Post by oedha on 2008-02-28
what is the partition type of your windows partition ?
have you enable ntfs-3g ( if you use it )

---

### Post by japc126 on 2008-02-28
I can acces it very easily through the file manager, Only i have to use the code to use it. In the permissions, it says I only have reading permissions and it doesnt le me change it....



Ooops, now amarok can now acces it easily... but I still dont have writting permissions. what do i do to enable writing to the windows partition?

---

### Post by oedha on 2008-02-28
if it's ntfs.......the easy way will be
go to applications - add/remove
search for ntfs in all available application
apply
then go to system - preferences - ntfs something
mark on the 2 boxes

---

### Post by Rocket2DMn on 2008-02-28
Can you please post the output of:
```
cat /etc/fstab
sudo fdisk -l
```
Also make sure you have write enabled when you run
```
gksudo ntfs-config
```

---

