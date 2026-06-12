---
title: "External HDD help!"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by i8bugs75 on 2007-10-31
Got a question please!!!!! I have a SMARTDISK external usb HDD that for some reason isnt being recognized by ubuntu. It is usb powered and the light comes on when i plug it in, but nothing showes up on the desktop or computer browser like it normally would. The "removable drives and media" options under System -> preferences, has everything set right to mount when hot plugged and all that. Any solutions as to this prob? im sure its simple and im just not getting so flame me if you want:lolflag:

Thanx for the help

---

### Post by Dr Small on 2007-10-31
What is the drive formatted as ?

---

### Post by taurus on 2007-10-31
Open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
That is a lower case letter l, not number 1.

---

