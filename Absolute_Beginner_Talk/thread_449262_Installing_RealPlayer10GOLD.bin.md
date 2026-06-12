---
title: "Installing RealPlayer10GOLD.bin"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by jwh on 2007-05-20
I downloaded this and it's on my DeskTop.  I was at a tutorial site and I followed their instructions for installation. But it doesn't work.  This is what I do and what I get:

jw@Quasimodo:~$ cd desktop
bash: cd: desktop: No such file or directory
jw@Quasimodo:~$ cd Desktop
jw@Quasimodo:~/Desktop$ chmod a+x RealPlayer10GOLD.bin
jw@Quasimodo:~/Desktop$ sudo ./RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
jw@Quasimodo:~/Desktop$


Can someone say what's wrong?:popcorn:

---

### Post by Bachstelze on 2007-05-20
You're doing nothing wrong, you just need an additional library to run your program.

```
sudo apt-get install libstdc++5
```

Hint : when Ubuntu complains about a missing .so file, just search for it on [http://packages.ubuntu.com](http://packages.ubuntu.com) and it will tell you which package provide it.

---

