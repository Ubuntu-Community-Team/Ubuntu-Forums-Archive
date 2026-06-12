---
title: "How do you install a file?"
date: 2005-12-05
forum: Absolute Beginner Talk
---

### Post by politicaldog on 2005-12-05
Hi,

I've download a file I want to install. Its fsbackup-1.2.tar.gz. How do I start it to load into my system?

Rick

---

### Post by Gray. on 2005-12-05
tar -xvzf /path/to/fsbackup.tar.gz (e.g. if fsbackup.tar.gz is in your home folder it would be tar -xvzf /home/<username>/fsbackup.tar.gz)
Then read the INSTALL or README that is included for instructions on how to install.

---

### Post by ssam on 2005-12-05
have you read [http://help.ubuntu.com/starterguide/C/ch02.html](http://help.ubuntu.com/starterguide/C/ch02.html)

---

### Post by public_void on 2005-12-05
First check if you can't get it via synaptic or apt-get install. If not then go to the terminal and type

tar -xvzf /PathToFile/fsbackup-1.2.tar.gz : Unpacks the .tar.gz and creates a new directory named after the file
cd fsbackup-1.2 : Change directory to that new directory
./configure : Run configure in that Directory
make : Compiles source
sudo make install : Installs program

EDIT: Ahhh, others beat me to it.

---

### Post by politicaldog on 2005-12-05
Ok,

I got the directory created and I am at that prompt.  richard@ubuntu:~/fsbackup-1.2$

I don't understand the rest:

> ./configure : Run configure in that Directory
make : Compiles source
sudo make install : Installs program

---

### Post by gord on 2005-12-05
just type 
```

./configure
make
sudo make install

```

into the terminal

---

### Post by politicaldog on 2005-12-05
I get:


> richard@ubuntu:~/fsbackup-1.2$ ./configure
bash: ./configure: No such file or directory
richard@ubuntu:~/fsbackup-1.2$ make
bash: make: command not found
richard@ubuntu:~/fsbackup-1.2$ sudo make install

<Just Learning...Sorry

---

### Post by cbudden on 2005-12-05
try 
```
 sudo apt-get install build-essential 
```

then try ./configure etc again.

Good luck

---

### Post by ssam on 2005-12-05
you will need to install the compilers be for you can compile source code.

run

```
sudo apt-get build-essential
```

then try again

you will probably get error messages about not having all the required librarys next. post them here and we can help you get those.

---

### Post by politicaldog on 2005-12-05
I get:


[COLOR="Red"]richard@ubuntu:~/fsbackup-1.2$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  binutils dpkg-dev g++ g++-4.0 gcc gcc-4.0 libc6-dev libstdc++6-4.0-dev
  linux-kernel-headers make
Suggested packages:
  binutils-doc debian-keyring gcc-4.0-doc lib64stdc++6 manpages-dev autoconf
  automake1.9 libtool flex bison gcc-doc gcc-4.0-locales libc6-dev-amd64
  lib64gcc1 glibc-doc libstdc++6-4.0-doc stl-manual
Recommended packages:
  libmudflap0-dev
The following NEW packages will be installed:
  binutils build-essential dpkg-dev g++ g++-4.0 gcc gcc-4.0 libc6-dev
  libstdc++6-4.0-dev linux-kernel-headers make
0 upgraded, 11 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/10.2MB of archives.
After unpacking 41.9MB of additional disk space will be used.
Do you want to continue [Y/n]? **y**

Preconfiguring packages ...
Selecting previously deselected package binutils.
(Reading database ... 59101 files and directories currently installed.)
Unpacking binutils (from .../binutils_2.16.1-2ubuntu6_i386.deb) ...
Selecting previously deselected package linux-kernel-headers.
Unpacking linux-kernel-headers (from .../linux-kernel-headers_2.6.11.2-0ubuntu13_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.3.5-1ubuntu12_i386.deb) ...
Selecting previously deselected package gcc-4.0.
Unpacking gcc-4.0 (from .../gcc-4.0_4.0.1-4ubuntu9_i386.deb) ...
Selecting previously deselected package gcc.
Unpacking gcc (from .../gcc_4%3a4.0.1-3_i386.deb) ...
Selecting previously deselected package libstdc++6-4.0-dev.
Unpacking libstdc++6-4.0-dev (from .../libstdc++6-4.0-dev_4.0.1-4ubuntu9_i386.deb) ...
Selecting previously deselected package g++-4.0.
Unpacking g++-4.0 (from .../g++-4.0_4.0.1-4ubuntu9_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.0.1-3_i386.deb) ...
Selecting previously deselected package make.
Unpacking make (from .../archives/make_3.80-9_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.13.10ubuntu4_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.1_i386.deb) ...
Setting up binutils (2.16.1-2ubuntu6) ...

Setting up linux-kernel-headers (2.6.11.2-0ubuntu13) ...
Setting up libc6-dev (2.3.5-1ubuntu12) ...
Setting up gcc-4.0 (4.0.1-4ubuntu9) ...
Setting up gcc (4.0.1-3) ...

Setting up make (3.80-9) ...

Setting up dpkg-dev (1.13.10ubuntu4) ...
Setting up libstdc++6-4.0-dev (4.0.1-4ubuntu9) ...
Setting up g++-4.0 (4.0.1-4ubuntu9) ...
Setting up g++ (4.0.1-3) ...

Setting up build-essential (11.1) ...
richard@ubuntu:~/fsbackup-1.2$ [/COLOR]

THEN I Tried:

richard@ubuntu:~/fsbackup-1.2$ ./configure
bash: ./configure: No such file or direc

AND

richard@ubuntu:~/fsbackup-1.2$ ./configure etc
bash: ./configure: No such file or directory

---

### Post by Harleen on 2005-12-05
I just googled for that package. If I found the correct project, than this is just a perl script, so no compilation is needed. ([http://www.opennet.ru/dev/fsbackup/index_eng.shtml](http://www.opennet.ru/dev/fsbackup/index_eng.shtml))

But I doubt that this is, what you expected, as it runs from command line only. If you are looking for a backup tool, try one from the Ubuntu repository. The package "sbackup" contains a backup utility with a graphical front end. Maybe that's more what you are looking for.

---

### Post by politicaldog on 2005-12-05
Actually I was looking to learn a bit about command line with the help of you knowlegable people and working an app.

Still need some help as of my last post!


Thanks
Rick

---

### Post by Sutekh on 2005-12-05
Good on you for trying to install something yourself...
Can you list the contents of the folder you extracted to?

```

richard@ubuntu:~/fsbackup-1.2$ **ls -l**

```

---

### Post by politicaldog on 2005-12-05
I get:

richard@ubuntu:~/fsbackup-1.2$ ls -l
> total 132
-rw-r--r--  1 richard richard 11356 2001-12-29 04:41 cfg_example
-rw-r--r--  1 richard richard  3419 2002-05-16 09:33 CHANGES
drwxr-xr-x  2 richard richard  4096 2002-05-16 09:36 contrib
-rw-r--r--  1 richard richard 17982 2001-09-18 07:58 COPYING
-rwxr-xr-x  1 richard richard  2828 2002-01-08 01:26 create_backup.sh
-rw-r--r--  1 richard richard  7508 2002-05-16 07:35 FAQ
-rwxr-xr-x  1 richard richard 33240 2002-05-16 07:35 fsbackup.pl
-rwxr-xr-x  1 richard richard  6342 2001-12-09 13:15 install.pl
drwxr-xr-x  2 richard richard  4096 2002-05-16 09:36 modules
-rw-r--r--  1 richard richard 20693 2002-05-16 07:35 README
drwxr-xr-x  2 richard richard  4096 2002-05-16 09:36 scripts
-rw-r--r--  1 richard richard     0 2002-05-16 07:35 TODO
-rw-r--r--  1 richard richard     3 2002-05-16 07:35 VERSIO

---

### Post by CPUFreak91 on 2005-12-05
[QUOTE=politicaldog]

THEN I Tried:

richard@ubuntu:~/fsbackup-1.2$ ./configure
bash: ./configure: No such file or direc

AND

richard@ubuntu:~/fsbackup-1.2$ ./configure etc
bash: ./configure: No such file or directory[/QUOTE]

Well first see if the confiure file is still there :) , then type:
[FONT="Courier New"]bash configure[/FONT]
somehow ./configure doesn't seem to work all the time for me.

Also, i'd really suggest you use Synaptic or apt-get. It's like "lasagna from heaven" -- Garfield

---

### Post by Sutekh on 2005-12-05
It looks like it has it's own install script: install.pl

From the [website]("http://www.opennet.ru/dev/fsbackup/index_eng.shtml")

[i]install.pl

    Script to install fsbackup package and some required perl modules. [/i]

Can you run this file?

---

### Post by Sutekh on 2005-12-05
[http://www.fullspan.com/proj/fsbackup/]("http://www.fullspan.com/proj/fsbackup/")

Is a newer version of the utility, once extracted you can run the fsbackup.sh file to run the utility.  Plus it has good instructions in English not Russian.

---

### Post by politicaldog on 2005-12-05
Ok,

I tried:

> richard@ubuntu:~/fsbackup-1.2$ bash configure
bash: configure: No such file or directory




> 
richard@ubuntu:~/fsbackup-1.2$ install.pl
bash: install.pl: command not found

---

### Post by Sutekh on 2005-12-05
Yup .pl is a PERL script, you'd need to install some PERL packages to get this to work.  ./configure won't work becuase there is no configure script.

Have a look at the other link I posted.

---

### Post by politicaldog on 2005-12-05
Maybe I just picked the wrong file to learn something on!

How do I remove all this?

richard@ubuntu:~$rm /fsbackup-1.2$

---

### Post by Sutekh on 2005-12-05
[QUOTE=politicaldog]Maybe I just picked the wrong file to learn something on!

[/QUOTE] Haha possibly, possibly.  If you want to do all the ./configure and make, make install there are lots of programs to look at. 

Any type of program you'd like to install?

[QUOTE=politicaldog]How do I remove all this?

richard@ubuntu:~$rm /fsbackup-1.2$[/QUOTE]

```

rm -r /fsbackup-1.2

```

---

### Post by politicaldog on 2005-12-05
Nope, Unless I typed it wrong!
> 
richard@ubuntu:~$ rm -r /fsbackup-1.2
rm: cannot remove `/fsbackup-1.2': No such file or directory

---

### Post by Sutekh on 2005-12-05
[QUOTE=politicaldog]Nope, Unless I typed it wrong![/QUOTE]
Whoops sorry, you typed wrong instructions right! From the directory just above fsbackup-1.2

```

rm -r fsbackup-1.2

```

---

### Post by politicaldog on 2005-12-05
Hey,

Thanks to everyone that helped me. That last line removed it.

I think I better look more carefully for the next time....:D 

Rick

---

### Post by kalos on 2005-12-05
from in fsbackup, can you give us the output of ```
ls -l | grep configure
```
(Just copy and paste)

This will list (ls) all of the files in the current directory and then search (grep) for a file called configure.

You might have to be in a subdirectory of fsbackup-1.2 (like src/)

-kalos

---

