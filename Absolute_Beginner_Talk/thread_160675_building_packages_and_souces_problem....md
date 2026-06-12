---
title: "building packages and souces problem..."
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by Caligula on 2006-04-15
Well, two more questions, hopefully the last for a while...

1. I'm trying to build the ies4linux, I managed to extract it, installed all dependencies and now I'm trying to put in the command:

> cd ~/Desktop/ies4linux
./configure
make

It comes up with 
> bash: ./configure: No such file or directory

Am I just being stupid or is there a problem?

2. I messed too much with the "sources.list" file, and now every time I go to synaptics it comes up with an error message:

> W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)

Can anybody show me how the file is supposed to look? 
I messed with it too much so now I've got loads of backups and no idea which one to use...

Thanks:)

---

### Post by Qrk on 2006-04-15
Fix the first problem by installing the tools you need to compile. 

```
sudo apt-get install build-essential
```

For the second problem, try the "source o matic" sources.list builder. Howerver, I think your problem may just be temporary. Sometimes the servers can be unreliable. Try apt-get update again to make sure you still have the problem first. 

[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

### Post by Caligula on 2006-04-15
I already have build-essential...

---

### Post by mostwanted on 2006-04-15
To answer 1.

Most likely there is no configure script. It's not a requirement to have a configure script. Do a

```
ls
```

there should be a file called Makefile plus some other files and NO script called configure (prefixing something with ./ in bash means it's a script in the current folder). To install, run
```

sudo make install
```

The make step (by itself) is actually redundant as it will automatically be run when you run make with the install target. I'm not sure why a source installation is always divided into 3 steps, when really it's 2 in all cases (unless it's a really amateur sucky makefile).

---

### Post by Caligula on 2006-04-15
nope... there is no makefile there...

---

### Post by taurus on 2006-04-15
What is the output of this command, in the directory where you want to build ies4linux?
```

ls -la 

```

---

### Post by mostwanted on 2006-04-15
When I think about, no there probably isn't a makefile since it's installing from binary. Maybe there's an install script somewhere. Do as the above poster told you. It should be obvious what to run.

---

### Post by croak77 on 2006-04-15
ies4linux is just a script.
 cd to where you extracted it
 ./ies4linux

Make sure you have wine and cabextract installed.

---

### Post by wolfee on 2006-04-15
when I installed it I just typed 
ies4linux/ies4linux 
And it worked!! I got a lucky guess try it!!
I need help installing tar gz,deb,and rpm anyone want to give a superduper dumb guy a break down step by step on how to do this?

---

### Post by taurus on 2006-04-15
For .deb, open a terminal and type
```

sudo dpkg -i filename.deb

```
For .rpm, do
```

sudo apt-get install alien <-- install package alien first
alien filename.rpm <-- convert the rpm to deb
sudo -i dpkg -r filename.deb 

```
And for tar.gz, do
```

sudo apt-get install build-essential
tar xvzf filename.tar.gz
-or-
tar xvjf filename.tar.bz2
cd filename
./configure
make
sudo make install
-or- 
sudo make checkinstall

```
And of course, read the README or INSTALL first before run the ./configure command...

---

