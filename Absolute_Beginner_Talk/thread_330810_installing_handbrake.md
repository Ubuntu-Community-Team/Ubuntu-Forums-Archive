---
title: "installing handbrake"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by gentlemanmasher on 2007-01-03
I have downloaded handbrake and extraced it.  I now go to that directory and try to configure but get the following error. 
caippers@caippers-desktop:~/handbrake$ ./configure
System: Linux
Endian: little

To build HandBrake, run 'jam'.
caippers@caippers-desktop:~/handbrake$ 

How do I run jam and what is it?

---

### Post by az on 2007-01-03
Jam is a replacement for make.  Not a lot of people use it.

Enable universe and
sudo apt-get install jam

---

### Post by SyvanX on 2007-01-03
It looks like you need jam.

You can get it from the repositories. The included BUILD file says it needs nasm also, so you should pick that up.

```
sudo apt-get install jam nasm
```

then re-run your configure.  
I'm not familiar with jam, but the BUILD file says, after you compile to run
```
jam
```
Hopefully that provides you with more information from there if it doesn't install completely.

---

### Post by gentlemanmasher on 2007-01-03
Well it went through a bunch of stuff then it was done and got me back to my handbrake directory.  I then ran a make and get this:

caippers@caippers-desktop:~/handbrake$ make
make: *** No targets specified and no makefile found.  Stop.
caippers@caippers-desktop:~/handbrake$ 

not sure why but if anyone has installed handbrake some suggestions would be great.

---

### Post by SyvanX on 2007-01-03
> **SyvanX said:**
> 
I'm not familiar with jam, but the BUILD file says, after you compile to run
```
jam
```
Hopefully that provides you with more information from there if it doesn't install completely.

As I  noted above, you need to run "jam" not "make" because jam is a make replacement.  Make sure you installed nasm also.

```
$ sudo jam
```
(I'm guessing it needs to be run as root since I didn't see a manual 'make install' equivalent)

---

### Post by gentlemanmasher on 2007-01-03
I did run jam.  It went through all the operations took about 30 minutes.

---

### Post by SyvanX on 2007-01-03
I'm sorry for my unfamiliarity with jam, but did that install it?

based on this site: [Handbrake Build Source]("http://caenim.com/HandBrake.CLI.Guide/buildSource.php") it looks like it should have ended with *Build Succeeded* and that would have been it?

---

