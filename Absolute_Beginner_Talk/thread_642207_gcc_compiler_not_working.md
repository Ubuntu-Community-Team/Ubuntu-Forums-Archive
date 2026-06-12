---
title: "gcc compiler not working"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by thejdev on 2007-12-16
I try to compile a simple .c file (main(){return(0);})  and when i type the command 
      gcc <filename>.c

it says 
/usr/bin/ld : crt1.o not found .... the file's not linking 

Could someone help me patch this 

I am running ubuntu on an AMD Athlon 64-bit machine and the gcc version is 4.1

---

### Post by taurus on 2007-12-16
How did you install the GCC compiler?  Did you just install gcc by itself or did you install the actual build-essential package?

```
sudo apt-get update
sudo apt-get install build-essential
gcc -v
gcc **filename**.c
```

---

### Post by thejdev on 2007-12-16
I didnt install the gcc compiler solo ... it came along with the Ubuntu Gutsy ... it compiles but finds problems with linking.
I tried to install the glibc-2.7 libraries but while configuring the package it said that my gcc cant form executables

---

### Post by taurus on 2007-12-16
Please install the build-essential package first before you compile anything.

---

### Post by thejdev on 2007-12-16
K  ..... thanks:) <was in idiot mode:confused:>

---

