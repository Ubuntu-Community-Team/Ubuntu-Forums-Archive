---
title: "Tar Files"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by Mikey_MW on 2007-06-09
I don´t normally have trouble with googling the answers but I´m stuck on this one file. I´ve downloaded the game Cube - but now I don´t know how to install it. Some site said -zxvf cube_2005_08_29_unix.tar.gz but that doesn´t work...

HELP!!!

---

### Post by reidms on 2007-06-09
type
```
tar -zxvf
```
-zxvf are options for the main program tar

---

### Post by m0rph on 2007-06-09
The .tar file extension indicates that the file is an archive that has been put into "Tape ARchive" format.  Today tar is most commonly used to package files together for transfer over the internet.  One tar file usually corresponds to many regular files.  Files can be extracted from the archive using the tar utility.

Think of the file you have downloaded like a zip file you just need to extract it so you can install CUBE

Have you followed;
[http://linux.softpedia.com/get/GAMES-ENTERTAINMENT/FPS/Cube-5774.shtml](http://linux.softpedia.com/get/GAMES-ENTERTAINMENT/FPS/Cube-5774.shtml)

Download file
Un Zip well i mean Un TAR
and Install

---

### Post by Mikey_MW on 2007-06-09
Ah, my stupidity - thank you

:D

---

### Post by Rocket2DMn on 2007-06-09
If it's tar.gz, you may need to 
```
gunzip filename.tar.gz
```
 first to get the tar archive.

---

