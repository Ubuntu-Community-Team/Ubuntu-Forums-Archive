---
title: "[SOLVED] install .tar.bz2"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by KDE_rocks2345 on 2008-04-13
I have a tar.bz2 which I extracted to "/home/nja/Documents/mscore-0.9.2/" (Includes the folder) How do I install it?  It has a makefile in it however it opens in Kate which I don't like using (partly because I can't use it!) How do I install the file? :confused::confused::confused::confused::confused::confused::confused::confused:

---

### Post by Martje_001 on 2008-04-13
Go to a terminal and typ:
```
cd /home/nja/Documents/mscore-0.9.2/
make
sudo make install
```
if that doesn't work post the output and the output of:
```
ls
```
here.

But what's mscore? Maby a link to a website?

---

### Post by KDE_rocks2345 on 2008-04-13
Here is the output:


```
nja@nja-laptop:~/Documents/mscore-0.9.2$ make
if test ! -d build;                              \
         then                                          \
            mkdir build;                               \
            cd build;                                  \
            cmake -DCMAKE_BUILD_TYPE=RELEASE           \
                  -DCMAKE_INSTALL_PREFIX=""/usr/local"" \
                   ../mscore;                          \
            make lupdate;                              \
            make lrelease;                             \
            make -j `grep -c processor /proc/cpuinfo`;                           \
         else                                          \
            echo "build directory does already exist, please remove first with 'make clean'"; \
         fi;
/bin/sh: cmake: not found
make[1]: Entering directory `/home/nja/Documents/mscore-0.9.2/build'
make[1]: *** No rule to make target `lupdate'. Stop.
make[1]: Leaving directory `/home/nja/Documents/mscore-0.9.2/build'
make[1]: Entering directory `/home/nja/Documents/mscore-0.9.2/build'
make[1]: *** No rule to make target `lrelease'. Stop.
make[1]: Leaving directory `/home/nja/Documents/mscore-0.9.2/build'
make[1]: Entering directory `/home/nja/Documents/mscore-0.9.2/build'
make[1]: *** No targets specified and no makefile found. Stop.
make[1]: Leaving directory `/home/nja/Documents/mscore-0.9.2/build'
make: *** [release] Error 2
nja@nja-laptop:~/Documents/mscore-0.9.2$ sudo make install
[sudo] password for nja:
cd build; make install
make[1]: Entering directory `/home/nja/Documents/mscore-0.9.2/build'
make[1]: *** No rule to make target `install'. Stop.
make[1]: Leaving directory `/home/nja/Documents/mscore-0.9.2/build'
make: *** [install] Error 2
nja@nja-laptop:~/Documents/mscore-0.9.2$
```

mscore is a music program (manuscript sort of thing)

---

### Post by Martje_001 on 2008-04-13
You can install it with Synaptic..
**System --> Administration --> Synaptic** or **sudo synaptic**

---

### Post by KDE_rocks2345 on 2008-04-14
I use adept and when I search for 'mscore' it can't find anything.:confused:

---

### Post by PmDematagoda on 2008-04-14
First of all did you run:-
```
./configure
```
before running make?

---

### Post by Tatty on 2008-04-14
Its definately in the gutsy repositories

this should install it for you:
```
sudo apt-get install mscore
```

---

### Post by aysiu on 2008-04-14
I couldn't find it on the [http://packages.ubuntu.com](http://packages.ubuntu.com) website, but it appears to actually be in the repositories...
[http://security.ubuntu.com/ubuntu/pool/universe/m/mscore/](http://security.ubuntu.com/ubuntu/pool/universe/m/mscore/)

Maybe download the .deb, and double-click it?

---

### Post by KDE_rocks2345 on 2008-04-14
> **Tatty said:**
> Its definately in the gutsy repositories

this should install it for you:
```
sudo apt-get install mscore
```

```
E: Couldn't find package mscore
```

---

### Post by Tatty on 2008-04-14
Go to System->Administration->Software Sources, and make sure that all the repositories are checked there, then try again.

---

### Post by KDE_rocks2345 on 2008-04-14
> **aysiu said:**
> I couldn't find it on the [http://packages.ubuntu.com](http://packages.ubuntu.com) website, but it appears to actually be in the repositories...
[http://security.ubuntu.com/ubuntu/pool/universe/m/mscore/](http://security.ubuntu.com/ubuntu/pool/universe/m/mscore/)

Maybe download the .deb, and double-click it?

Thanks that post was really helpful

---

### Post by HunterThomson on 2008-04-14
I have mscore in my synaptic package manager... Try t click "Update" in the top left corner...

---

