---
title: "No clue on installing programs"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by 3amConspiracy on 2007-05-15
Okay here's the deal I have absolutely no clue how to work the command line terminal thing. I want to install PengAOL (yes sadly I am still using dial-up :-/) Anyways I have no clue how to extract/ install run a tar.gz file. I already have the file downloaded.  I need to to know step by step everything I should be typing to install these type of files.Everything from extracting to line-commands. Explain it to me as if I am someones tech inept parent. I know it can't be as hard as it seems to me but. And unless there is a new link you have othe then the ones i have checked out around the boards already Those aren't any help to me.

Thanks in advance.

---

### Post by taurus on 2007-05-15
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by Grungydan on 2007-05-15
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

More good reading.

---

### Post by Hobo Joe on 2007-05-15
with the file I tried, when I typed 'configure', it said:
```

bash: ./configure: No such file or directory

```
What am I doing wrong?

---

### Post by taurus on 2007-05-15
What are you trying to install and are you in the right directory when you ran that command, ./configure?

```
ls -la ~/Desktop
```

---

### Post by freebeer on 2007-05-15
have you changed directories to where the configure file is located?  It's been my experience that after untarring the file, an application specific directory is created and the files are unarchived to that location.  You then must cd to that location first before you run the configure file.

---

### Post by Hobo Joe on 2007-05-15
> **taurus said:**
> What are you trying to install and are you in the right directory when you ran that command, ./configure?

```
ls -la ~/Desktop
```

Ok, I was in the right directory, but then I realized that the folder I was trying to install had what that site called a "binary executable".

How can I run one of those?

---

### Post by icechen1 on 2007-05-15
> **3amConspiracy said:**
> Okay here's the deal I have absolutely no clue how to work the command line terminal thing. I want to install PengAOL (yes sadly I am still using dial-up :-/) Anyways I have no clue how to extract/ install run a tar.gz file. I already have the file downloaded.  I need to to know step by step everything I should be typing to install these type of files.Everything from extracting to line-commands. Explain it to me as if I am someones tech inept parent. I know it can't be as hard as it seems to me but. And unless there is a new link you have othe then the ones i have checked out around the boards already Those aren't any help to me.

Thanks in advance.

THis might help you [http://www.yolinux.com/TUTORIALS/LinuxTutorialAOL.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialAOL.html)

---

### Post by taurus on 2007-05-15
> **Hobo Joe said:**
> Ok, I was in the right directory, but then I realized that the folder I was trying to install had what that site called a "binary executable".

How can I run one of those?

Yes, if it comes in a binary.

```
./**filename**
```

---

### Post by 3amConspiracy on 2007-05-16
Thanks for the help everyone. I'm starting to get the hang of it now but when i run the ./configure script I get this message "you must tape ./recompile !!" what do i do now do i just enter ./recompile or did i do something wrong?

---

### Post by eentonig on 2007-05-16
You're probably making this wau to difficult. Is it really necesary to compile a program from source?

Normally, there should be plenty of alternatives in the repo's that you can via a GUI called Synaptic.

Just open System\Administration\Synaptic Package Manager

You'll be prompted to enter your password and will then get a GUI with search capabilities. Search for the program/functionality you need, choose one and mark it for installation. Then click on apply changes et voila....

Even easier when you're confused. Ask here which program will do what you want, and we'll provide you with a one line command to install it.

---

### Post by 3amConspiracy on 2007-05-16
> **eentonig said:**
> You're probably making this wau to difficult. Is it really necesary to compile a program from source?

Normally, there should be plenty of alternatives in the repo's that you can via a GUI called Synaptic.

Just open System\Administration\Synaptic Package Manager

You'll be prompted to enter your password and will then get a GUI with search capabilities. Search for the program/functionality you need, choose one and mark it for installation. Then click on apply changes et voila....

Even easier when you're confused. Ask here which program will do what you want, and we'll provide you with a one line command to install it.

Your probably right I think I am making it way to difficult. But the ./recompile came up on it's on. And after I tried the next command nothing woudl happen. Anyway I did the recompile and got to a point where i typed in ./configure and i got error and it said to check the make.log I did that and got this what it said:

/bin/sh: g++: not found
make[2]: *** [threadELV3.o] Error 127
make[1]: *** [all-recursive] Error 1
make: *** [all-recursive-am] Error 2
g/peng'
g++ -DHAVE_CONFIG_H -I. -I. -I..     -D_REENTRANT -c threadELV3.cpp
make[2]: Leaving directory `/home/jaron/TB/peng/peng'
make[1]: Leaving directory `/home/jaron/TB/peng'

Did I screw up at some point or what. But I'll try the synaptic package manager. I forgot to add I get the whole how to install thing now it's jsut I have and issue installing Peng1.05 liek I said I'm stuck using this crappy aol dial-up

---

### Post by eentonig on 2007-05-16
I don't know what this aol thing is you want to install. What's it's funtionality?

If I search the repo's for anything with "aol,, I get the output below. But maybe there are alternatives to the thing you want.

> rfonteyn@ubuntu:~$ sudo apt-cache search aol
aolserver4 - AOL Web Server 4 (Program)
aolserver4-dev - AOL Web Server 4 (Development Tools)
aolserver4-doc - AOL Web Server 4 (Documentation)
aolserver4-nscache - AOLserver 4 module: Tcl API for AOLserver Caches
aolserver4-nsimap - This is AOLserver 4 module that implements IMAP4 interface
aolserver4-nsldap - AOLServer 4 module for LDAP
aolserver4-nsopenssl - AOLserver 4 module: module for SSL mode.
aolserver4-nspostgres - AOLserver 4 module: Postgres connector
aolserver4-nssha1 - AOLserver4 module: performs SHA1 hashes
aolserver4-nsxml - Module for XML support in aolsever4
grouch.app - AOL and ICQ Instant Messenger client for GNUstep
html-helper-mode - A popular HTML editing mode for emacs
naim - A console client for AOL Instant Messenger and IRC
penggy - connects to AOL via modem or TCP/IP
pork - Console-based AOL Instant Messenger & IRC client
sfront - MPEG 4 Structured Audio decoder
timps - Transparent Instant Messaging Proxy Server
rfonteyn@ubuntu:~$

---

### Post by rich.bradshaw on 2007-05-16
Maybe you should try penggy? As eentonig just suggested. You shouldn't be installing things in the way you rae attempting as it is complex. Not until you really know what you are doing, things are much simpler normally.

try

sudo apt-get install penggy

Then run it 

penggy

and see what happens? It might have an interface or it might not, I've never used it. If it doesn't seem to do anything, try

penggy --help

to see what to do.

---

