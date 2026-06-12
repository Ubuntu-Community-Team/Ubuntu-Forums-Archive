---
title: "Anyone OpenOffice working on PowerPC?"
date: 2005-11-29
forum: Apple PPC Users
---

### Post by tijs on 2005-11-29
Hi,

I have problems with OpenOffice. It never worked for me, not even after installing all packages related to OpenOffice.

It looks like there is a problem with Java:


> xxxxxxx@macintosh:/opt/ibm-java2-ppc-50/bin$ ooffice2 -writer %U
/usr/lib/openoffice2/program/javaldx: error while loading shared libraries: libuno_sal.so.3: cannot open shared object file: No such file or directory
/usr/lib/openoffice2/program/soffice.bin: error while loading shared libraries: libvcl680lp.so: cannot open shared object file: No such file or directory

So I installed Java for PPC as instructed in the WIKI: [https://wiki.ubuntu.com/JavaPPC](https://wiki.ubuntu.com/JavaPPC)

However, I'm not sure whether Java is actually working, though I can configure which Java to use (see Wiki, "sudo update-alternatives --config java" works for me).

This is where it goes wrong I think:

> Pick the java version we installed as the default.

$ java -showversion 
java version "1.5.0"
Java(TM) 2 Runtime Environment, Standard Edition (build pxp32dev-20050923b)
IBM J9SE VM (build 2.3, J2RE 1.5.0 IBM J9 2.3 Linux ppc-32 j9vmxp3223-20050915a (JIT enabled)
J9VM - 20050914_03248_bHdSMR
JIT  - 20050914_1758_r8
GC   - 20050907_AB)
JCL  - 20050915


The command "java -showversion" gives me a "command not found" error.

What am I missing here?

---

### Post by grizzly451 on 2005-11-30
I don't know enough about that error to help you any, but I've got OpenOffice running fine on my old apple.   Have you tried reinstalling linux?

I did have a big problem with java when I was running ubuntu, but after I switched to kubuntu I got it installed without any problems.

---

### Post by tijs on 2005-11-30
[QUOTE=grizzly451]I don't know enough about that error to help you any, but I've got OpenOffice running fine on my old apple.   Have you tried reinstalling linux?

I did have a big problem with java when I was running ubuntu, but after I switched to kubuntu I got it installed without any problems.[/QUOTE]

Well, reinstalling is a bit drastic isn't it? I'd rather not do that obviously.

I just discovered that I can get Openoffice 1.1.5 to work in Gnome and Xfce, not in KDE. Openoffice 2 works in none of them and gives the error above.

Anyway, I come to realise there are quite a few issues if you run Ubuntu on a Powerpc, issues which are probably not Ubuntu's fault (problems installing proprietary software like Java and nVidia drivers) but which are a nuisance nonetheless. :)

---

### Post by grizzly451 on 2005-11-30
I only suggest the reinstalling option since I know I had to reinstall like 5 or 6 times before I got the install right and the computer working the way I wanted it (without breaking the OS).

Like I said I had a huge problem with getting java on my apple when I was running ubuntu.  It definitely run kubuntu alot smoother and more to my liking.

I haven't had any problems with video thank goodness.

What are the specs of your ppc?  I was only wondering about what kind of performance you are having with it overall.

---

### Post by tijs on 2005-12-01
Performance is quite good, but then there is 1.5 GB of RAM in this machine. The video card is acting a bit funny sometimes, with green colours turning up on the border of the screen, but all in all it is OK.

I am crossing my fingers, but it looks like in Gnome things are working better, no crashes yet but then it's morning and the crashes usually happen in the afternoon :D 

Kubuntu and Ubuntu are the same AFAIK, it's just a different window manager. I have both installed now.

---

### Post by rwaliany on 2006-03-26
Just had this problem re-install openoffice.org2-core

- Ryan Waliany

---

### Post by funkyade on 2006-03-29
try this to check for your java version

```
java -version
```

The IBM java doesn't recognise -showversion!

I have openoffice2 running on an iBook with all the components - it works with the free java (GCJ) btw.

Use Synaptic or Adept mark all the openoffice packages for installation and then do a search for java or jvm and install the GCJ or GIJ packages to get a free java.

hth

---

