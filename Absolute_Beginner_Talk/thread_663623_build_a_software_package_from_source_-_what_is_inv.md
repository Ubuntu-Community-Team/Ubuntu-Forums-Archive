---
title: "build a software package from source - what is involved?"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by sipickles on 2008-01-10
Hi,

As a recent windoze user, I am a bit puzzled by building from source.

I am trying to install stackless python from source, from a subversion repository. The website says use this command:

svn checkout [http://svn.python.org/projects/stackless/tags/python-2.51/](http://svn.python.org/projects/stackless/tags/python-2.51/)

Does this just download the source? where to? and how do i then do a build?

I thought I needed to type configure, then make in the folder, but locate python-2.51 doesn't turn up anything on my box.

Thanks for the advice


Simon

---

### Post by Jussi Kukkonen on 2008-01-10
> Does this just download the source? 
Yes
> where to?  
python-2.51/ in current directory, probably.
> and how do i then do a build? 
That depends on the build system, read files README and/or INSTALL in the source directory to find out.
>  I thought I needed to type configure, then make in the folder, but locate python-2.51 doesn't turn up anything on my box. 
locate is not "live", you need to "sudo updatedb" to get the locate database updated (this usually happens once a day).

---

### Post by sipickles on 2008-01-10
Thanks, thats a great help.

Never realised locate wasn't live!

Should I run the ./configure and make in the folder i want it to be installed into?

or will it install over the existing python installation?

---

### Post by sipickles on 2008-01-10
o look the README tells me how.... <blush>

sorry!:lolflag:

---

### Post by PeterJS on 2008-01-10
Looks like the issue is solved, but I'll drop a shameless plug on the end for checkinstall for posterity and google.

The build instrctions are writen in a general enough fashion so that they will work on pretty much any machine without modification. While this is a a good thing, it has the side effect of not being the best way to install something on any machine.

The last step, make install, is actually pretty clever and does a good job of getting the files where they're supposed to be, the downside is that it's a very gerneral tool and doesn't know which package manager to what it's doing or how. In debian, and ubuntu by extension, there's a tool called checkinstall that works  as a wrapper for make install and keeps careful notes on what it does and then tells the package manager, it even produces a nice deb package for future use.

Long story short if you're using a debian based system, when ever you see make install in the directions just remember to substitute in checkinstall. Makes you're life alot cleaner if you ever want to upgrade or remove something built from source.

---

