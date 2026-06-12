---
title: "How to install JBuilder..?"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by Nizzle on 2007-01-13
Hello :)

I'm using Ubuntu 6.10 Edgy for a while now.. started with dual boot but now totally removed all of the MS and Windows crap.. :D

anyways.. back on point
at school I need to use JBuilder to write JAVA applications..
but on ubuntu I have no clue how to install it.. I've downloaded it.. to the desktop.. even managed to extract the files and made the install.bin file executable.. followed some tutorials on that

anyways then I try to run the install.bin file to.. install..? right?

so I did this 
```
nizzle@nizzle-desktop:~$ cd Desktop
nizzle@nizzle-desktop:~/Desktop$ cd jb2005_linux
nizzle@nizzle-desktop:~/Desktop/jb2005_linux$ ls
index.html  install.bin  licensed.src  license.html  setup
nizzle@nizzle-desktop:~/Desktop/jb2005_linux$ ./install.bin
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
nawk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
hostname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

Launching installer...

grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/tmp/install.dir.10074/Linux/resource/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory
```

and now I have no clue how to continue.. ](*,) 
please help :mrgreen:

---

### Post by jvc26 on 2007-01-13
If you're trying to install a .bin file, go to the file, right click, properties, permissions, allow executing, then close that, then double click on it and it should open the package manager and let you install it.
Il

---

### Post by Nizzle on 2007-01-13
yeah.. I did that.. but then I get all them errors as I posted above :(

---

### Post by Nizzle on 2007-01-17
anyone..? 8-[

---

### Post by Axed on 2007-01-21
I was googling a similar error because I was having trouble installing gallery remote, and the  instructions at the end of this thread fixed it for me:
[http://gallery.menalto.com/node/56684](http://gallery.menalto.com/node/56684)

The Gallery site appears to be inaccessible from my current location at present so if you don't have any luck try the google cache.

edit: may as well c&p it here:
```
$ cp Gallery_Remote Gallery_Remote.back
$ cat Gallery_Remote.back | sed "s/export LD_ASSUME_KERNEL/#xport LD_ASSUME_KERNEL/" > Gallery_Remote
```
Obviously replace any reference to Gallery_Remote with jbuilder.

---

### Post by Nizzle on 2007-01-21
yes I've found the same thing with mercury messenger

at which they say this
> I had the same problems with some launchers of java programs.
The solution I found that works is the following:

1. Make a backup of Mercury file:
cp Mercury Mercury.bak
2. Comment the lines with export LD_ASSUME_KERNEL and create a new Mercury file:
cat Mercury.bak | sed "s/export LD_ASSUME_KERNEL/#xport LD_ASSUME_KERNEL/" > Mercury
3. Try now to execute Mercury and if it works you can delete Mercury.bak

Bye!

I have no clue what they mean though.. :(

---

### Post by jtsop on 2007-01-26
> **Axed said:**
> I was googling a similar error because I was having trouble installing gallery remote, and the  instructions at the end of this thread fixed it for me:
[http://gallery.menalto.com/node/56684](http://gallery.menalto.com/node/56684)

The Gallery site appears to be inaccessible from my current location at present so if you don't have any luck try the google cache.

edit: may as well c&p it here:
```
$ cp Gallery_Remote Gallery_Remote.back
$ cat Gallery_Remote.back | sed "s/export LD_ASSUME_KERNEL/#xport LD_ASSUME_KERNEL/" > Gallery_Remote
```
Obviously replace any reference to Gallery_Remote with jbuilder.

go to the directory where you extracted the downloaded file and:
$ cd jb2006_linux/Disk1/InstData/Linux/VM/
$ cp install.bin install.bin.orig
$ cat install.bin.orig | sed "s/export LD_ASSUME_KERNEL/#xport LD_ASSUME_KERNEL/" > install.bin

---

### Post by Nizzle on 2007-01-26
omg thank you :D

now I've finally got it working (H)

---

### Post by boolean12 on 2007-01-29
i have still troubles! could anyone post a 1,2,3... steps of install HOW TO??
i couldn't make it work! :( 

i get these two screens one after another and nothing happens. I really need your help...

[IMG]http://img233.imageshack.us/img233/276/screenshotborlandjbuildeg4.png[/IMG]   
[IMG]http://img388.imageshack.us/img388/1060/screenshotborlandjbuildfr4.png[/IMG]

help would be much appreciated!

---

### Post by cpttripzz on 2007-03-08
thnx alot to jtsop and Axed, you guys are wicked. I was getting worried that i was going to have to install a supported os, you guys saved me a lot of time. ubuntu rules, and you guys kick ***.

CONFIRMATION: this fixed the problem. :guitar:

---

