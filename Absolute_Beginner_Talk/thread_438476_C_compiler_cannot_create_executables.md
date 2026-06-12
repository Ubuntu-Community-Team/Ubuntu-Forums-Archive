---
title: "C compiler cannot create executables"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by krisfrajer on 2007-05-09
Hi people
I am trying to install pidgin from the source code. I untar the file and then I execute ./configure and I got the following error:

root@NARUTO:/home/cristian/Desktop# cd pidgin-2.0.0
root@NARUTO:/home/cristian/Desktop/pidgin-2.0.0# ./config
-bash: ./config: No such file or directory
root@NARUTO:/home/cristian/Desktop/pidgin-2.0.0# ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for sed... /bin/sed
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
root@NARUTO:/home/cristian/Desktop/pidgin-2.0.0# 

How can I fix this? Working in ubuntu v 7.02  in AMD64 architecture. Thxs a bunch... C.

---

### Post by Iokua on 2007-05-09
Try installing these packages: "libc6-dev" and "g++" either by Synaptic or in the terminal.

```
sudo apt-get install libc6-dev g++ 
```

---

### Post by taurus on 2007-05-09
```
sudo aptitde update
sudo aptitude install build-essential
```

---

### Post by krisfrajer on 2007-05-09
Hi 
I try how what you recommend and now I got this error. Could you point me out where could I find the source for the GLib 2.0 headers and how to install them??

root@NARUTO:/home/cristian/Desktop/pidgin-2.0.0# ./configure 
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
.
.
.
checking for dlopen in -ldl... yes
checking for the %z format string in strftime()... yes
checking for GLIB... no
no
configure: error:

You must have the GLib 2.0 development headers installed to build.

root@NARUTO:/home/cristian/Desktop/pidgin-2.0.0#

---

### Post by Adramelech on 2007-05-09
Look in the repositories:

libglib

You need the libglib-dev for compiling (development)

---

### Post by krisfrajer on 2007-05-09
sorry... what is that repository? somewhere in the web or a kind of files?
maybe a server with all the Linux source code? C.

---

### Post by Adramelech on 2007-05-09
Synaptic =)

---

### Post by krisfrajer on 2007-05-09
Synaptic... does it come with ubuntu? I cant find it and searching on the web... it says I have to install like 10 lib (or make sure I have them install) before I can install Synaptic. Am I doing something wrong?
C.

---

### Post by Adramelech on 2007-05-09
sorry my fault:
Synaptic is already in ubuntu, you ca find it on the menu System -> Administration -> Synaptic, is the usual way you use to install software. I suggest you get used to ubuntu before compiling stuff.

---

### Post by krisfrajer on 2007-05-09
Ths Adram... I am trying to get used to ubuntu... believes me... It is fun!
C.

---

