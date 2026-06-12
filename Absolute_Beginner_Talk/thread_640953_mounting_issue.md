---
title: "mounting issue"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by jamelb on 2007-12-14
everytime i try and mount my other drive i get this[ATTACH]53253[/ATTACH]

---

### Post by thelatinist on 2007-12-14
You've got an invalid character in the name of the directory you're trying to mount to.  Try mounting to a different directory.

---

### Post by PmDematagoda on 2007-12-14
You can try mounting the drive manually by following these steps:-

1) Open Nautilus in root mode using:-

```
gksudo nautilus
```

2) Create a new folder in the /media folder called "test"

3) Mount the drive using:-
```

sudo mount /dev/location /media/test
```

Location replaced by the location of your hard drive such as:-
```
sda1
sdb1
hda1
```

---

### Post by jamelb on 2007-12-14
wont even let me create a folder when i try to open it i get that error it was just working yesterday

---

### Post by taurus on 2007-12-14
What other drive on this list that you are trying to mount?

```
sudo fdisk -l
```

---

### Post by jamelb on 2007-12-14
/dev/sda1 is the one i am trying to mount

---

### Post by taurus on 2007-12-14
If it's ntfs filesystem, do

```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/sda1
sudo mount -t ntfs-3g /dev/sda1 /media/sda1
```

If it's fat32, do

```
sudo mkdir /media/sda1
sudo mount -t vfat /dev/sda1 /media/sda1 -o umask=000
```

If it's ext3, do

```
sudo mkdir /media/sda1
sudo mount -t ext3 /dev/sda1 /media/sda1
```

---

### Post by diatribe on 2007-12-14
assuming it isn't ntfs are the -t switches even necessary?

---

### Post by jamelb on 2007-12-15
thank you to everybody that helped put i got it working

---

