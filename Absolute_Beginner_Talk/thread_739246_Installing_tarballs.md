---
title: "Installing tarballs?"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by gazz1982 on 2008-03-29
Ok I'm new to linux, I'm trying to install a module for GRASS GIS using the make command, I currently have the tarball on my desktop and GRASS is located under /usr/lib/grass/ so how and where do i untar to to install the module?

Sorry I'm a complete novice at the moment!

---

### Post by Whiffle on 2008-03-29
First, you untar the tarball, either with an archive manager such as file-roller, or using the tar command (tar zxvf for .tar.gz and tar jxvf for .tar.bz2).

Next, open a terminal and cd into the directory created when you untarred it.  The usual commands are 

./configure
make
make install

However, I would install checkinstall and use that instead of make install, as it will create a handy packages thats easy to uninstall.

---

### Post by gazz1982 on 2008-03-29
it was on my desktop so 
cd /Desktop/r.horizon/
make

returns 
Makefile:9  ../../include/Make/Module.make: No such file or directory
make: *** No rule to make target ' ../../include/Make/Module.make' . Stop.

Any ideas?

---

### Post by bumanie on 2008-03-29
Right click on the tarball and left click extract here.
Open terminal
> cd ~/Desktop --> enter
> cd <name of extracted file> --> enter
./configure
make 
sudo make install

---

### Post by Whiffle on 2008-03-29
Could you post a link to the file?  I'd like to have a look at it and see if it is what I think it is.

---

### Post by gazz1982 on 2008-03-29
there is no configure, says no file or directory

There is a Makefile but returns the same error as above

---

### Post by Whiffle on 2008-03-29
Is there a README or an INSTALL file?

---

### Post by Joeb454 on 2008-03-29
Or even an autconf file?

---

