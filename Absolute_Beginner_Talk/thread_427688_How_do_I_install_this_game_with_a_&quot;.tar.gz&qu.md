---
title: "How do I install this game with a &quot;.tar.gz&quot; extension?"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by papuccino1 on 2007-04-29
I want to know how to install/use .tar.gz files..


PLEASE step by step instructions. Cause I'm really lost.

---

### Post by yabbadabbadont on 2007-04-29
You should probably provide a link to the main website for the game so that others can read, and then explain, any installation instructions that the author(s) may provide.

---

### Post by starcraft.man on 2007-04-29
tar.gz files are compressed... easy enough. Just right click on the file and click "extract here".

Installation after that depends on whats inside :p. If its debian, double click on it and install the package. If its RPM, you need to use alien to convert it, instructions can be found on the ubuntu guide. If its neither and is binary... you might have to compile or use a script labelled "install" in the folder.

Is this file not in the repos for feisty/edgy? Repos are always the easiest way to install. Mind telling me what game it is?

---

### Post by Seisen on 2007-04-29
The easiest way to install them is to the archive manger in Ubuntu. The other way to install them is in the terminal. To untar them it would like this in the terminal

```
tar xvzf filename.tar.gz
```

---

### Post by black_ice on 2007-04-29
:) 

1- cd to the .tar.gz package directory 

2-write that down 

tar xvf the name of the package.tar.gz 

then cd to extracted directory 

3- ./configure 

4-make 

5-make install 

have fun !

---

### Post by floke on 2007-04-29
1) Check the repositories for the software in the first instance. It will save you time.
2) Extract the tarball (right click and eg select extract here).
3) This will create a file in the same name as the tarball (eg if the tar file is called 'newgame' then this will make a file called 'newgame').
4) Enter the file
5) Read the install instructions file; but it will normally tell you to do a three stage process....
5a) open a terminal (make sure you're in the right place - so you might have to type 'cd /home/[yourname]/Desktop/newgame' (or whatever the path to it is, first) [or 'sudo apt-get install nautilus-open-terminal' will allow you to right click and open the terminal wherever you currently are in nautilus); and type './configure' - this will check to make sure you have the dependencies met.
5b) type 'make'
5c) type 'make install'

Alternatively, look for a '.deb' package of the software, since the file-roller can install this without you having to compile it from source.

Hope this helps.

---

### Post by papuccino1 on 2007-04-29
Ok thanks for all the massive help. However this is chinese to me!!! >_<

What's a reposotorie? 

I found the game in the add/remove program thingy. Hehe I installed it from there. I'd still like to learn how to install using the .tar.gz!!!!

---

### Post by agurk on 2007-04-29
> **papuccino1]What's a reposotorie?[/quote]
A repository (or "repo" for short)  is a collection of software said:**
> https://help.ubuntu.com/community/Repositories[/url]

[QUOTE=papuccino1]I'd still like to learn how to install using the .tar.gz!!!!
.tar.gz means that the file is compressed, just like a .zip file.
If you right-click on the file and choose 'Extract here', it will be decompressed, unpacked. What should happen after that depends on what has been extracted. :)

---

