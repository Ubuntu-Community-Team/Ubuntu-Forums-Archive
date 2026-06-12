---
title: "RealPlayer problem"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by Benbow on 2007-11-02
When I have downloaded realplayer to my home directory and follow the usual instructions to install for Feisty (I am now using Gutsy), I get the following - 

benbow@benbow-desktop:~$ chmod +x RealPlayer10GOLD.bin
benbow@benbow-desktop:~$ ./RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
benbow@benbow-desktop:~$ 

Help appreciated

---

### Post by reckless2k2 on 2007-11-02
sudo apt-get install libstdc++5

then try it again.

---

### Post by jayaramk on 2007-11-02
there's a .deb package of real player available .. you can download it and install it rather than installing the bin file!!!!

---

### Post by philinux on 2007-11-02
Real player is in synaptic if you've set up your sources.

---

### Post by Bablefish on 2007-11-02
Installing Real Player could not be any easier than using this terminal command line

sudo apt-get install realplayer

---

