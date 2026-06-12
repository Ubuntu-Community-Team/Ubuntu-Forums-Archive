---
title: "WindowMaker install Problems"
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by Tentacel on 2006-01-15
Hi out there

I'm new to Ubuntu, but worked a little bit with SuSE 8.0 before. There I used the WindowMaker and I want to use it now too. But now there are several problems.
When I use synaptic (I hope you know what I mean because I use the german version of ubuntu) (nearly) everything work's fine, but it looks awfull :(. Most of the text doesn't fit into the belonging boxes. So I downloaded the WindowMaker-0.92.0 Version from the Homepage, opened the INSTALL.txt (surely it is not .txt, but I can't read the file extension) and there I read:
[B]The following software is required to use Window Maker:
- X11R6.x[/B] -> can't find via synaptic
[B]The following is required to build Window Maker:

- Basic obvious stuff
	gcc (or some other ANSI C compiler)[/B]-> instaled via synaptic
**	glibc development files (usually glibc-devel in Linux distributions)**-> can't find via synaptic
**	X development files (XFree86-devel or something similar)**-> can't find via synapticv
[B]- autoconf, automake and libtool
	autoconf 2.54[/B] -> found and installed via synaptic autoconf2.59a-3
**	automake 1.4**-> found and installed via synaptic automake1.9.5-1
**	libtool 1.4.2** -> found and installed via synaptic libtool1.5.6-6
**- Xft2** -> can't find via synaptic
**	and its dependencies (such as freetype2 and fontconfig)** -> found via synaptic but I'm not sure if these are the right files
**	You will also need the development files for it (xft2-devel)** -> can't find via synaptic
when I now run ./configure in the shell (like it is written in the INSTALL.txt) I'll get several error messages like
[B]checking for g++... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check[/B]
then I tried "g+" and pressed "Tab" to check if the command exist and there appears "g++-3.4" in the shell.

now my question is: what have I to do to install WindowMaker

Thank you for the answers

P.S. When I installed everything I surely will come up with some more questions

---

### Post by encompass on 2006-09-02
Are youtrying to build windowmaker from source?  Why?  You should just try to figure out how to make your current installation work.  It is better overall.

---

### Post by bodhi.zazen on 2006-09-02
why not install windowmaker via synaptic.

You may have to enable a few repositories:

edit /etc/atp/sources.list and remove the hash marks (#).

Else install build-essential and checkinstal (sudo apt-get install butild-essential checkinstall)

---

