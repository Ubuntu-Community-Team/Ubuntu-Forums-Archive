---
title: "Giving up: want to install pdfedit, need boost library, installing boost fails"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by fsando on 2007-01-02
I want to install pdfedit
pdfedit not in synaptic package manager (is there a repo I should know about?)
Downloaded sources via pdfedit homepage ([http://sourceforge.net/projects/pdfedit](http://sourceforge.net/projects/pdfedit))
Tried to install: './configure'
Turns out boost library is needed
Boost library not in synaptic package manager (perhaps another repo?)
Downloaded sources via boost homepage ([http://www.boost.org/](http://www.boost.org/))
Tried to install boost library but failed
Not sure what to do :???:

---

### Post by oyvindaa on 2007-01-02
How did the boost library fail to install?

---

### Post by fsando on 2007-01-02
First I ran './configure':
```
xxx@xxxxxx:~/Desktop/boost_1_33_1$ ./configure
Building Boost.Jam with toolset gcc... tools/build/jam_src/bin.linuxx86/bjam
Detecting Python version... 2.4
Detecting Python root... /usr
Python support?... yes.
Unicode/ICU support for Boost.Regex?... no.
Generating Makefile...

```
After that I ran 'make'
It takes in the vicinity of 20 minutes or so (didn't time it) it ends with something like this (I am unsure of the exact wording - will run the the command again though if necessary):
updating 238 objects
12 objects failed
From their website it should be installed in /usr/local/bin/boost-x_x
Nothing turns up there. There are other instructions on their site that I do not quite understand. 
I really only want pdfedit, but it needs the boost library - perhaps there is a prebuild version somewhere? Or maybe the boost library is generally needed so I might as well get it working - it's just head on into linux ](*,) :D

---

### Post by po0f on 2007-01-02
fsando,

Boost is in the repos, do a search in Synaptic.  You'll want [libboost-dbg](http://packages.ubuntu.com/edgy/libdevel/libboost-dbg) as well as [libboost-dev](http://packages.ubuntu.com/edgy/libdevel/libboost-dev) most likely.

---

### Post by fsando on 2007-01-03
Thanks
It wasn't obvious to me that boost library was libboost.
But new problems arise: It needed something related to qt3 so installed libqt3-mt-dev (and some other libqt3). It says on pdfedit homepage that it must be qt3 not qt4.
Now ./configure runs apparently fine though one warning:

```
config.status: WARNING:  config.pro.in.in seems to ignore the --datarootdir setting
```

But now make complains (several times) about missing gmake
```
/bin/sh: gmake: not found
```
and:
```
Can't find Qt library. No QTDIR set
```
and ends with:
```
make: *** [src] Error 2
```

---

