---
title: "make install error"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-07-18
```
total 2552
drwxr-xr-x 2 shane shane    4096 2006-07-17 22:30 bin
-rw-r--r-- 1 shane shane       5 2005-11-13 23:53 callgrind.cmd
-rw-r--r-- 1 shane shane   18009 2005-04-03 13:44 COPYING
drwxr-xr-x 2 shane shane    4096 2006-07-17 22:30 CVS
-rw-r--r-- 1 shane shane    1824 2005-12-20 18:00 deneme.swf
drwxr-xr-x 2 root  root     4096 2006-07-17 22:30 doc-pak
-rw-r--r-- 1 shane shane    9922 2005-04-03 13:44 Doxyfile
drwxr-xr-x 6 shane shane    4096 2005-12-20 21:35 f4l-0.2.1
-rw-r--r-- 1 shane shane    5646 2005-12-20 21:35 f4l.kdevelop
-rw-r--r-- 1 shane shane 2515388 2005-12-20 21:35 f4l.kdevelop.pcs
-rw-r--r-- 1 shane shane    1087 2005-12-20 21:35 f4l.kdevses
-rw-r--r-- 1 shane shane     371 2005-07-13 16:43 f4l.pro
-rw-r--r-- 1 shane shane    4451 2005-11-13 08:34 Makefile
drwxr-xr-x 6 shane shane    4096 2006-07-17 22:30 src
drwxr-xr-x 3 shane shane    4096 2006-07-17 22:30 templates
^[[6~shane@amd3400:~/f4l$ sudo make install
make: *** No rule to make target `/usr/share/qt3/mkspecs/default/qmake.conf', needed by `Makefile'.  Stop.
```


what am i doing wrong?

---

### Post by brentoboy on 2006-07-18
what command did you run, and what package are you trying to install? where did you get the tarball? are there any known dependancies?

is this the make error
or a make install error

did you run sudo make install?
or just make install?

Please fill in a bunch more detail about what you are doing, I bet there are a lot of people who can point out ways to help.

---

### Post by OU812 on 2006-07-18
Looks like a missing dependency. Install all dependencies first, then try reinstalling your app.

john

P.S. When everything's installed, run the program from the terminal to find out if there's any other errors.

---

### Post by Sef on 2006-07-18
Have you installed build-essential?

If not, then follow these directions:

1) Open the terminal (For Ubuntu - Applications > Accessories > Terminal)

2) sudo apt-get update

3) sudo aptitude install build-essential

---

### Post by diepruis on 2006-07-18
Looks like you need to run configure.

```

./configure

```

---

### Post by Dinerty on 2006-07-18
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

gives you a good guide for installing anything on Ubuntu and what extra packages you may need

---

### Post by givré on 2006-07-18
> **diepruis said:**
> Looks like you need to run configure.

```

./configure

```

This is the man :cool:

---

### Post by shanepardue on 2006-07-18
thanks for all the responses..i believe it's a dependency issue so i'll look into that..as far as the configure command, i tried that..it's no available with this program.

---

### Post by stephenlittleton on 2007-07-19
Yah, i got the same thing too.

Its for f4l.

One of you smartie smart smarts who thinks you got all the answers, go and try to download a flash program for linux, see the total 1 available.

(Not to view flash, dont start getting your hopes up that you are the next genius to answer the question, this is to make flash)

After you come across F4L, (which looks like utter crap, but if it works, it works), you will notice that the file you download looks like an export utility.  They tell you to run make, but when you do, there is the error.

Now, a lot of you ... for lack of a better term ... PEOPLE, think that you can just ./configure.  Did you even read his post?  There is no file called configure, he dumped the directory for you... yet you look at it, and say to just use ./configure?  

Good one guys.

Well this post is over a year old it looks like, so I doubt anyone will respond or answer the question.  I'll try to post an answer.  I am sick of running crossover and vmware... these simply aren't good enough.  Plus what if i want to do it for free, you suggest I actually pirate software?  Because no one who uses linux in their right mind would actually buy this to have it 'somewhat' run.

:guitar:

---

### Post by stephenlittleton on 2007-07-19
GOT IT...  do this

apt-get install qt3-dev-tools libqt3-mt-dev g++


Dont know which one worked, but I wacked enter and it started making no problem...

Took reading through a spanish (or some language) site to get it... Thanks spanish guys, you rock!


Rock on!
:guitar:

---

### Post by stephenlittleton on 2007-07-19
If you get the error 2, do this to the install directory.  you edit the file;

in f4l-0.2.1/src/flagStonePort/transform-cxx-bsd/transform/FSDefineSound.h:line 140

change FSDefineSound::FSDefineSound to FSDefineSound

then make it.

I guess there is no make install
so look in the 'bin' directory where you are typing make, the 'f4l-0.2.1' directory, the folder called bin, it looks like there is an executable

Just click on it.  (Unless you are in konsole and not a shell, then you can just ./run it)  Otherwise it gives the error, cannot connect to x server.
:guitar:

---

### Post by stephenlittleton on 2007-07-19
Just for reference, this is the error produced when you need to edit the file.

make: *** [sub-src-flagStonePort-transform-cxx-bsd-transform] Error 2

---

### Post by stephenlittleton on 2007-07-19
Great, now if anyone can actually get this to open a FLA or SWF or even use it, let ME know, cause i cant even get it to work, how pathetic.

I guess linux people dont like cartoons made with flash. 
jerks.

---

### Post by diepruis on 2007-07-20
> **stephenlittleton said:**
> Now, a lot of you ... for lack of a better term ... PEOPLE, think that you can just ./configure.  Did you even read his post?  There is no file called configure, he dumped the directory for you... yet you look at it, and say to just use ./configure?

Apologies. In retrospect that seems obvious. But please keep your derogatory comments for another place.

Furthermore, if you don't like the tools that are available currently, why don't you make a new one? That's what Linux is all about, it's not about being handed perfect tools on a silver platter, although that's the way it turns out most of the time. I'm certain there are thousands of users willing to help you create a flash application for Linux, and quite a few companies willing to sponsor work on it.

---

### Post by stephenlittleton on 2007-07-22
> **diepruis said:**
> Apologies. In retrospect that seems obvious. But please keep your derogatory comments for another place.

Furthermore, if you don't like the tools that are available currently, why don't you make a new one? That's what Linux is all about, it's not about being handed perfect tools on a silver platter, although that's the way it turns out most of the time. I'm certain there are thousands of users willing to help you create a flash application for Linux, and quite a few companies willing to sponsor work on it.

Okay okay, In hindsight, I understand but everyone just keeps posting the obvious.  I understand also when you don't, is the same time someone will say, "What is make and how do i download it." 

Nevertheless, Linux programming seems real simple, but I am no programmer.  I am actually trying to go to school to learn to do just that, create GPL Freeware.   But if you want to teach me real quick, how to whip up a program, that would be cool too!

---

### Post by diepruis on 2007-07-23
> **stephenlittleton said:**
> Okay okay, In hindsight, I understand but everyone just keeps posting the obvious.  I understand also when you don't, is the same time someone will say, "What is make and how do i download it." 

Perils of web forum based support I'm afraid.

> **stephenlittleton said:**
> Nevertheless, Linux programming seems real simple, but I am no programmer.  I am actually trying to go to school to learn to do just that, create GPL Freeware.   But if you want to teach me real quick, how to whip up a program, that would be cool too!

Programming is a very difficult skill that takes years to learn and no small amount of talent to master. Still, it richly rewards those with the discipline to study it. If you're interested in learning Linux programming, I'd advise buying a good C++ book (Jesse Liberty's "Learn C++ in 21 days" is a good example) and reading up on gcc, make etc. Also, go check out tldp.org, they have an archive of e-books on Linux programming and so forth. The "Advanced Linux Programming Guide" is very useful if you can find it. Of course, you could also learn Python, Ruby, Java or any one of a multitude of languages, but C++ is the "de-facto" Linux language.

Hope that helps.

---

