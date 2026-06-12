---
title: "Type &quot;make&quot; to compile the program"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by coubury on 2008-02-14
I have been reading alot of tutorials and i keep seeing

Type "make" to compile the program, Then install  with "make install"

ok so i download a program and extract it to my documents but i cant undertsand were im ment to type make, well i know its in a terminal but im obviously doing it wrong i just clickm terminal and type make and it bring an error saying cannot find specific file which of course is correct

so my question is when i download a program do i extract it? and were to and how do i go about making these commands "Type "make" to compile the program, Then install  with "make install""


Cheers

---

### Post by zerhacke on 2008-02-14
You first need to install the build-essential metapackage.

```
sudo apt-get install build-essential
```

After that, you first run ./configure at a command line, then make, then sudo make install.

---

### Post by bigken on 2008-02-14
move the extracted file/folder to your desktop then in a terminal type cd Desktop
then cd to the folder

---

### Post by hyper_ch on 2008-02-14
and if configure fails it will mostly tell you it needs additional libraries to be installed. Mostly also their developers (-dev) version.

I have seen now a few programs that first require to run ./autogen.sh to actually create the config file. Once you extracted the source, it should contain some basic installation guide and required packages.

---

### Post by bigken on 2008-02-14
what is the name of the program ? have you looked to see if its in synaptic or if there is a deb

---

### Post by coubury on 2008-02-14
Its a driver for my wireless network card

from here

[http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)

this is what it says in the read me file

Type "make" to compile the program. It is known to compile with g++-3.3,
previous version have not been tested and are unsupported.

Then install RutilT with "make install", it must be done as root if you want to
use the built-in helper launcher and/or install it system-wide.

so what would i do? goto a terminal and type

cd Desktop cd rt2500-cvs-daily.tar.gz

is that right?

---

### Post by bigken on 2008-02-14
right click the file and extract it to your desk top 
open a terminal
cd Desktop
cd (name of folder)
make
make install

---

### Post by kpkeerthi on 2008-02-14
Right click the archive and choose extract here. Now cd to the folder that was created.

---

### Post by hyper_ch on 2008-02-14
> **bigken said:**
> right click the file and extract it to your desk top 
open a terminal
cd Desktop
cd (name of folder)
make
make install

that doesn't work ;)

it is
```

sudo make install

```
as then the compiled files will be "scattered" throughout the filesystem to their according places.

---

### Post by bigken on 2008-02-14
have installed build essentials as **zerhacke** said without them you wont be able to compile

---

### Post by bigken on 2008-02-14
you should also take a look [here ]("http://ubuntuforums.org/showthread.php?t=563547&highlight=rt2500")

---

### Post by zvacet on 2008-02-14
[Here](http://www.cutlersoftware.com/ubuntuinstall/)

---

### Post by Crooksey on 2008-02-14
```

./configure
make
sudo make install
```

99 times out of100 that should do it, also there is usualy a file named README, which will tell you how to install it.

---

