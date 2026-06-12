---
title: "[SOLVED] compile .tar.gz"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by skyjacker on 2007-12-12
I have tried for several days to install .tar.gz packages, with no success. Even read most of the threads and web sites on this subject. Please tell me what I am doing (or not doing) that won't let me install.
Here is the instructions from the software's install info. I can't even get this to work. The .tar.gz file is located on my desktop, and I can't even cd to it because I get a message that says there is no such file. Thanks in advance.

The simplest way to compile this package is:

  1. `cd' to the directory containing the package's source code and type  
     `./configure' to configure the package for your system.  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself.

     Running `configure' takes awhile.  While running, it prints some
     messages telling which features it is checking for.

  2. Type `make' to compile the package.

  3. Optionally, type `make check' to run any self-tests that come with
     the package.

  4. Type `make install' to install the programs and any data files and
     documentation.

  5. You can remove the program binaries and object files from the
     source code directory by typing `make clean'.  To also remove the
     files that `configure' created (so you can compile the package for
     a different kind of computer), type `make distclean'.  There is
     also a `make maintainer-clean' target, but that is intended mainly
     for the package's developers.  If you use it, you may have to get
     all sorts of other programs in order to regenerate files that came
     with the distribution.
P.S. detailed instructions if possible.

---

### Post by aysiu on 2007-12-12
What's the program you're trying to install?

---

### Post by kellemes on 2007-12-12
> **skyjacker said:**
> I have tried for several days to install .tar.gz packages, with no success. Even read most of the threads and web sites on this subject. Please tell me what I am doing (or not doing) that won't let me install.
Here is the instructions from the software's install info. I can't even get this to work. The .tar.gz file is located on my desktop, and I can't even cd to it because I get a message that says there is no such file. Thanks in advance.

The simplest way to compile this package is:

  1. `cd' to the directory containing the package's source code and type  
     `./configure' to configure the package for your system.  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself.

     Running `configure' takes awhile.  While running, it prints some
     messages telling which features it is checking for.

  2. Type `make' to compile the package.

  3. Optionally, type `make check' to run any self-tests that come with
     the package.

  4. Type `make install' to install the programs and any data files and
     documentation.

  5. You can remove the program binaries and object files from the
     source code directory by typing `make clean'.  To also remove the
     files that `configure' created (so you can compile the package for
     a different kind of computer), type `make distclean'.  There is
     also a `make maintainer-clean' target, but that is intended mainly
     for the package's developers.  If you use it, you may have to get
     all sorts of other programs in order to regenerate files that came
     with the distribution.
P.S. detailed instructions if possible.


You need to unpack the tar first..
"tar xvzf filename.tar.gz"

Now you can try the instructions..

---

### Post by thelatinist on 2007-12-12
You need to untar the source code to a directory before you can use ./configure or make.  Try this:

```
sudo mkdir ~/src/program_name 
cd ~/src/program_name
tar xvfz ~/Desktop/program_name.tar.gz
./configure
make
make install
make clean
```

To explain these commands:

**sudo mkdir temp-install** creates a temporary directory which you can delete after you're done installing.
**cd temp-install **switches to the directory you just created
**tar xvfz ~/Desktop/something.tar.gz** unzips the file from your desktop to the folder you are currently in. Replace something.tar.gz with your file's name
**./configure** configures the make file for compilation.
**make** makes the package for installation.
**make install** intalls the package you just created using the make command.
**make clean **removes configuration files from the current directory.

It has been suggested to me that one always keep the source files, so I have edited this post to reflect that practice.

---

### Post by mali2297 on 2007-12-12
First install the packages build-essential and checkinstall:
```

sudo apt-get install build-essential checkinstall

```

Then open the archive, suppose it is called foo.tar.gz,
```

tar -xvzf ~/Desktop/foo.tar.gz

```
You will get an output like
```

foo/
foo/man
.
.
.

```
The directory is thus called foo, cd to it:
```

cd foo

```
Now proceed with
```

./configure
make
sudo checkinstall

```
Use here checkinstall instead of *make install*, then you can easily uninstall the program later.

Doesn't work? 
You will often get an error about missing files when running "./configure". This means that you need to install some extra dependencies.

---

### Post by bodhi.zazen on 2007-12-12
> **thelatinist said:**
> You can then delete the temp-install directory, which was only needed for the installation process.  You can choose any name you want intstead of temp-install.

First, nice post.

I would like to add a caution though, I advise you extract to ~/src/program_name .

I would also caution that you should keep the source code in case you need to un-install or update (often you may need to first remove a program, then update). Thus, I save it in ~/src

---

### Post by thelatinist on 2007-12-12
> **bodhi.zazen said:**
> First, nice post.

I would like to add a caution though, I advise you extract to ~/src/program_name .

I would also caution that you should keep the source code in case you need to un-install or update (often you may need to first remove a program, then update). Thus, I save it in ~/src

Thank you, That makes sense, and I shall edit my post to reflect that and change my own practices.

---

### Post by skyjacker on 2007-12-12
> **thelatinist said:**
> You need to untar the source code to a directory before you can use ./configure or make.  Try this:

```
sudo mkdir ~/src/program_name 
cd ~/src/program_name
tar xvfz ~/Desktop/program_name.tar.gz
./configure
make
make install
make clean
```

To explain these commands:

**sudo mkdir temp-install** creates a temporary directory which you can delete after you're done installing.
**cd temp-install **switches to the directory you just created
**tar xvfz ~/Desktop/something.tar.gz** unzips the file from your desktop to the folder you are currently in. Replace something.tar.gz with your file's name
**./configure** configures the make file for compilation.
**make** makes the package for installation.
**make install** intalls the package you just created using the make command.
**make clean **removes configuration files from the current directory.

It has been suggested to me that one always keep the source files, so I have edited this post to reflect that practice. Here is what I got when I tried the first line of the code:

skyjacker@skyjacker-desktop:~$ sudo mkdir ~/src/jpilot-0.99.9.tar.gz
[sudo] password for skyjacker:
mkdir: cannot create directory `/home/skyjacker/src/jpilot-0.99.9.tar.gz': No such file or directory
HELP!!!

---

### Post by mali2297 on 2007-12-12
> **skyjacker said:**
> Here is what I got when I tried the first line of the code:

skyjacker@skyjacker-desktop:~$ sudo mkdir ~/src/jpilot-0.99.9.tar.gz
[sudo] password for skyjacker:
mkdir: cannot create directory `/home/skyjacker/src/jpilot-0.99.9.tar.gz': No such file or directory
HELP!!!

Do
```

mkdir ~/src
mkdir ~/src/jpilot

```

---

### Post by aysiu on 2007-12-12
What's wrong with [enabling extra repositories](http://www.psychocats.net/ubuntu/sources) and then installing jpilot from the repositories? ```
sudo apt-get update
sudo apt-get install jpilot
``` It's [in the Universe repositories](http://packages.ubuntu.com/gutsy/otherosfs/jpilot).

---

### Post by thelatinist on 2007-12-12
While everything we've said is true for installing from source, aysiu is correct: if something is in the repositories it is almost always better to install it from there.  If I had known that was what you were trying to install, I would have suggested it.

---

### Post by skyjacker on 2007-12-12
Thanks to everyone that had a reply. I took the easy way out (I didn't know the program was listed in adept package manager), but took the advice of Aysiu and installed it from there. This forum is GREAT, and makes learning a new OS easier. This thread is solved!!:):)

---

