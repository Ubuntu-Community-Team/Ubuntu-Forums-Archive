---
title: "Problem installing a program via tarbell source~"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by UnknownVariable on 2006-10-02
I download a few different .tar.gz files of source code for some programs I'd like to install. I've tried a few different methods I'd read up on, but this program won't install.

I extract the .tar.gz, navigate to the new folder via terminal, and then...

> **./configure**
bash: ./configure: No such file or directory

   - *I read not all source packs have config files, that's cool, I'll move on.*



**make**
make: *** No targets specified and no makefile found. Stop

   - *Make doesn't work? Kinda odd.*



**sudo make clean install**
make: *** No rule to make target `clean'. Stop.

   - *I thought that command was supposed to install source packs, hm...*


Any ideas? :-k

---

### Post by Sef on 2006-10-02
To compile, you need to install build-essential.  If you haven't installed it, then follow these directions:

Applications > Accessories > Terminal

sudo aptitude update

sudo aptitude install build-essential

---

### Post by UnknownVariable on 2006-10-02
Forgot to mention, build-essential is indeed already installed -- it was the first thing I installed upon loading Ubuntu. :)

---

### Post by po0f on 2006-10-02
UnknownVariable,

If the Makefile isn't horribly big, can you post it here for review?  It looks like there isn't a default target specified.

---

### Post by UnknownVariable on 2006-10-02
Forgive my ignorance, but which file is the makefile? I'm not sure of that...

Also, this happens with two different source packages I'm trying to install from. One of them being Azureus, with the source download URL located [here](http://prdownloads.sourceforge.net/azureus/Azureus_2.5.0.0_source.zip?download), which is 5.6 MB in size, and the second is lolifox, an edited version of firefox, downloadable from [this link](http://lolifox.com/download/lolifox-0.2.4.en-US.linux-i686.tar.gz), and the package is 8.4 MB in size.

---

### Post by po0f on 2006-10-02
UnknownVariable,

For most source tarballs you'll download, the make file will be located either in the top level directory, or in the src/ (or whatever the developer happens to call it) directory, in a file called Makefile (note the capital m).  None of those downloads has a standard Makefile per se, but the Azureus has a file called make.mak, and upon inspection, looks like it's for Mac OSX.

[EDIT]

I looked at the lolifox download closer, and it appears that it's already compiled and ready for use.  There are a bunch of object (.o) files and a file called lolifox-bin (which is the executable).  Looks like you don't have to compile anything today.  :)

---

### Post by UnknownVariable on 2006-10-02
I must have downloaded the wrong Azureus package then, I'll try again with a different package later. :) As for lolifox, I placed the tarbell in /usr/lib and extracted the contents so /usr/lib/lolifox as created with all of the files inside of that. One question now, however, how do I run this program? I know typing **firefox** into the terminal starts up firefox, but this doesn't prove true for lolifox as well.

Thank you for the help, by the way. :) It's appreciated.

---

### Post by po0f on 2006-10-02
UnknownVariable,

Just cd into the directory and run lolifox-bin:
```
$ cd /usr/lib/lolifox
$ ./lolifox-bin
```

There is also a script called run-mozilla.sh in there, but I'm not quite sure how it's used.  It looks like you'd type this after cd'ing into the directory:
```
$ cd /usr/lib/lolifox
$ ./run-mozilla.sh lolifox
```

Try running the lolifox-bin file directly first, as I really  don't know about the script.

---

### Post by UnknownVariable on 2006-10-02
```
$ ./run-mozilla.sh lolifox
./run-mozilla.sh: line 166: lolifox: command not found

$ ./run-mozilla.sh
run-mozilla.sh: Cannot execute .

$./lolifox-bin
./lolifox-bin: error while loading shared libraries: libmozjs.so: cannot open shared object file: No such file or directory
```

Apparently it's very close to the code for Firefox, simply tweaked a bit, so I suppose I'll look into the documentation on Firefox and see if something strikes my eye. :)

---

### Post by po0f on 2006-10-02
UnknownVariable,

In the lolifox tarball I downloaded, there is indeed a libmozjs.so.  Maybe try re-extracting it?

I don't know why I didn't see it before, but there is a lolifox file in there, and it looks like a script.  Run it with the ./ in front of the name after cd'ing into the directory.  Glancing through it real quick reveals that they want you to extract it to /usr/local/lib, but you can change that path to /usr/lib if you wanted to.  It also looks like something called mre is supposed to be installed.  Hope this helps.

---

