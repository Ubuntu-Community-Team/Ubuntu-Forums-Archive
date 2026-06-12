---
title: "g95 installation problem in Ubuntu"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by jlawrence on 2007-01-08
Hi all,

 I have been trying to install g95, as mentioned by the installation file*fortras
1. download the tar file, decompress
2. create link by : sudo ln -s $PWD/g95-install/bin/i686-pc-linux-gnu-g95 /usr/bin/g95
(is "sudo" necessary btw ?)

however an error message will appear everytime i try to compile a simple fortran code
>g95: installation problem, cannot exec 'f951': No such file or directory

Help, please ? or are there any available ubuntu packages for this ?

Thank you in advance,

---

### Post by K.Mandla on 2007-01-08
There doesn't seem to be anything called "g95" in the repositories. What is it? Can you tell us where it's coming from?

---

### Post by jlawrence on 2007-01-09
it is a fortran package, very important for compiling many computational program.
is it possible to have it listed in the repositories?

---

### Post by alvenegas on 2007-09-15
Here is the deb package for g95.  
[http://www.gfd-dennou.org/library/cc-env/g95/index.htm.en](http://www.gfd-dennou.org/library/cc-env/g95/index.htm.en)

Although I installed first from source,
this installation didn't work either for what I wanted to do.  It was complainting
on:
g95: installation problem, cannot exec 'f951': No such file or directory

However the file f951 exist and the g95 link in /usr/bin/ is fine.  File f951 is 
in the lib section, perhaps is a matter of linking it somewhere...the question 
is where?  Anybody knows?

---

### Post by longman on 2007-12-03
A bit late but still:

try to do the following:```

mkdir /tmp/g95
ln -s /path/to/g95 /tmp/g95
```

Where /path/to/g95 is your fortran installation directory

---

