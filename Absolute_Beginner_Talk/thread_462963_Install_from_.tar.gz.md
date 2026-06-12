---
title: "Install from .tar.gz????"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by dcahill on 2007-06-03
I need help to install the latests version of a software package that I downloaded as a tar.gz file. 

The instructions in the readme file copied below are not clear to me and I would appreciate a "translation" to Ubuntu 7.04.  

Unpack the tar.gz file in a source code directory (such as /usr/src
under Slackware) as 'root':

	cd /usr/src
	tar xvfz splat-1.2.0b.tar.gz

This action will generate a subdirectory named splat-1.2.0b.

Next, cd into the directory:

	cd splat-1.2.0b

Invoke the configure script to build SPLAT! and related utilities:

	./configure

If you are 'root', SPLAT! and its related man page and utilities will
be installed after the compilation process is complete.  If not, you
will be prompted to su to 'root' and invoke the install script manually:

	su root
	Password:
	./install all
	exit

Thanks,
Dennis.

---

### Post by Happy_Man on 2007-06-03
Right, get this .tar.gz to your desktop..... and then put the following code into the terminal:

```
cd Desktop
tar -xzvf splat-1.2.0b.tar.gz
cd splat-1.2.0b
./configure
sudo apt-get install build-essential
make
sudo make install
```

Completely Ubuntified.

---

### Post by dcahill on 2007-06-03
Thanks Happy_Man!

Something went wrong when I reached the "make" stuff. 

When I call up the program the old version that I had previously installed shows up. 

This is what what I got when installing:

snip.... (no error messages so far)

Setting up g++ (4.1.2-1ubuntu1) ...

Setting up build-essential (11.3) ...
dcahill@ubuntu:~/Desktop/splat-1.2.0b$ make
make: *** No targets specified and no makefile found.  Stop.
dcahill@ubuntu:~/Desktop/splat-1.2.0b$ sudo make install
make: Nothing to be done for `install'.
dcahill@ubuntu:~/Desktop/splat-1.2.0b$ dcahill@ubuntu:~/Desktop/splat-1.2.0b$ make
bash: dcahill@ubuntu:~/Desktop/splat-1.2.0b$: No such file or directory
dcahill@ubuntu:~/Desktop/splat-1.2.0b$ make: *** No targets specified and no makefile found.  Stop.
bash: make:: command not found
dcahill@ubuntu:~/Desktop/splat-1.2.0b$ dcahill@ubuntu:~/Desktop/splat-1.2.0b$ sudo make install
bash: dcahill@ubuntu:~/Desktop/splat-1.2.0b$: No such file or directory
dcahill@ubuntu:~/Desktop/splat-1.2.0b$ make: Nothing to be done for `install'.
> dcahill@ubuntu:~/Desktop/splat-1.2.0b$ 
>

---

### Post by taurus on 2007-06-03
Can you post the complete output of your screen when you run

```
./configure
```

---

### Post by dcahill on 2007-06-03
Here it is:

dcahill@ubuntu:~$ cd Desktop
dcahill@ubuntu:~/Desktop$ tar -xzvf splat-1.2.0b.tar.gz
splat-1.2.0b/
splat-1.2.0b/docs/
splat-1.2.0b/docs/man/
splat-1.2.0b/docs/man/splat.1
splat-1.2.0b/docs/man/docmaker
splat-1.2.0b/docs/man/splat.man
splat-1.2.0b/docs/pdf/
splat-1.2.0b/docs/pdf/splat.pdf
splat-1.2.0b/docs/postscript/
splat-1.2.0b/docs/postscript/splat.ps
splat-1.2.0b/docs/text/
splat-1.2.0b/docs/text/splat.txt
splat-1.2.0b/docs/text/spanish/
splat-1.2.0b/docs/text/spanish/splat.txt
splat-1.2.0b/utils/
splat-1.2.0b/utils/usgs2sdf.c
splat-1.2.0b/utils/postdownload
splat-1.2.0b/utils/README
splat-1.2.0b/utils/install
splat-1.2.0b/utils/fontdata.c
splat-1.2.0b/utils/citydecoder.c
splat-1.2.0b/utils/build
splat-1.2.0b/utils/fips.txt
splat-1.2.0b/utils/s.fnt.gz
splat-1.2.0b/utils/srtm2sdf.c
splat-1.2.0b/build
splat-1.2.0b/CHANGES
splat-1.2.0b/clean
splat-1.2.0b/configure
splat-1.2.0b/COPYING
splat-1.2.0b/fontdata.h
splat-1.2.0b/install
splat-1.2.0b/itm.cpp
splat-1.2.0b/README
splat-1.2.0b/README2
splat-1.2.0b/sample.lrp
splat-1.2.0b/smallfont.h
splat-1.2.0b/splat.lrp
splat-1.2.0b/splat.cpp
splat-1.2.0b/splat-1.2.0b.lsm
splat-1.2.0b/splat-1.2.0b.tar.gz
dcahill@ubuntu:~/Desktop$ cd splat-1.2.0b
dcahill@ubuntu:~/Desktop/splat-1.2.0b$ ./configure

       ****************************************************************
       **    Welcome to SPLAT! Terrain Analysis Software by KD2BD    **
       ****************************************************************

               Now building SPLAT! and associated utilities...

Compiling SPLAT!... ./build: line 12: g++: command not found
Done!
Compiling citydecoder... Done!
Compiling usgs2sdf... Done!
Compiling srtm2sdf... srtm2sdf.c:16:19: error: bzlib.h: No such file or directory
srtm2sdf.c:187: error: expected ‘)’ before ‘*’ token
srtm2sdf.c: In function ‘LoadSDF_BZ’:
srtm2sdf.c:254: error: ‘BZFILE’ undeclared (first use in this function)
srtm2sdf.c:254: error: (Each undeclared identifier is reported only once
srtm2sdf.c:254: error: for each function it appears in.)
srtm2sdf.c:254: error: ‘bzfd’ undeclared (first use in this function)
srtm2sdf.c:273: warning: implicit declaration of function ‘BZ2_bzReadOpen’
srtm2sdf.c:275: error: ‘BZ_OK’ undeclared (first use in this function)
srtm2sdf.c:280: warning: implicit declaration of function ‘BZfgets’
srtm2sdf.c:280: warning: passing argument 1 of ‘sscanf’ makes pointer from integer without a cast
srtm2sdf.c:281: warning: passing argument 1 of ‘sscanf’ makes pointer from integer without a cast
srtm2sdf.c:282: warning: passing argument 1 of ‘sscanf’ makes pointer from integer without a cast
srtm2sdf.c:283: warning: passing argument 1 of ‘sscanf’ makes pointer from integer without a cast
srtm2sdf.c:287: warning: passing argument 1 of ‘sscanf’ makes pointer from integer without a cast
srtm2sdf.c:291: warning: implicit declaration of function ‘BZ2_bzReadClose’
Done!
Compiling fontdata... fontdata.c:34:18: error: zlib.h: No such file or directory
fontdata.c: In function ‘main’:
fontdata.c:45: warning: implicit declaration of function ‘gzopen’
fontdata.c:45: warning: assignment makes pointer from integer without a cast
fontdata.c:61: warning: implicit declaration of function ‘gzgetc’
fontdata.c:78: warning: implicit declaration of function ‘gzclose’
Done!

To install SPLAT! and its associated utilities, please
su to 'root' and execute the install script as follows:

        ./install all

Don't forget to read the documentation under the docs directory
as well as the various README files in the splat and splat/utils
directories.  Enjoy the program!  73, de John, KD2BD
dcahill@ubuntu:~/Desktop/splat-1.2.0b$ sudo apt-get install build-essential
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev g++ g++-4.1 libstdc++6-4.1-dev
Suggested packages:
  debian-keyring gcc-4.1-doc lib64stdc++6 libstdc++6-4.1-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 libstdc++6-4.1-dev
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 4368kB of archives.
After unpacking 17.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libstdc++6-4.1-dev g++-4.1 g++ dpkg-dev build-essential
Install these packages without verification [y/N]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main libstdc++6-4.1-dev 4.1.2-0ubuntu4 [1632kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main g++-4.1 4.1.2-0ubuntu4 [2581kB]    
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main g++ 4:4.1.2-1ubuntu1 [1428B]       
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main dpkg-dev 1.13.24ubuntu6 [147kB]    
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main build-essential 11.3 [6974B]       
Fetched 4368kB in 41s (104kB/s)                                                
Selecting previously deselected package libstdc++6-4.1-dev.
(Reading database ... 164673 files and directories currently installed.)
Unpacking libstdc++6-4.1-dev (from .../libstdc++6-4.1-dev_4.1.2-0ubuntu4_i386.deb) ...
Selecting previously deselected package g++-4.1.
Unpacking g++-4.1 (from .../g++-4.1_4.1.2-0ubuntu4_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.1.2-1ubuntu1_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.13.24ubuntu6_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3_i386.deb) ...
Setting up dpkg-dev (1.13.24ubuntu6) ...
Setting up libstdc++6-4.1-dev (4.1.2-0ubuntu4) ...
Setting up g++-4.1 (4.1.2-0ubuntu4) ...
Setting up g++ (4.1.2-1ubuntu1) ...

Setting up build-essential (11.3) ...
dcahill@ubuntu:~/Desktop/splat-1.2.0b$ make
make: *** No targets specified and no makefile found.  Stop.
dcahill@ubuntu:~/Desktop/splat-1.2.0b$ sudo make install
make: Nothing to be done for `install'.
dcahill@ubuntu:~/Desktop/splat-1.2.0b$ dcahill@ubuntu:~/Desktop/splat-1.2.0b$ make
bash: dcahill@ubuntu:~/Desktop/splat-1.2.0b$: No such file or directory
dcahill@ubuntu:~/Desktop/splat-1.2.0b$ make: *** No targets specified and no makefile found.  Stop.
bash: make:: command not found
dcahill@ubuntu:~/Desktop/splat-1.2.0b$ dcahill@ubuntu:~/Desktop/splat-1.2.0b$ sudo make install
bash: dcahill@ubuntu:~/Desktop/splat-1.2.0b$: No such file or directory
dcahill@ubuntu:~/Desktop/splat-1.2.0b$ make: Nothing to be done for `install'.
> dcahill@ubuntu:~/Desktop/splat-1.2.0b$ 
>

---

### Post by taurus on 2007-06-03
After you installed the build-essential package, you need to run ./configure again.

```
./configure
make
sudo make install
```

---

### Post by dcahill on 2007-06-03
I did everything over again and this is what I get:

dcahill@ubuntu:~$ cd Desktop
dcahill@ubuntu:~/Desktop$ cd splat-1.2.0b
dcahill@ubuntu:~/Desktop/splat-1.2.0b$ ./configure
       ****************************************************************
       **    Welcome to SPLAT! Terrain Analysis Software by KD2BD    **
       ****************************************************************

               Now building SPLAT! and associated utilities...

Compiling SPLAT!... splat.cpp:34:19: error: bzlib.h: No such file or directory
splat.cpp:1575: error: ‘BZFILE’ was not declared in this scope
splat.cpp:1575: error: ‘bzfd’ was not declared in this scope
splat.cpp:1575: error: expected primary-expression before ‘unsigned’
splat.cpp:1575: error: initializer expression list treated as compound expression
splat.cpp:1576: error: expected ‘,’ or ‘;’ before ‘{’ token
splat.cpp: In function ‘int LoadSDF_BZ(char*)’:
splat.cpp:1644: error: ‘BZFILE’ was not declared in this scope
splat.cpp:1644: error: ‘bzfd’ was not declared in this scope
splat.cpp:1691: error: ‘BZ2_bzReadOpen’ was not declared in this scope
splat.cpp:1693: error: ‘BZ_OK’ was not declared in this scope
splat.cpp:1705: error: ‘BZ_OK’ was not declared in this scope
splat.cpp:1710: error: ‘BZfgets’ cannot be used as a function
splat.cpp:1711: error: ‘BZfgets’ cannot be used as a function
splat.cpp:1712: error: ‘BZfgets’ cannot be used as a function
splat.cpp:1713: error: ‘BZfgets’ cannot be used as a function
splat.cpp:1718: error: ‘BZfgets’ cannot be used as a function
splat.cpp:1731: error: ‘BZ2_bzReadClose’ was not declared in this scope
Done!
Compiling citydecoder... Done!
Compiling usgs2sdf... Done!
Compiling srtm2sdf... srtm2sdf.c:16:19: error: bzlib.h: No such file or directory
srtm2sdf.c:187: error: expected ‘)’ before ‘*’ token
srtm2sdf.c: In function ‘LoadSDF_BZ’:
srtm2sdf.c:254: error: ‘BZFILE’ undeclared (first use in this function)
srtm2sdf.c:254: error: (Each undeclared identifier is reported only once
srtm2sdf.c:254: error: for each function it appears in.)
srtm2sdf.c:254: error: ‘bzfd’ undeclared (first use in this function)
srtm2sdf.c:273: warning: implicit declaration of function ‘BZ2_bzReadOpen’
srtm2sdf.c:275: error: ‘BZ_OK’ undeclared (first use in this function)
srtm2sdf.c:280: warning: implicit declaration of function ‘BZfgets’
srtm2sdf.c:280: warning: passing argument 1 of ‘sscanf’ makes pointer from integer without a cast
srtm2sdf.c:281: warning: passing argument 1 of ‘sscanf’ makes pointer from integer without a cast
srtm2sdf.c:282: warning: passing argument 1 of ‘sscanf’ makes pointer from integer without a cast
srtm2sdf.c:283: warning: passing argument 1 of ‘sscanf’ makes pointer from integer without a cast
srtm2sdf.c:287: warning: passing argument 1 of ‘sscanf’ makes pointer from integer without a cast
srtm2sdf.c:291: warning: implicit declaration of function ‘BZ2_bzReadClose’
Done!
Compiling fontdata... fontdata.c:34:18: error: zlib.h: No such file or directory
fontdata.c: In function ‘main’:
fontdata.c:45: warning: implicit declaration of function ‘gzopen’
fontdata.c:45: warning: assignment makes pointer from integer without a cast
fontdata.c:61: warning: implicit declaration of function ‘gzgetc’
fontdata.c:78: warning: implicit declaration of function ‘gzclose’
Done!

To install SPLAT! and its associated utilities, please
su to 'root' and execute the install script as follows:

        ./install all

Don't forget to read the documentation under the docs directory
as well as the various README files in the splat and splat/utils
directories.  Enjoy the program!  73, de John, KD2BD
dcahill@ubuntu:~/Desktop/splat-1.2.0b$ sudo apt-get install build-essential
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dcahill@ubuntu:~/Desktop/splat-1.2.0b$ ./configure

       ****************************************************************
       **    Welcome to SPLAT! Terrain Analysis Software by KD2BD    **
       ****************************************************************

               Now building SPLAT! and associated utilities...

Compiling SPLAT!... splat.cpp:34:19: error: bzlib.h: No such file or directory
splat.cpp:1575: error: ‘BZFILE’ was not declared in this scope
splat.cpp:1575: error: ‘bzfd’ was not declared in this scope
splat.cpp:1575: error: expected primary-expression before ‘unsigned’
splat.cpp:1575: error: initializer expression list treated as compound expression
splat.cpp:1576: error: expected ‘,’ or ‘;’ before ‘{’ token
splat.cpp: In function ‘int LoadSDF_BZ(char*)’:
splat.cpp:1644: error: ‘BZFILE’ was not declared in this scope
splat.cpp:1644: error: ‘bzfd’ was not declared in this scope
splat.cpp:1691: error: ‘BZ2_bzReadOpen’ was not declared in this scope
splat.cpp:1693: error: ‘BZ_OK’ was not declared in this scope
splat.cpp:1705: error: ‘BZ_OK’ was not declared in this scope
splat.cpp:1710: error: ‘BZfgets’ cannot be used as a function
splat.cpp:1711: error: ‘BZfgets’ cannot be used as a function
splat.cpp:1712: error: ‘BZfgets’ cannot be used as a function
splat.cpp:1713: error: ‘BZfgets’ cannot be used as a function
splat.cpp:1718: error: ‘BZfgets’ cannot be used as a function
splat.cpp:1731: error: ‘BZ2_bzReadClose’ was not declared in this scope
Done!
Compiling citydecoder... Done!
Compiling usgs2sdf... Done!
Compiling srtm2sdf... srtm2sdf.c:16:19: error: bzlib.h: No such file or directory
srtm2sdf.c:187: error: expected ‘)’ before ‘*’ token
srtm2sdf.c: In function ‘LoadSDF_BZ’:
srtm2sdf.c:254: error: ‘BZFILE’ undeclared (first use in this function)
srtm2sdf.c:254: error: (Each undeclared identifier is reported only once
srtm2sdf.c:254: error: for each function it appears in.)
srtm2sdf.c:254: error: ‘bzfd’ undeclared (first use in this function)
srtm2sdf.c:273: warning: implicit declaration of function ‘BZ2_bzReadOpen’
srtm2sdf.c:275: error: ‘BZ_OK’ undeclared (first use in this function)
srtm2sdf.c:280: warning: implicit declaration of function ‘BZfgets’
srtm2sdf.c:280: warning: passing argument 1 of ‘sscanf’ makes pointer from integer without a cast
srtm2sdf.c:281: warning: passing argument 1 of ‘sscanf’ makes pointer from integer without a cast
srtm2sdf.c:282: warning: passing argument 1 of ‘sscanf’ makes pointer from integer without a cast
srtm2sdf.c:283: warning: passing argument 1 of ‘sscanf’ makes pointer from integer without a cast
srtm2sdf.c:287: warning: passing argument 1 of ‘sscanf’ makes pointer from integer without a cast
srtm2sdf.c:291: warning: implicit declaration of function ‘BZ2_bzReadClose’
Done!
Compiling fontdata... fontdata.c:34:18: error: zlib.h: No such file or directory
fontdata.c: In function ‘main’:
fontdata.c:45: warning: implicit declaration of function ‘gzopen’
fontdata.c:45: warning: assignment makes pointer from integer without a cast
fontdata.c:61: warning: implicit declaration of function ‘gzgetc’
fontdata.c:78: warning: implicit declaration of function ‘gzclose’
Done!

To install SPLAT! and its associated utilities, please
su to 'root' and execute the install script as follows:

        ./install all

Don't forget to read the documentation under the docs directory
as well as the various README files in the splat and splat/utils
directories.  Enjoy the program!  73, de John, KD2BD
dcahill@ubuntu:~/Desktop/splat-1.2.0b$ make
make: *** No targets specified and no makefile found.  Stop.
dcahill@ubuntu:~/Desktop/splat-1.2.0b$ sudo make install
make: Nothing to be done for `install'.
dcahill@ubuntu:~/Desktop/splat-1.2.0b$

---

### Post by Seisen on 2007-06-03
After running ./configure put this in terminal. 

```
sudo ./install all
```

---

### Post by lambros on 2007-06-03
I think you need to install the libbz2-dev package.  This is the relevant line of the output showing the error:

```
Compiling SPLAT!... splat.cpp:34:19: error: bzlib.h: No such file or directory
```

Open a terminal and run this command:

```
sudo aptitude install libbz2-dev
```

Then rerun the ./configure step and continue from there.

Lambros

---

### Post by dcahill on 2007-06-03
OK that last tip did it. It seems to be running OK now. Thank you all for the help!

---

### Post by Happy_Man on 2007-06-03
No, wait, I agree w/ Seisen, the configure script compiled it and all, he just needs to do ./install all, like the configure script said.

EDIT: Oh, ok, nvm. Glad that it's all worked out.

---

