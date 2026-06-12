---
title: ".bz2"
date: 2005-10-10
forum: Absolute Beginner Talk
---

### Post by nerdman on 2005-10-10
now I can follow tutorials how to install programs when I download the archive then follow the instructions. But now I've downloaded a .bz2 file that comes with no install instructions... generically speaking, what do I do to install one?

---

### Post by Kyral on 2005-10-10
```
bunzip2 <file>
```

Then proceed as normal ;P

---

### Post by nerdman on 2005-10-10
o.o;; as normal? could you... erm, "refresh" my memory on standard procedure? Just to be sure.

---

### Post by Manny C on 2005-10-10
if you have foo.tar.bz2, then to uncompress you need to issue the following command:

```
 tar jxvf foo.tar.bz2 
```

This will decompress the contents of the archive into say a folder named foo.

Then to install a 'typical' program, you issue the following commands:
```
cd foo
./configure --prefix=/usr
make
sudo make install
```

You will probably need to install the build-essential package from the repos:
```
sudo apt-get install build-essential
```
and depending on the program type, various X, Qt and KDE/Gnome libraries. Use synaptic/kynaptic/adept to find which ones are required.

---

### Post by Wolki on 2005-10-10
[QUOTE=nerdman]o.o;; as normal? could you... erm, "refresh" my memory on standard procedure? Just to be sure.[/QUOTE]

Depends on what the normal install procedure for that package is :)
programs are installed differently than themes are installed differently than plugins are installed differently than skins and so on. Not to say that all of one type are installed the same way...

[edit] MannyC, are you sure that's the best way to install software? if you install dirctly into /usr, you'll get a mess of distro- and selfcompiled packages, which can have bad side effects in the long run.
I also recommend using "sudo checkinstall"  instead of "sudo make install". (needs "checkinstall" installed). Will create .deb files for easy removal later.

---

### Post by nerdman on 2005-10-10
ah, I see. .bz2 isn't enough information.

Whats a **.diff** file?

---

### Post by Wolki on 2005-10-10
[QUOTE=nerdman]ah, I see. .bz2 isn't enough information.

Whats a **.diff** file?[/QUOTE]

A .diff contains the difference between a original file and a modified version, basically a patch. You need the exact basic file used for the patch.

---

### Post by Manny C on 2005-10-10
Thanks wolki...will look into that.

---

### Post by Perfect Storm on 2005-10-11
tar --bzip2 -xvf XXXXXXXXX.tar.bz2

---

