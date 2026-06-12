---
title: "noob needs help installing gdesklets (Solved)"
date: 2005-10-25
forum: Absolute Beginner Talk
---

### Post by rlange on 2005-10-25
I would like to install gdesklets 0.35.2. I have download the app and extacted the files. Here is where I am at during the install
```
root@ubuntu:/home/rick/gdesklets-0.35.2 # ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for gcc... gcc
checking whether we are using the GNU C++ compiler... yes
checking whether gcc accepts -g... yes
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is require d for intltool
root@ubuntu:/home/rick/gdesklets-0.35.2 # make
make: *** No targets specified and no makefile found.  Stop.
root@ubuntu:/home/rick/gdesklets-0.35.2 # su -c "make install"
make: *** No rule to make target `install'.  Stop.
root@ubuntu:/home/rick/gdesklets-0.35.2 #

```

thanks for your help

---

### Post by linbetwin on 2005-10-25
Try installing gdesklets through the "Add Application" option in the Applications menu. It worked for me.

---

### Post by davmac on 2005-10-25
Any particular reason why you're installing from source? All I did to install it was to open up a terminal and type "sudo apt-get install gdesklets gdesklets-data".

Then click on System -> Preferences -> Sessions, click on the start up programs tab and add gdesklets.

Hope this helps,

Dave Mac

---

### Post by rlange on 2005-10-25
that version is has worthless desklets as i have tried that and found this out searching the forums. But thanks for the reply

this thread on page 1 is why:

[http://ubuntuforums.org/showthread.php?p=442495#post442495](http://ubuntuforums.org/showthread.php?p=442495#post442495)

---

### Post by Jussi Kukkonen on 2005-10-25
Look at the output from configure, it ends (prematurely) with an error about XML::Parser perl module.

You'll need to search the repositories for the missing dependency, like this 
```
apt-cache search XML::Parser
```
From the results list I'd guess you want to install libxml-parser-perl:
```
sudo apt-get install libxml-parser-perl
```

You might have to remove the configure result files before running it again (*config.status* maybe?).

---

### Post by rlange on 2005-10-25
[QUOTE=Jussi Kukkonen]Look at the output from configure, it ends (prematurely) with an error about XML::Parser perl module.

You'll need to search the repositories for the missing dependency, like this 
```
apt-cache search XML::Parser
```
From the results list I'd guess you want to install libxml-parser-perl:
```
sudo apt-get install libxml-parser-perl
```

You might have to remove the configure result files before running it again (*config.status* maybe?).[/QUOTE]

thanks for your reply here is the code after running the code you posted:

configure: error: Can't find Python.h! You will need the python development package
              to successfully compile gDesklets.

Problem solved.  I found an easy way to get gdesklets working, just upgrade to Breezy from Hoary. Case closed.

---

### Post by Samuli on 2005-10-30
Edit: nevermind :)

---

