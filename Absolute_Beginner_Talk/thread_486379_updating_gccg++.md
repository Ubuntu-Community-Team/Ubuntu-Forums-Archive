---
title: "updating gcc/g++"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by resistantgnome on 2007-06-27
Is it possible to  get a updated gcc/g++ package from somewhere which I can use to update my home pc's gcc/g++ package?
It has gcc 3.35 which is very old.

---

### Post by mickmade on 2007-06-27
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by resistantgnome on 2007-06-27
Actually I can't run command on my home PC as I am not connected to internet when I am at home. Can't I download some rpm of it from web through my office PC and later use it to update my home pc?

---

### Post by mickmade on 2007-06-28
[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.2/](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.2/)

There is an older article talking about installing gcc-3.4, should be the same. 
[http://ubuntuforums.org/showthread.php?t=79896](http://ubuntuforums.org/showthread.php?t=79896)

BTW, Ubuntu uses *.deb instead of *.rpm.

---

