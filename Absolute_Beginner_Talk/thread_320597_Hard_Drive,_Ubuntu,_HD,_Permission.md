---
title: "Hard Drive, Ubuntu, HD, Permission"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by ubuntu27 on 2006-12-17
Hello, I am helping another firend again. :D

This time he says that he has trouble deleting or making any changes to his external HD in UBuntu. It tells him:

The file blahblach cannot be deleted becouse it is inside a read only disc.


Any help will be apreciated.

Some notes:
The external HD is Western Digital
It connects using USB.

---

### Post by taurus on 2006-12-17
Just need to put the sudo in front of the command he is planning to run...

---

### Post by ubuntu27 on 2006-12-17
> **taurus said:**
> Just need to put the sudo in front of the command he is planning to run...

Thank you.

We don't know that much about terminal comands. 

He is trying to do everything in nautilus. :)

---

### Post by taurus on 2006-12-17
Applications -> Accessories -> Terminal
```
gksudo nautilus
```

---

### Post by ubuntu27 on 2006-12-18
> **taurus said:**
> Applications -> Accessories -> Terminal
```
gksudo nautilus
```


Yooho! Thank you Taurus!! :)
Got to memorize that command "gksudo"

so gksudo is for giving sudo power to a non-terminal app?

---

### Post by taurus on 2006-12-18
Yip.  If you want to run something from a terminal like cp, mv, nano, etc., then you use sudo but if you want something in graphical like gedit, nautilus, synaptic, etc., then you need to run it with gksudo.

---

### Post by ubuntu27 on 2006-12-18
> **taurus said:**
> Yip.  If you want to run something from a terminal like cp, mv, nano, etc., then you use sudo but if you want something in graphical like gedit, nautilus, synaptic, etc., then you need to run it with gksudo.

THank you Taurus! This new knowledge is going to be so useful. :)

---

### Post by score_under on 2006-12-18
If you are running kubuntu, you could use kdesu

---

