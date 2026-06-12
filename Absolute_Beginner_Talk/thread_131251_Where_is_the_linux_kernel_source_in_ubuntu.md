---
title: "Where is the linux kernel source in ubuntu"
date: 2006-02-16
forum: Absolute Beginner Talk
---

### Post by ubuntes on 2006-02-16
I can't seem to find the linux kernel source.

I always thought in was in /usr/src (eg. /usr/src/linux)

However, when i went to /usr/src, the directory was empty.

I am using Ubuntu 5.10(breezy)

Thanks in advance,
Alex

---

### Post by bartbes on 2006-02-16
I think you have to download it first ```
e.g. with processor type 386
sudo apt-get source linux-386
```
I think you have it then..

---

### Post by steve.horsley on 2006-02-16
[QUOTE=bartbes]I think you have to download it first ```
e.g. with processor type 386
sudo apt-get source linux-386
```
I think you have it then..[/QUOTE]
You also probably want to install build-essentials. This is the compiler, make utilities, Linux source header files etc. If you are trying to compile an aplication, thsi may be all you need.

Steve

---

### Post by az on 2006-02-16
[QUOTE=ubuntes]I can't seem to find the linux kernel source.

I always thought in was in /usr/src (eg. /usr/src/linux)

However, when i went to /usr/src, the directory was empty.

I am using Ubuntu 5.10(breezy)

Thanks in advance,
Alex[/QUOTE]
There are linux-source and linux-headers packages available.  Not a lot of people need the source for the kernel, so it is not install by default.  If you only need to make a kernel module for the ubuntu kernel, use the linux-headers package and forget about using the full kernel source.

Linux-headers is on the install cd,

---

### Post by nickle on 2006-02-16
Here is a useful Howto if you want to build your own kernel...

[http://www.ubuntuforums.org/showthread.php?t=85064](http://www.ubuntuforums.org/showthread.php?t=85064)

---

### Post by ubuntes on 2006-02-16
[QUOTE=steve.horsley]You also probably want to install build-essentials. This is the compiler, make utilities, Linux source header files etc. If you are trying to compile an aplication, thsi may be all you need.

Steve[/QUOTE]


I am indeed trying to compile an application.  I will give this a shot.  Thanks Steve!

Alex

---

