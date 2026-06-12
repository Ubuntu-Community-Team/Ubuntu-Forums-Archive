---
title: "cant install .run file"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by ezek on 2006-08-28
Hey, i downloaded the quake 4 demo for linux x86 and when i type in sudo sh install <filename> it says that it cant find the binary. Any suggestions?:confused: The file is quake4-linux-1.0-demo.x86.run

---

### Post by Anduu on 2006-08-28
All you should need to do is cd to the directory it is in and type ```
sh quake4-linux-1.0-demo.x86.run
```

---

### Post by ezek on 2006-08-28
i got it :D

---

### Post by WalmartSniperLX on 2006-08-28
or just put it in ur home folder and use the normal sudo sh <file.run name> command

---

### Post by amo-ej1 on 2006-08-28
(typically such a run file is a piece of a shell script followed with an embedded archive, usually a zip, the shell script checks the integrity of the archive and installs it, it's rather common in linux most games and third party software is shipped like this e.g. the java JDK as shipped by sun and the nvidia drivers as shipped by nvidia also use this format)

---

