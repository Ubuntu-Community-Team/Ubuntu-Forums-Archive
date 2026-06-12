---
title: "Editing etc/apt files [Resolved]"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by BeeRad on 2006-11-20
Hi, I was in the process of adding a package in which I was to add line to my "sources.list" I made a mistake in entering the line using gedit.  I tried to reopen the file and change my mistake and I am not allowed to save the file.  I can't make any changes.  I tried to get into terminal as root but I can't open gedit from root.

Any suggestions?

BeeRad :confused:

---

### Post by junglepeanut on 2006-11-20
gksudo to open graphical programs with root

or 
sudo gedit /etc/apt/sources.list

---

### Post by junglepeanut on 2006-11-20
also try vim if gedit itself is not working

---

### Post by aysiu on 2006-11-20
> **junglepeanut said:**
> gksudo to open graphical programs with root

or 
sudo gedit /etc/apt/sources.list
In which case you'd actually do ```
gksudo gedit /etc/apt/sources.list
``` since Gedit is a graphical program. Otherwise, you can also do ```
sudo nano -B /etc/apt/sources.list
``` since Nano is a command-line program.

---

### Post by BeeRad on 2006-11-20
I did try sudo gedit /etc/apt/sources.list but I still couldn't make any changes.  I got a warning could not change ... message in yellow.
BeeRad

---

### Post by aysiu on 2006-11-20
Can you post the output of these commands in this order? ```
cd /etc/apt
ls -al
groups
```

---

### Post by BeeRad on 2006-11-20
I tried sudo nano -B /etc/apt/sources.list and it worked ok. thank you :)

BeeRad

---

