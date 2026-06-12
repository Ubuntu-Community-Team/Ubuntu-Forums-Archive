---
title: "really simple query"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by niteblind on 2006-06-26
hi all

i hope this is simple.... i am following the instructions to set up bluetooth headset and am doing the following bit

"4. Time for the shell!
cd btsco-0.4
./configure
make
sudo make install"

when i type in ./configure i get a splurge of text which i assume is supposed to happen but when i then type "make" i get error that the command is not found

what am i doing wrong?
niteblind

---

### Post by jazzmuzik on 2006-06-26
You are compiling a program from source code. Therefore you need the compilers and libraries to accomplish that. Run this and it will install most of the basic programs you will need. (You may need other libraries however)

```
sudo apt-get install build-essential
```

This installs the essential packages for building (compiling) programs.

---

### Post by tonyr on 2006-06-26
Install package **build-essential** and try again.

---

### Post by angkor on 2006-06-26
Did you read the link I posted in your other thread?

On breezy you needed the following packages (and build-essential as mentioned above):
gcc
gcc-4.0
libc6-dev
linux-kernel-headers
libasound2-dev
libao-dev

I don't know if it's still the same, but I have all these packages installed on my system and building the snd_bt_sco module worked for me.

---

