---
title: "How to run *.run files"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by H3HI on 2006-09-11
I have downloaded a nVidia diplay driver from the offical website.

it's extend name is "run", how do i run these file on ubuntu?

---

### Post by Najand on 2006-09-11
Mayeb you just need to:
```
./FILENAME.run
```
And push the enter key.

---

### Post by monktbd on 2006-09-11
is the driver that you can install from the repositories with synaptic or apt-get not working for you?
if it does i would suggest sticking to it.

if you really need to have the newest version then you need to write ./ in front of the command you would like to execute from the current directory.

löinux only checks in the folders in the path for executables not in the current directory. so you need to specify directly with ./ that you want to run a command in the current folder.

e.g

> ./mydriver.run

and you might need to set the file to be executed as well with chmod or with a right click on it in nautlisu and changing permissions in the properties.

---

