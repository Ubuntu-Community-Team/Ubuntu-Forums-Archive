---
title: "how to install mercurial"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by macgywer on 2007-04-27
this is my first post so i say hello to all in the ubuntu forum!

i'm a total newbie so please don't be too rude to me. can someone explain to me how to install mercurial on ubuntu 7.04?
i tried apt-get install mercurial
    E:Couldn't find package mercurial
then i downloaded mercurial-0.9.3.tar.gz from: [http://www.selenic.com/mercurial/wiki/]("http://www.selenic.com/mercurial/wiki/")
   tar xvzf mercurial-0.9.3.tar.gz
   cd mercurial-0.9.3.tar.gz
the next step from the readme is:
   python setup.py install --force
and i get a bunch of errors. here are some of them:
.
.
.
I/usr/include/python2.5 -c mercurial/mpatch.c -o build/temp.linux-i686-2.5/mercurial/mpatch.o 
mercurial/mpatch.c:23:20: error: Python.h: No such file or directory 
mercurial/mpatch.c:24:20: error: stdlib.h: No such file or directory 
mercurial/mpatch.c:25:20: error: string.h: No such file or directory 
mercurial/mpatch.c:44:24: error: sys/types.h: No such file or directory 
mercurial/mpatch.c:45:24: error: arpa/inet.h: No such file or directory 
mercurial/mpatch.c:46:23: error: inttypes.h: No such file or directory 
.
.
.
what am i doing wrong?

---

### Post by xyz on 2007-04-27
If this is what you mean, it's in System > Administration > Synaptic > Search
> Scalable distributed version control system
Mercurial is a fast, lightweight Source Control Management system designed
for efficient handling of very large distributed projects.

Its features include:
 * O(1) delta-compressed file storage and retrieval scheme
 * Complete cross-indexing of files and changesets for efficient exploration
   of project history
 * Robust SHA1-based integrity checking and append-only storage model
 * Decentralized development model with arbitrary merging between trees
 * High-speed HTTP-based network merge protocol
 * Easy-to-use command-line interface
 * Integrated stand-alone web interface
 * Small Python codebase

 Homepage: [http://www.selenic.com/mercurial/](http://www.selenic.com/mercurial/)

---

### Post by macgywer on 2007-04-27
i tried searching in Synaptic Package Manager but it is not there. i'm searching for a manual way to install it.

---

### Post by Outrunner on 2007-04-27
Yes it is, you just need to uncomment the universe lines in /etc/apt/sources.list

---

### Post by macgywer on 2007-04-27
how do i do that? i opened /etc/apt/sources.list and unchecked comunity-maintained open source software (universe) but i don't have any internet connection on the linux maschine. any chance to add it offline?

---

### Post by paparucino on 2007-04-27
> **macgywer said:**
> how do i do that? i opened /etc/apt/sources.list and unchecked comunity-maintained open source software (universe) but i don't have any internet connection on the linux maschine. any chance to add it offline?
In the same way you downloaded the .tar.gz file, download the.deb file from this link
[http://snipurl.com/mercurial](http://snipurl.com/mercurial) (it's a shortened link since the original was too long).
Then open a terminal then

```
sudo dpkgi -i mercurial*.deb

```


then run it

---

### Post by macgywer on 2007-04-27
thanks to all but no luck till now.

terminal:
sudo: dpkgi: command not found
if i double click it i get
Error: Dependency is not satisfiable: Python2.4

is something wrong with my system? is there any way to add programs during installation of ubuntu, like there is in the install of mandriva or suse?

---

### Post by xyz on 2007-04-27
try this:
```
sudo dpkg -i mercurial*.deb
```

---

### Post by paparucino on 2007-04-27
> **macgywer said:**
> thanks to all but no luck till now.

terminal:
sudo: dpkgi: command not found
if i double click it i get
Error: Dependency is not satisfiable: Python2.4

is something wrong with my system? is there any way to add programs during installation of ubuntu, like there is in the install of mandriva or suse?
The first problem is you wrote the command in the incorrect way, the correct sentence is **dpkg -i**     :-)

To solve the second problem you need an internet connection on your linux system then run a program called synaptic, then check all the occurrences of python2.4, click on apply and wait till all the files are installed.
But as said before you need a linux internet connection

---

### Post by macgywer on 2007-04-27
sudo dpkg -i mercurial*.deb worked, but i got a broken package at the end.

...
dpkg: dependency problems prevent configuration of mercurial:
   mercurial depends on python2.4; however:
      package python is not installed.
dpkg: error processing mercurial (--install):
   dependency problems - leaving unconfigured
Errors were encounterd while processing:
   mercurial

i checked in Synaptic Package Manager and it says that i have python v2.5. i think that's the problem. any way to degrade it to 2.4?

what if i download and install Ubuntu 6.06? which python and kernel is used in 6.06?

---

### Post by paparucino on 2007-04-27
> **macgywer said:**
> 

i checked in Synaptic Package Manager and it says that i have python v2.5. i think that's the problem. any way to degrade it to 2.4?

what if i download and install Ubuntu 6.06? which python and kernel is used in 6.06?

You can have python 2.4 and python2.5 on you machine. They can live together. 
If you check the list in synaptic, you'll see a lot python installed :-)

---

