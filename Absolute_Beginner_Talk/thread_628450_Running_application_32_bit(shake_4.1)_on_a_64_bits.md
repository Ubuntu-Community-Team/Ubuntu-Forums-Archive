---
title: "Running application 32 bit(shake 4.1) on a 64 bits?"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by Madj on 2007-12-01
Hi i really need to run an application 32 bit and i ve unbutstudio 64 bit.
I ve follow these command i found on the forum to install shake 4.1 but it s still not working:
So i ve made first that :To create a lib 32 bit on ubuntu:

sudo apt-get install dpkg-dev
cd ~/Desktop/usr/lib
cp -r ./* /usr/lib32/

And then i try to install the program shake 4.1.tar.gz:

First i ve Unpack shake and create dir. /usr/appl
then : gksu nautilus
then i move upacked folder to /usr/apple
install csh and tcsh
chmod 755 * /usr/apple/shake.../bin
csh shake

and when i do sudo shake or csh shake the terminale respond:

/usr/apple/shrank/shake4/bin# csh shake
/usr/apple/shrank/shake4/bin/shkx.exe: Command not found.



Can someone please help with his knowledge or give any advice,Thank you in advance.

---

### Post by Madj on 2007-12-01
No one can help ! please!

---

### Post by skymera on 2007-12-01
/usr/apple/shrank/shake4/bin/shkx.exe

is it a windows program?

if so

```
cd /to/the/directory
```

then

```
wine whatever.exe
```

---

### Post by Madj on 2007-12-01
No it s not a windows program this program have been  only devellop for mac os and linux and he have been not develop for windows at all!

So i try  wine but it don t make any difference!

Did someone know what s going wrong?

---

### Post by Madj on 2007-12-01
In fact  i think that to run this application yi ve to put tcsh and not csh.

/usr/apple/shrank/shake4/bin$ tcsh shake
/usr/apple/shrank/shake4/bin/shkx.exe: error while loading shared libraries: libGL.so.1: wrong ELF class: ELFCLASS64

I think it s a 32 bit problem on a 64 system?

i ve put the libstdc++5 and the ia32-libs i saw on a forum but it wont change a thing 

Also when  i make ldd le to find the missing lib it say not a dynamic executable 

/usr/apple/shrank/shake4/bin$ ldd le shake
le:
ldd: ./le: No such file or directory
shake:
        not a dynamic executable

Can someone,please, explain how i can solved this problem.

---

### Post by Madj on 2007-12-01
In fact i think that to run this application yi ve to put tcsh and not csh.

/usr/apple/shrank/shake4/bin$ tcsh shake
/usr/apple/shrank/shake4/bin/shkx.exe: error while loading shared libraries: libGL.so.1: wrong ELF class: ELFCLASS64

I think it s a 32 bit problem on a 64 system?

i ve put the libstdc++5 and the ia32-libs i saw on a forum but it wont change a thing

Also when i make ldd le to find the missing lib it say not a dynamic executable

/usr/apple/shrank/shake4/bin$ ldd le shake
le:
ldd: ./le: No such file or directory
shake:
not a dynamic executable

Can someone,please, explain how i can solved this problem.
__________________

---

### Post by Madj on 2007-12-01
really need some help please!

---

