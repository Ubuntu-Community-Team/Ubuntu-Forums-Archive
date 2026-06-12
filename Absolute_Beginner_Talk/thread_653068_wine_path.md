---
title: "wine path"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by gleble on 2007-12-29
I have had to download wine to run a sim card reader I got for Xmas. However when i try to run it I get this;```
neil@neil-laptop:~$ wine simeditor.exe
wine: could not load L"c:\\windows\\system32\\simeditor.exe": Module not found
``` 
Am I being stupid or is it looking in the wrong place. How do I make it look in Program Files/SIM MAX ?

---

### Post by PmDematagoda on 2007-12-29
You should move into the folder where the file is found and then execute the command.

---

### Post by gleble on 2007-12-29
Tried:
```
neil@neil-laptop:~$ cd .wine
neil@neil-laptop:~/.wine$ cd drive_c
neil@neil-laptop:~/.wine/drive_c$ cd Program Files
bash: cd: Program: No such file or directory
neil@neil-laptop:~/.wine/drive_c$ 

```
Why won't it go to Program Files?

---

### Post by mc4man on 2007-12-29
try
```
cd 'Program Files'
```
or complete   change  - particulars
```
wine '/home/doug/.wine/drive_c/Program Files/ImgBurn/ImgBurn.exe' 
```

you won't be able to run the exe by cd'ing to it ,either run to complete as above or browse to the .exe and right click open with wine.  If you browse to it when you get to drive_c set a bookmark and it will show up in places for future use

---

### Post by gleble on 2007-12-29
ok
```
neil@neil-laptop:~/.wine/drive_c$ cd Program\ Files
```

---

