---
title: "Help compiling from source"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by aswells on 2006-11-30
I am trying to install a program, wine 0.9.25, from its source code. I downloaded the appropriate tar ball, and this is what happened when I tried to extract and ./configure and make

```

target@target-laptop:~$ tar xjf wine-0.9.25.tar.bz2
target@target-laptop:~$ cd wine-0.9.25/
target@target-laptop:~/wine-0.9.25$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... no
checking for cc... no
checking for cl.exe... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
target@target-laptop:~/wine-0.9.25$ make
make: *** No targets specified and no makefile found. Stop.

```

I am a little confused, because all I have ever read about compiling form source is all you have to do is use the commands
```

./configure
make
sudo make install

```

---

### Post by bmillsap on 2006-11-30
Try installing build-essential:

sudo aptitude build-essential

---

### Post by aysiu on 2006-11-30
Wine 9.22 doesn't do it for you, eh?

---

### Post by aswells on 2006-11-30
> **aysiu said:**
> Wine 9.22 doesn't do it for you, eh?
I am actually going back from 0.9.26; I had hotkeys working in ventrilo, quit on me after I upgraded to 9.26

---

### Post by aswells on 2006-11-30
Installing build-essentials lead to a few other needed dependencys, like flex and bison, but wine is compiling as we speak! Thanks for the quick replys.

---

### Post by aswells on 2006-11-30
For practice, I downloaded the source code for 9.26. When I ran ./configure, I got the following messages.

```

configure: WARNING: Wine will be build without OpenGL or Direct3D support
configure: WARNING: because something is wrong with the OpenGL setup:
configure: WARNING: No OpenGL development headers were found

configure: WARNING: FontForge is missing.
configure: WARNING: Fonts will not be built. Dialog text may be invisible or unaligned.

```

I tried to apt-get these things, but that didnt work.

---

### Post by hod139 on 2006-11-30
[]("http://packages.ubuntu.com/edgy/devel/mesa-common-dev")For OpenGL headers, install mesa-common-dev

---

### Post by aswells on 2006-11-30
Thanks hod139, Ill look around and find out what FontForge is

---

### Post by aswells on 2006-11-30
After installing mesa-common-deb and FontForge, I still get the following message after running ./configure

```

configure: WARNING: Wine will be build without OpenGL or Direct3D support
configure: WARNING: because something is wrong with the OpenGL setup:
configure: WARNING: No OpenGL development headers were found
```

When I searched Synaptic for OpenGL headers, I got a relatively long list, I could just install everything but dont want to accidently break something. 

In case it makes a difference, here are my system specs


Integrated 915 Graphics
1.4 Ghz Celeron M
1 Gig ram

if you need anything else let me know ill be more than happy to get it!

---

### Post by Abild on 2006-11-30
Try running ./configure --help

This will give you a list of all the diffrent parameters the wine configure script accept. Usually you will need to pass several parameters to a configure script to enable or disable features you want or don't want to have.

---

### Post by Revery on 2007-11-19
This is an old thread but I'll post in it anyways as it came up high on the google list and will help someone else later.  To solve the OpenGL headers dependency the package I had to install was libgl1-mesa-dev

---

