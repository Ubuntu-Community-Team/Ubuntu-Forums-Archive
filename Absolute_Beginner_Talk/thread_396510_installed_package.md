---
title: "installed package"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by ceezax on 2007-03-29
hi there

i just installed dsniff using aptitude install dsniff 

then i want to run this application how can i do that???

note : i searched the whole system for dsniff which come out with this result

/usr/share/doc/bash/completion-contrib

and when i try to run ./dsniff it tells me that permission denied although i am logged 

in as th root user

---

### Post by zvacet on 2007-03-29
Use** sudo**.

---

### Post by zvacet on 2007-03-29
Use** sudo**. 
```
sudo ./dsniff
```

---

### Post by ceezax on 2007-03-29
muhammad@muhammad-desktop:/usr/share/doc/bash/completion-contrib$ sudo ./dsniff
sudo: ./dsniff: command not found


please tell me the right form

---

### Post by hockey97 on 2007-04-11
The command is 

sudo dsniff 

type that in the console thing and should start up.

---

