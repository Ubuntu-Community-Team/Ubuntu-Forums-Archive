---
title: "[SOLVED] &amp;quot;You must COMPILE. You must COMPILE.&amp;quot;"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by the8thstar on 2007-07-08
One unnerving thing with Linux is the 'compile' thing. I'm still shaking my head in disbelief whenever I download a package that I have to compile with the terminal.

My main complaint is that I don't understand why I have to compile .rpm or tar.gz files; I mean, can't the devs have a normal .deb ready for you? 

My question is: **[COLOR="Blue"]IS THERE AN APPLICATION THAT CONVERTS .BIN, .RPM, TAR.GZ, and TAR.GZ2 files into easy to install .DEB files?[/COLOR]**

---

### Post by chuckyp on 2007-07-08
To avoid your problem you need to search with synaptic make sure the package hasn't already been built.  

With RPM's you can install with a program called alien. (Not recomended to be using RPMS though).

Most tar.gz files are going to be source code so yes, you are going to have to compile those; however, you can use checkinstall when compiling instead of install helps a lot.  Checkinstall will take the source that you just built and make a deb and install it for easy removal.

For a better understanding you need to check out the desktop guide on installing software help.ubuntu.com

---

### Post by the8thstar on 2007-07-08
So I should type:

> checkinstall ~/example.tar.gz

and it will install the example.tar.gz into Ubuntu?

---

### Post by Sef on 2007-07-08
Read [How to Install Anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

---

### Post by por100pre1 on 2007-07-08
Alien can covert some of those files but it is NOT easy...

---

