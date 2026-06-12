---
title: "broken pipe on .deb package?"
date: 2006-01-12
forum: Absolute Beginner Talk
---

### Post by justinesalo on 2006-01-12
[sorry to double post--got no response in the other forum and i'm thinking it was the wrong place for it]

any idea what i can do about this? i have a .deb package and this is what happens--it says something about g++ being missing, but synaptic says i have a bunch of g++ packages (is there a specific one i need?--i have g++ by itself, but there are a bunch of them). any ideas would rock:

veronica@ubuntuvxxx:~/Desktop$ sudo dpkg -i gtkpod-aac_0.99.2-1_i386.deb
(Reading database ...
dpkg: serious warning: files list file for package `g++' missing, assuming package has no files currently installed.
93005 files and directories currently installed.)
Unpacking gtkpod (from gtkpod-aac_0.99.2-1_i386.deb) ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing gtkpod-aac_0.99.2-1_i386.deb (--install):
short read in buffer_copy (backend dpkg-deb during `./usr/bin/gtkpod')
Errors were encountered while processing:
gtkpod-aac_0.99.2-1_i386.deb

---

### Post by kingsidy on 2006-01-12
on the terminal type in > sudo apt-get install build-essential this will install the basic libraries necessary for compiling stuff. I think that would solve your issue. then retry installing the program

---

