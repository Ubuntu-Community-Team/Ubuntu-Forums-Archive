---
title: "make command not found while installing streamripper"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by alexandros81 on 2007-07-06
I want to record streamming audio (.pls). I have downloaded the streamripper in tar.gz. I typed in my terminal the tar -xzvf /home/alex/ streamripper-1.62.1.tar.gz comand. Created the directory  streamripper-1.62.1
. Changed to streamripper-1.62.1 directory. Typed the command ./configure. Started to run. When finished i typed the command make. Output was: command not found. Same happened with anothe package i tried to install.

---

### Post by annda on 2007-07-06
```
sudo apt-get install build-essential
```

is your answer. it will install the libraries needed for compiling.

---

