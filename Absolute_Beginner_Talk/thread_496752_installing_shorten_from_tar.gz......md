---
title: "installing shorten from tar.gz....."
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by centipus on 2007-07-09
so i'm pretty much totally new at this whole linux thing...having a grand ol time so far. this forum is a BIG help, you people are a far out bunch.....

i'm just trying to decode some .shn files using command line, shntool and so on, and it seems i need to install the shorten codec itself. so i download shorten-3.6.1.tar.gz to the desktop, and go to reading up on what to do with compressed archives like this one.

now i'm totally confused....if i even got so far as decompression, i would have no idea at all where or how or what to install and how or where to.......see, i'm kinda lost here, this is probably rudimentary stuff, but i'm just beginning. 

any help would be appreciated, a bunch, a whole bunch

in the future
centipus

---

### Post by KIAaze on 2007-07-09
```
tar -xzvf shorten-3.6.1.tar.gz
cd shorten-3.6.1/
./configure
make
sudo make install

```

If there are any error messages during the configure or make process, post them here.
Usually, it's about missing packages or libraries, in which case you'll have to install them and relaunch the "configure/make/make install" process.

---

### Post by centipus on 2007-07-09
wow thanks for the help KIAaze!!

so i've decompressed the tar.gz, and now i have a folder on the desktop named shorten-3.6.1. i have trouble here

```
shitstellar@shitstellar-desktop:~/Desktop/shorten-3.6.1$ ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
```

thanks again KIAaze!!

centipus

---

### Post by KIAaze on 2007-07-09
```
sudo aptitude install build-essential
```
This will install the essential tools necessary for compiling from source (which is what you're doing).

Note: Can also be done through Synaptic package manager. ;)

edit:
You might want to read one of these articles:
[http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")
[http://www.psychocats.net/ubuntu/installingsoftware]("http://www.psychocats.net/ubuntu/installingsoftware")
[https://help.ubuntu.com/community/SoftwareManagement]("https://help.ubuntu.com/community/SoftwareManagement")

---

### Post by centipus on 2007-07-09
beautiful! thanks and thanks!

i'm decoding some files as we speak....one quick question...the shorten-3.6.1 folder on the desktop, is that where it should be? is there a more apropriate place for it? just curious..

more and more thanks KIA..

centipus

edit:
the links are great, now that i 've compiled from the source once the info will make more sense...

---

### Post by KIAaze on 2007-07-09
**The shorten-3.6.1 folder can be placed anywhere. You can even delete it after installation.**

It's just as if you had downloaded a .rar file in Windows containing a setup.exe.
Both can be deleted after installation.

The difference here is that instead of installing a binary file using a binary, you are installing from the source code.

If you are a programmer, this should make you really happy since you can look at the code, change it and recompile the program. :D
That's what open source means: You get the source code.
Free software means: This source code remains open. Nobody can take it, modify and keep the modifications for himself. The Freedom is protected.

Here's an explanation of every step you do to install from source:

1)Extraction (can be done with right-click/extract too):
```
tar -xzvf shorten-3.6.1.tar.gz
```
If the file ends in tar.bz2, you have to use "tar -xjvf" instead.

2)Change to the created directory:
```
cd shorten-3.6.1/
```

3)Check that all dependencies are met and create the Makefile:
```
./configure
```
(configure is a script present in the extracted folder)

4)Compile the program (i.e: Transform it into an executable):
```
make
```

5)
```
sudo make install
```
Move the compiled binaries, documentation, data, etc to the corresponding system folders and create the shortcuts if any.
This means that theoretically, you could run the program from the folder where you compiled it.
But by doing make install, you're moving them to default directories like /usr/local/bin or /usr/bin so that they can be run from anywhere.

---

### Post by centipus on 2007-07-09
far out....thanks for explaining every step of the process!!

all this linux learnin' has been very exciting so far....not nearly as difficult as i had previously thought....

KIA, you are blessed..

centipus

---

### Post by Rui Pais on 2007-07-09
Hi,
if you install **checkinstall** package you can even make a deb package. 
That make things like upgrade/uninstall/reintsall easier. 

Just replace the 
```
sudo make install
```
by
```
sudo checkinstall -D
```
(D stabs for deb)
:)

---

### Post by girard on 2007-07-10
and now i understand! thanks...

although i'd also like to know what the -xvf options[?] mean. is there like a list of these and what they do?

---

### Post by Malibu Illusion on 2007-07-10
x = extract
v = verbose
f = file

Type this:

```
man tar
```

That will give you more information on the tar application.

---

