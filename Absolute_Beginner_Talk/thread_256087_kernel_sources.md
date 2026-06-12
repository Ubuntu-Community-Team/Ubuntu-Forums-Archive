---
title: "kernel sources"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by Chris Val Kef on 2006-09-12
where are the kernel sources installed?

if there are not installed what is the package needed?

---

### Post by whizbaby on 2006-09-12
The source package is called *linux-source*, but you might also want *build-essential* or *linux-kernel-headers*.

---

### Post by az on 2006-09-12
To build an extra kernel module, you do not need the full source.  Just install linux-headers-386 and you are good to go.

---

### Post by Chris Val Kef on 2006-09-12
do you know where hey are installed. can you give me the path?

i need the path to install some drivers...

---

### Post by az on 2006-09-13
There is a symlink to the headers once you install the package.  Usually, the configure script finds that symlink and you don't need to enter anything - the symlink is in /lib/modules/`uname -r`/build

---

