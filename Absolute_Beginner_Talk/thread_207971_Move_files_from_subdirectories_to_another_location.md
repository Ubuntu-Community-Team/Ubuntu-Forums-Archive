---
title: "Move files from subdirectories to another location."
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by chajuram on 2006-07-02
Hi,

I have a directory with subdirectories and the ls -R looks like this

> 
.:
Aakash Prodeep    Archana               Deeper Naam Tiyarong  Salil Chowdhury
Aandhar Surjo     Baluchuri             Deya Neya             Shagorika
Ami Shey O Sakha  Bhanu Pelo Lottery    Komollata
Anada Ashram      Bhrantibilash         Panna Heerey Chuni
Antoral           Bonpalashir Podaboli  Raajkonya

./Aakash Prodeep:
07 Mago Tumi Emon Korey.m4a

./Aandhar Surjo:
17 Raat Nijhum Hok Na.m4a

./Ami Shey O Sakha:
15 Ei Haanshi Manay Na.m4a

./Anada Ashram:
13 Tinti Montro Niye.m4a

./Antoral:
03 Tumi Ki Emni Korei.m4a  10 Tomar Shomadhi Phuley.m4a
.
.
.


Now I want to move/copy all the files in all subdirectories with the extension .m4a, I know there must be an easy way of doing this, either using mv/ls/cp, but I could not figure it out. I was wondering if anyone could give me a nice small answer. 

Chajuram.

---

### Post by scxtt on 2006-07-02
you could run find, then have it move anything it finds w/ a .m4a extension somewhere else ...```
find . -name .m4a -exec mv {} /move_to_dir \;
```where "move_to_dir" is the absolute path to the directory where you want to move them too (for example /home/chajuram/m4a_files) ... make sure you're in the top level directory where you ran ls -R from, so it looks in those subdirs ... also, try a cp instead of mv if you "just want to be safe" ...

---

### Post by chajuram on 2006-07-02
Hi,

Thanks scxtt for you quick reply. 

It worked, I suppose it will be *.m4a instead of .m4a. 

Chajuram.

---

