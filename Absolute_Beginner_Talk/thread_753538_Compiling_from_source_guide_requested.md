---
title: "Compiling from source guide requested"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by andrewk8 on 2008-04-12
I'm looking for a comprehensive guide to compiling from source.

I'm an experienced Windows user who just installed Ubuntu 7.10 in VirtualBox to give it a try.  There are a couple of pieces of software that I want to try out that aren't available in Add/Remove Programs or Synaptic, so I want to compile them from source.  I haven't done any programming before and don't plan on modifying the programs; I just want to compile them and install.

I've figured out a couple of things on my own, but keep running into problems.  The README files are fairly clear, but they make A LOT of assumptions about the abilities of the person reading the file.  I'm obviously missing some basic concepts.

I've installed 'build-essentials', for example, and got 'xmkmf' to run without errors, but when I run 'make World', I get a lot of errors, including "No such file or directory" errors.  I'm guessing it's because I don't have all of the dependencies.  In this particular case, the README says:

> ... you must have a reasonably recent version of X installed ... requires JPEG and zlib
libraries installed in the system ...

I am a little naive thinking that since GNOME is running, that X is automatically installed.  Some of the "no such file or directory" errors relate to the X11 path.  I've searched Synaptic for X, but I can't figure out what else I need from the list.  Same for JPEG and zlib.

Can someone provide a summary or link for the following questions:
[LIST=1]
[*]additional packages that are required to generate software from source (e.g. build-essential)
[*]addtional packages that are recommended for compiling / installation, but not required (e.g. checkinstall)
[*]summary of procedures for compiling / installing programs
[*]how to check if required dependencies are installed
[*]how to interpret dependency lists in README files to get the right build dependencies
[*]a summary of how to GET the dependencies installed
[*]how to uninstall programs that were compiled from source
[/LIST]

I've found a lot of very-specific answers to very-specific questions, but I haven't been able to put all the pieces together to be able to compile EVERY program from source.

TIA.

---

### Post by spiderbatdad on 2008-04-12
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)
and checkout checkinstall...
[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

Synaptic package manager is the source of the majority of dependencies (and programs) you'll ever need. If not, due to a recently upgraded or deprecated lib, then google the package you need, or search sourceforge.net

---

### Post by sardion on 2008-04-12
Okay, I will try to help you out.  But a "general compiling from source" guide is basically impossible since there is no 100% standard way of writing code.

Most linux programs that come as source work as follows: you download the source (usually a "tarball" .tar.gz), and then you untar it (tar -xzf xxx.tar.gz).  Then cd into the dir and read the README file.

Most commonly, the next step is to run
./configure

This *should* check for required dependencies and tell you if something is missing.
If something is, say for example, zlib, you need to install it form the repos.
Do

apt-cache search zlib   (or use packages.ubuntu.com) to find the package

then install:

aptitude install libzlib
aptitude install libzlib-dev

The -dev package is crucial for building from source (the -dev includes the files needed to compile a program using the library.... to run it just needs the library)

Then you wuld rerun ./configure and see if anything else is missing.  I wish there was a better way to "find" the dependencies but all I can suggest is apt-cache search and packages.ubuntu.com (and googling for "ubuntu PROGRAMNAME compile from source").

After ./configure the next step is usually

make

(or perhaps make ____ but usually just make)

This actually compiles the program.  If there are errors, again, the best plan is to google for the *exact* error text (and also the program name, but if you get no hits with the prog name, use just the error text).  Usually someone knows the problem...

Finally,

make install

This installs the program.

As to removal.... when you run ./configure there are various options you can pass in, including where to install it   ./configure --prefix=/opt/local
for instance will put everything into /opt/local

I usually install things with ./configure --prefix=/opt/local/PROGRAM

Then to remove the program..... rm -fr /opt/local/PROGRAM

Note: if you do not specify a prefix= it will *usually* default to /usr/local so everything will be installed in the same dirs.... removal is then kind of a pain.  (you may need to do sudo make install to install there as well).


I should also point out that it is possible to create your own .deb files, which makes all of the install/removal much easier.... they act just like things from the repos.  That said, they are a bit tricky to build.  Once you master building from source the usual way, the best place to go is the debian website and take a look at the guides on "how to create deb files" or "dpkg" or something along those lines.

Also, most all of us learned to do this but trying, failing, trying again, asking, etc.  So keep at it.

Hope that helps.

---

### Post by vgrisham on 2008-04-12
I've found the following steps work well. I'll use my favorite personal finance manager Kmymoney2 as an example.

1. Download and extract the source code to a folder in your home directory. I create a hidden folder called .install and I keep my installation files there.

2. Make sure you have build-essential installed and if not, install it.

3. Open a terminal and cd to the .install folder and open the folder for your software and code sudo apt-get build-dep kmymoney2. That command will build a list of dependencies and install them.

4. ./configure

5. make

6. sudo make install

I hope that helps.

---

### Post by andrewk8 on 2008-04-15
> **spiderbatdad said:**
> [https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)
and checkout checkinstall...
[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

Synaptic package manager is the source of the majority of dependencies (and programs) you'll ever need. If not, due to a recently upgraded or deprecated lib, then google the package you need, or search sourceforge.net

Exactly what I was looking for.  'checkinstall' was an added bonus.  I don't know why anyone *wouldn't* want to use it.

FYI, I wasn't able to find any links to the CompilingSoftware page from the top of Community Docs.  Looked in obvious places like installing software and installing tarballs, but I couldn't find anything directly discussing compiling.  Maybe it is an orphaned page?

---

### Post by andrewk8 on 2008-04-15
> **sardion said:**
> Most commonly, the next step is to run
./configure

This *should* check for required dependencies and tell you if something is missing.
If something is, say for example, zlib, you need to install it form the repos.
Do

apt-cache search zlib   (or use packages.ubuntu.com) to find the package

then install:

aptitude install libzlib
aptitude install libzlib-dev

The -dev package is crucial for building from source (the -dev includes the files needed to compile a program using the library.... to run it just needs the library)

Then you wuld rerun ./configure and see if anything else is missing.  I wish there was a better way to "find" the dependencies but all I can suggest is apt-cache search and packages.ubuntu.com (and googling for "ubuntu PROGRAMNAME compile from source").

In this particular case, the source code used 'xmkmf' instead of './configure'.  It built the makefile without generating any errors (like configure should?).

Got another hot tip to search for packages containing the missing file.

```
sudo apt-file update
apt-file search [filename]
```

Came close in this case, but still didn't return exactly what I needed.  I did get a reaponse finally on the forum's mail list.

---

