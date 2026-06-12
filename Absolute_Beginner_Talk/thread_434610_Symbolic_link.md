---
title: "Symbolic link"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by subtle on 2007-05-06
Hello,

I'm a real noob to linux. I want to learn as most Programming jobs require at least some knowledge of linux.I'm trying to install java. I've managed to install it although probably not in the best place (on the Desktop :( ).Now I'm tryinf to set upsymbolic links to I can compile and run my programs from anywhere.

The first symboliclink i tried was

ln -s /usr/java/j2sdk1.4.2/bin/java /usr/bin/java

the console said that this link already exists then next link I tried was

ln -s /usr/java/j2sdk1.4.2/bin/javac /usr/bin/javac

the console said "Permission denied"

How do I overcome this? also is there a better place to install the sdk other than on my desktop? if so, how do I remove the current install and create the new one.

Any helpmuch appreciated.

---

### Post by Cappy on 2007-05-06
you need to use sudo when creating a link in a folder you don't have permissions for. My java's default install was /opt/jdk1.6.0_01/bin but I used the the java + netbeans install.

---

### Post by subtle on 2007-05-06
Thanks

---

