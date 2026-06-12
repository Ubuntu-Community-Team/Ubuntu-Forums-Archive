---
title: "NTFS refucsing"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-07-20
diffdrent matter.

in fstab my windows, (sda1) appears
but when i try to mount
```
 sudo mount /dev/sda1
```

it says no such device??
anyone wknow why?

---

### Post by kagashe on 2007-07-20
> **skymera said:**
> diffdrent matter.

in fstab my windows, (sda1) appears
but when i try to mount
```
 sudo mount /dev/sda1
```

it says no such device??
anyone wknow why?Check whether fstab is already mounting it at /media/sda1, if not the command is:
> sudo mount /dev/sda1 /media/sda1

I hope the directory sda1 already exists if not:
> sudo mkdir /media/sda1

kagashe

---

### Post by skymera on 2007-07-20
i do 
sudo mount /dev/sda1

but it says its not found in fstba?????

---

### Post by AlexenderReez on 2007-07-20
> **skymera said:**
> i do 
sudo mount /dev/sda1

but it says its not found in fstba?????

try to understand it is better....look at this--->

> [http://ubuntuforums.org/showpost.php?p=3047936&postcount=2](http://ubuntuforums.org/showpost.php?p=3047936&postcount=2)

---

