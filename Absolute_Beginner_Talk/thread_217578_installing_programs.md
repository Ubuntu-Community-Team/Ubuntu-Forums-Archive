---
title: "installing programs"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by mharris5 on 2006-07-17
Hi,

I'm new to Ubuntu and am having problems installing programs. The program I've tried to install is a g++ compiler, compressed using tar and then bzip2.

So far I have unpacked the program, but when I go to configure the file I get an error message,

./configure
configure: error: cannot find install-sh or install.sh in . ./.. ./../..

I have checked to make sure I'm in the right folder and it's the only one containing a configure file.

Any help would be great. Thanks.

Matt

---

### Post by mostwanted on 2006-07-17
```
sudo apt-get install build-essential
```

Installs GCC (which includes G++) and the other compiler tools.

---

### Post by lurkerspine on 2006-07-17
Code:
```
sudo apt-get install g++
```

That code is for just installing a g++ compiler.

---

### Post by mharris5 on 2006-07-17
great. thanks again.

---

