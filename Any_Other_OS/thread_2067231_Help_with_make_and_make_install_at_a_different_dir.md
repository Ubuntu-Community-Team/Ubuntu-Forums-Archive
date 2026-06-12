---
title: "Help with make and make install at a different directory"
date: 2012-10-06
forum: Any Other OS
---

### Post by thahgr on 2012-10-06
Hello!

I am trying to install scite, compile the source code but i have a problem.
I am using scientific linux on a computer where I only have one directory.. 

scite requires scintilla installation.. on the readme file there are instructions, but i cant get the command properly..

"To build Scintilla, use the makefile located in the scintilla/gtk directory
    cd scintilla/gtk
    make
    cd ../..

To build and install SciTE, use the makefile located in the scite/gtk directory
    cd scite/gtk
    make
    make install

This installs SciTE into $prefix/bin. The value of $prefix is determined from
the location of Gnome if it is installed. This is usually /usr if installed
with Linux or /usr/local if built from source. If Gnome is not installed
/usr/bin is used as the prefix. The prefix can be overridden on the command
line like "make prefix=/opt" but the same value should be used for both make
and make install as this location is compiled into the executable. The global
properties file is installed at $prefix/share/scite/SciTEGlobal.properties.
The language specific properties files are also installed into this directory."

I get the error "make: Nothing to be done for `all'. "

what is the command I should write exactly?

Thank you in advance!

---

### Post by oldos2er on 2012-10-06
Moved to Other OS/Distro Talk.

---

### Post by thahgr on 2012-10-12
come on, nobody can help with a simple command?

---

### Post by drmrgd on 2012-10-12
What is the exact command you've entered?  The error suggests you typed it incorrectly.  Also, are you in the scintilla/gtk directory when you try to run it?

---

