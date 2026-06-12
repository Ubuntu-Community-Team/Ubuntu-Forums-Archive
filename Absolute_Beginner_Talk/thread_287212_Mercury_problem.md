---
title: "Mercury problem"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by barisnisli on 2006-10-28
I can't run mercury messenger 1.8. I installed the java and mercury messenger. I configured the java.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
*         2    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
 +        3    /usr/lib/j2se/1.4/bin/java


When I write mercury, I have this error. 

nawk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/usr/lib/jvm/java-1.5.0-sun/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory


what should I do. thanks :)

---

### Post by seaside on 2006-10-28
Did you install "libc6"?

---

### Post by barisnisli on 2006-10-28
yes I did. libc6 version is 2.4-1.

---

### Post by Omnios on 2006-10-31
I have the same problem. It can probably be fixed by linking libc.so.6 for java. Im looking into it so it might be a bit before I figure it out.

---

### Post by Omnios on 2006-11-01
Made a mercury fix mod here:

[http://ubuntuforums.org/showthread.php?t=290234](http://ubuntuforums.org/showthread.php?t=290234)

---

### Post by barisnisli on 2006-11-04
I followed that instructions. but I have had same error since I wrote Mercury instead of mercury by chance. when I write mercury I have same error. when I write Mercury it works. thanks :)

---

### Post by erizo on 2006-12-28
Hi, I installed everything correctly from a .deb package.
the installer said: installation succesful, all the dependencies are OK.
I got a launch icon but when I double click it nothing happens...
any clue?

---

### Post by syshex on 2007-01-04
Hi everyone

See if my example makes any sense to you:
This is my error and the way I corrected it:

```


rui@pipeline:~/Archive/Installers$ ./jb2005_linux/install.bin 
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
/tmp/install.dir.30172/Linux/resource/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory
rui@pipeline:~/Archive/Installers$ cd jb2005_linux
rui@pipeline:~/Archive/Installers/jb2005_linux$ cat install.bin  | sed "s/export LD_ASSUME_KERNEL/#xport LD_ASSUME_KERNEL/" > install2.bin 
rui@pipeline:~/Archive/Installers/jb2005_linux$ ls -lFh
total 193M
-rw-r--r-- 1 rui rui  907 2004-09-02 12:00 index.html
-rw-r--r-- 1 rui rui  97M 2007-01-04 16:54 install2.bin
-rwxr-xr-x 1 rui rui  97M 2004-09-02 12:00 install.bin*
drwxr-xr-x 2 rui rui 4.0K 2004-09-02 12:00 licensed.src/
-rw-r--r-- 1 rui rui  39K 2004-09-02 12:00 license.html
drwxr-xr-x 5 rui rui 4.0K 2004-09-02 12:00 setup/
rui@pipeline:~/Archive/Installers/jb2005_linux$ chmod +x install2.bin 
rui@pipeline:~/Archive/Installers/jb2005_linux$ ./install2.bin 
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...

Launching installer...

rui@pipeline:~/Archive/Installers/jb2005_linux$ 

```

Change accordingly and see if it works this time
Syshex

---

### Post by Christoffer Klang on 2007-05-04
wow i have been sitting here for well over two hours just trying to fix this, thank you for your fix post syshex!, works like a charm ;)

---

### Post by Puro_Osso on 2007-05-16
> **barisnisli said:**
> I can't run mercury messenger 1.8. I installed the java and mercury messenger. I configured the java.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
*         2    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
 +        3    /usr/lib/j2se/1.4/bin/java


When I write mercury, I have this error. 

nawk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/usr/lib/jvm/java-1.5.0-sun/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory


what should I do. thanks :)



Got same error here!
I tried this [http://ubuntuforums.org/showthread.php?t=290234](http://ubuntuforums.org/showthread.php?t=290234) and didn't work =/

root@chen-linux:/home/chen# mercury
nawk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/usr/lib/j2se/1.4/bin/../jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory

I got libc6 installed too!

---

### Post by syshex on 2008-01-03
dude, check my example before hand .... it should be pretty clear what you need to do.

Thx
Rp

---

