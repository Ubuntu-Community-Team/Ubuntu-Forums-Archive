---
title: "help me on IEs 4 Linux  problem"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by saurabh kakkar on 2007-08-04
hi
IEs 4 Linux - Internet Explorers for Linux whose readme says this 

USAGE
=====
Just execute the program ies4linux inside this folder and follow the instructions.
To do this, open a terminal, cd to this folder and type:
./ies4linux

i am doing the same but terminal is showing something like this 

root@ubuntu:/home/saurabh/Desktop/ies4linux-2.0.3#  ./ies4linux
bash: ./ies4linux: Permission denied

what should i do ?

---

### Post by ron999 on 2007-08-04
Hi
Try typing** sudo ./ies4linux**
:)

---

### Post by saurabh kakkar on 2007-08-04
sir i have tried these things but in vain 

root@ubuntu:/home/saurabh# cd
root@ubuntu:~# cd /home/saurabh/Desktop/ies4linux-2.0.3
root@ubuntu:/home/saurabh/Desktop/ies4linux-2.0.3# sudo ./ies4linux
sudo: ./ies4linux: command not found

root@ubuntu:/home/saurabh/Desktop/ies4linux-2.0.3# sudo./ies4linux
bash: sudo./ies4linux: No such file or directory

root@ubuntu:/home/saurabh/Desktop/ies4linux-2.0.3# ./ies4linux
bash: ./ies4linux: Permission denied
root@ubuntu:/home/saurabh/Desktop/ies4linux-2.0.3# 

what should i do ?

---

### Post by atomkarinca on 2007-08-04
```
chmod +x ies4linux
```
then try it again.

---

### Post by saurabh kakkar on 2007-08-04
thanks buddy it solved my problem but i wana know what was wrong and what is this command 

thanks again

---

### Post by atomkarinca on 2007-08-04
it's an installer so it should have some permissions before it can start. this command just gives the installer permissions.

---

### Post by ron999 on 2007-08-04
...............

---

