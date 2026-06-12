---
title: "Can you make folders hidden???"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by WalmartSniperLX on 2006-09-04
Hey i was wondering if its possible to makes folders hidden and how to do that :D  thanks

---

### Post by Uluen on 2006-09-04
Yes, just put a dot in the beginning of the folder name.
```
$ mkdir test
```
```
$ mv test/ .test
```

---

### Post by skymt on 2006-09-04
Yep! Just stick a period (.) at the start of the name.

EDIT: Simulpost! Also, to see hidden folders in GNOME, go to the View menu and choose Show Hidden Files

---

### Post by WalmartSniperLX on 2006-09-04
ok Thanks all! :D

---

### Post by catlett on 2006-09-04
Just put a period in front of the folder when you name it. That makes it hidden.  Either right click and select "create folder" or use the terminal command mkdir (make directory). For a folder called hidden in your home folder issue this command```
 mkdir /home/WalmartSniperLX/.hidden
```
To view hidden folders, open up nautilus (the file browser. launch it with Places<Home Folder) then select "view" and then "show hidden folders".

---

### Post by Uluen on 2006-09-04
CTRL-H is a quick way to show/hide hidden files in nautilus.

---

