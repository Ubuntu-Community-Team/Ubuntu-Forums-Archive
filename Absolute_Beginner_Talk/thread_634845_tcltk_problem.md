---
title: "tcl/tk problem"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by keeZey on 2007-12-08
I had problems with getting my rt73 based wireless to work so i did some stuff off the internet which i had no idea what it does, but it worked. 

Now when i try to install amsn i says i dont have tcl8.4 when i have just installed it off package manger, also i cant install tk8.4 as it doesnt show ?

Any ideas on how to sort this?

---

### Post by keeZey on 2007-12-08
any1? wheres it install to so i can just delete it?

---

### Post by Partyboi2 on 2007-12-08
You should be able to install tk8.4 via apt-get
```
sudo apt-get install tk8.4
```
It should be listed if you do a search for it in synaptic package manager
If you want to remove you can do this:
```
sudo apt-get remove Package name
```Replace package name with name of package
eg```

sudo apt-get remove tcl8.4
```
You could try removing tcl8.4 and then reinstalling

---

