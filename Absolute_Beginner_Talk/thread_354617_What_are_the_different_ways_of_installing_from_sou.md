---
title: "What are the different ways of installing from source?"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-02-06
**Objective of this Thread**
To let users post all possible ways of installing from source on this thread

**Problem with installing from source**
Many new users are unfamiliar with installing from source. There are good guides available but, for some reason, not all instructions work for **every case** of installing from source.
[B]
Instructions from ["How to install ANYTHING in Ubuntu"]("http://monkeyblog.org/ubuntu/installing/#source")[/B] ([This is the other link]("http://cutlersoftware.com/ubuntuinstall/")... thanks to bodhi.zazen)
> Source Package (.tar, .tar.gz, .tgz, .tar.bz, ...)
    Note: not all files with an extension named .tar, .tar.gz, and so on are archives with source code in them - they might be precompiled! If the archive is precompiled, there should be an installer or a binary executable inside it.

    Sometimes all you've got is a package full of uncompiled source code. Luckily, you don't need to be a programmer to know how to compile and install a package with source code. Back in the old days, this was the only way to install software on Linux and there is a standard way of installing these files. It will not work in every case, but it will in most (if you have the right dependencies installed). To compile a package you must first extract it somewhere. This is easily done, simply right-click on the package and select Extract Here.

**Nature of Posts this Thread is Intended for**
This thread is designed for **NEWB-PROOF** instructions on how to install **any software** from source and what to do in case they experience problems with it since every package and computer is unique and may encounter different sorts of problems.
[B]
Notes[/B]
Please avoid to be off topic. Please try to post nothing other than suggestions and instructions on how to install software from source

:guitar:

---

### Post by Rui Pais on 2007-02-06
the simpler and the one i always try fist is checkinstall.
```
sudo aptitude install checkinstall
```

After get source code (tar, cvs, svn, what ever), ls to it's folder and:
```
./configure
make
sudo checkinstall -D
```
Easy!
It it works, it will make a nice deb and install it.
to remove:
```
sudo apt-get remove <mygloriouspackage>
```

:)


*NOTE*
**There is no guaranty that checkinstall work for everything.**
Anyway ./configure and make are the base for any source install, no matter if you choose to use checkinstall or not. 
If checkinstall fail should be replaced with the usual '**sudo make install**'.

---

### Post by wersdaluv on 2007-02-06
Upon installing [Kooldock]("http://www.kde-look.org/content/show.php?content=12097"), I have encountered a problem.

**sudo aptitude install checkinstall** worked. 

Then, I tried **./configure**, but there was no configure script.

I continued with make, but it did not work.


Here is what happened:

```
user@Laptop:~$ cd '/home/user/Extracted Files/Kooldock/kooldock'
user@Laptop:~/Extracted Files/Kooldock/kooldock$ ./configure
bash: ./configure: No such file or directory
user@Laptop:~/Extracted Files/Kooldock/kooldock$ make
make: *** No targets specified and no makefile found.  Stop.

```

In a case like this, what could we do?

---

### Post by Rui Pais on 2007-02-06
**There is no guaranty that check install work for everything.**
A generic note:
Anyway  ./configure and make are the base for any source install, no matter if you choose to use checkinstall or not. If checkinstall fail should be replaced with the usual 'make install'.


> **wersdaluv said:**
> Upon installing [Kooldock]("http://www.kde-look.org/content/show.php?content=12097"), I have encountered a problem.

**sudo aptitude install checkinstall** worked. 

Then, I tried **./configure**, but there was no configure script.

I continued with make, but it did not work.


Here is what happened:

```
user@Laptop:~$ cd '/home/user/Extracted Files/Kooldock/kooldock'
user@Laptop:~/Extracted Files/Kooldock/kooldock$ ./configure
bash: ./configure: No such file or directory
v:~/Extracted Files/Kooldock/kooldock$m ake
make: *** No targets specified and no makefile found.  Stop.

```

In a case like this, what could we do?
 
hi wersdaluv,
for all code one download it's a must read the file README or the INSTALL.

in your case try read:
/home/user/Extracted Files/Kooldock/kooldock/INSTALL
;)

---

### Post by Hanzerik on 2007-02-06
Another option for trying applications out, but not installing them system wide:
```

cd
mkdir MyApps
cd apptobuild/
./configure --prefix=$HOME/MyApps/AppName
make
make install

```

This will install the application and all associated files to /home/yourname/MyApps/AppName. In that directory you will more then likely have a bin directory where the executable is placed.
Just type: ./MyApps/Appname/bin/app to run it.

If you don't like the app or don't need it anymore, you can safely delete the Appname directory without any problems.

---

### Post by bodhi.zazen on 2007-02-06
Well, that is a great link but, FYI it is often down :(

I have discussed this with the author and hopefully the problem is solved.

In the event it is not, the page is also available here:

[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/) 

If you like this link, you may want to track this second link :p

---

### Post by ComplexNumber on 2007-02-06
i never had much luck with checkinstall, for some reason. for installing from source, i use paco. there are a few shortcomings to it, though. when a particular install of a package appends to a file (for example, in /etc/gconf), uninstalling the package can become problematic because it doesn't restore the state of the file before it appended to it, but deletes the whole file.

---

### Post by wersdaluv on 2007-02-06
In a problem like this...

```
user@Laptop:~/Extracted Files/BasKet 6.1 Beta 3/basket-1.0$ make
make: *** No targets specified and no makefile found.  Stop.

```

What should I do? I do not think the problem is with the tarballs I download. I think it's with my computer. Everytime I run "make," that thing happens.

---

### Post by bodhi.zazen on 2007-02-06
./configure

make

sudo make install (or sudo checkinstall)

---

### Post by ComplexNumber on 2007-02-06
> **wersdaluv said:**
> In a problem like this...

```
user@Laptop:~/Extracted Files/BasKet 6.1 Beta 3/basket-1.0$ make
make: *** No targets specified and no makefile found.  Stop.

```What should I do? I do not think the problem is with the tarballs I download. I think it's with my computer. Everytime I run "make," that thing happens.
in the case of basKet, there is a configure file, so that should work. do you have the last 20 lines of the output of configure for basKet? the configure script is obviously complaining due to lack of dependencies met.


the following is also part of the problem. there is a gap between "Extracted" and "Files". rename it to say "ExtractedFiles" so there is no space inbetween those 2 words:
> **Extracted Files**/BasKet 6.1 Beta 3/basket-1.0$


THEN run the configure script again with the usual "./configure"

---

### Post by confused57 on 2007-02-06
I recently installed LFS 6.0 & 6.2...it was pretty much cookbook, but there were different ways to "install" the various programs & packages...as someone mentioned, be sure to check out the README file.  I was "kind of" getting the hang of compiling, patching, symlinking, etc, by the time I was finished.

---

### Post by jpkotta on 2007-02-06
> When you're in the correct directory you execute a configure script: ./configure. The purpose of the configure script is usually to check for dependencies and then create the makefile. If the script fails for some reason and tells you to install certain packages, look up the names in Synaptic (Important! If you find packages in Synaptic named almost the same but with a -dev extension, remember to install those as well! They're development packages and are needed for compiling). Don't worry if it complains that there is no configure script - many packages don't come with one! Then you compile it with make and after it's been compiled you can install it. There are two ways:

Here's a tip:  
If the package is in the repos already, and you're just building the latest upstream version, you can easily resolve all of the build dependencies with ```
sudo apt-get build-dep <package>
```
Sorry, it doesn't work with aptitude.  Of course you can supply the -s option and just see what the deps are, then use aptitude.

---

### Post by Rui Pais on 2007-02-11
> **ComplexNumber said:**
> i never had much luck with checkinstall, for some reason. for installing from source ....

I have come to apparent failures in a lot o packages too. Usually only a few compile straight.
 
I found that one have to take special care on the field 'Version', the [3] on the options. 
It only work when it have only **one line** and **a number** somewhere on tag. 
Example are: 3r or 3vers or -svn3b, whatever... usually work.
Something like -cvs or svn or mine_amazing_version fail. Some packages, usually from svn, have the revision repeated on 3 or 4 lines and will failed unless one replaced by one line only.

hope that helps anyone who gets stuck on that.

---

### Post by Perfect Storm on 2007-02-11
uuh...This a big subject. It really depends how the packed the source and with which programs. Some uses Scons/python etc. etc. The best thing to do is to read the documentation from the place you got the source and/or the readme files that comes with it. 
Others don't have a configure script so you have to mover it manually and others again just require a make...

---

