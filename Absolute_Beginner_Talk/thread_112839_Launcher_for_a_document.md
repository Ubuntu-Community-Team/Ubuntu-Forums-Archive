---
title: "Launcher for a document"
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by TeeAhr1 on 2006-01-05
I would like to make a panel launcher for my phone list, which is an OpenOffice spreadsheet document.  I have tried a few different things, but I'm not really conversant in the commands used.  Let's say my phone list is at /path/to/file/phonelist.ods  What command would I use to launch this in OpenOffice directly?

---

### Post by SavageBeginner on 2006-01-05
```
oocalc2 /path/to/file/phonelist.ods
```
or even better
```
gnome-open /path/to/file/phonelist.ods
```
gnome-open will open any file with the same program that the file browser would.

---

### Post by TeeAhr1 on 2006-01-05
Aha!  I had it right, but it won't work if you have a space in the file name.  Thx!  -p.

---

### Post by SavageBeginner on 2006-01-05
You can add quotes for a space.
```
oocalc2 "/path/to/file/phone list.ods"
```
or a '\'
```
oocalc2 /path/to/file/phone\ list.ods
```

---

### Post by TeeAhr1 on 2006-01-05
Hey, nice!  Thank you!

---

### Post by TeeAhr1 on 2006-01-10
Hey, would this work with a media stream?  (I'm asking rather than trying it myself because I'm at work, not because I'm lazy :razz: )

---

