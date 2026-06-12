---
title: "dxdiag command for linux"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by bobplano on 2007-05-15
i was just wondering if there was some kind of dxdiag command for linux that listed all your system specs

---

### Post by n8bounds on 2007-05-15
sudo lshw

---

### Post by DarkN00b on 2007-05-16
System -> Preferences -> Hardware Information.

---

### Post by Compyx on 2007-05-16
For the graphical, openGL side of things:
```

glxinfo

```

---

### Post by bobplano on 2007-05-16
thanks for the responses. the commands are good, although the output is a tad confusing at first. i don't have hardware information for the GUI way, but that's most likely because i'm using dapper. anyway thanks again

---

### Post by n8bounds on 2007-05-17
lshw-gtk is neat (its in universe, make sure u turn that on first)

sudo aptitude install lshw-gtk -y

then say 

sudo lshw-gtk

sometimes, tho I just say

sudo lshw > hardware.txt && gedit hardware.txt

replace gedit with kate or mousepad or leafpad or your other favorite text editor :)

---

