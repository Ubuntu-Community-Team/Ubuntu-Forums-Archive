---
title: "configure an editor in octave"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by ayesha kalra on 2007-05-29
% I posted this in the programing forum yesterday, but did not get any replies. :(

Hi 

Is there a way to start (open) an editor in Octave when I type 

octave:1> edit hello_world.m

The command should either open the hello_world.m in the editor I configure (if hello_world.m is there in pwd, or it should make a new file called hello_world.m in the present working dir.)
Right now, octave says

parse error: 

syntax error

>>> edit hello_world.m
^

Thanks
Ayesha

---

### Post by tkjacobsen on 2007-05-31
You need to install octave-forge before the "edit" command works.

Then to choose editor, before you start octave (form the terminal)
export EDITOR=gedit

(if gedit is your preferred editor)


EDIT:
Files will by default be in ~/octave/

---

### Post by ayesha kalra on 2007-06-03
Thanks tkjacobsen.


But octave-forge has a lot of packages. I installed the general package, but the edit command still does not work. Is there any particular package I need to install? I do not want to install all the packages though.

Ayesha

---

### Post by tkjacobsen on 2007-06-04
In the newer packages from octave-forge the edit function is in the 'Miscellaneous' package.

---

### Post by ayesha kalra on 2007-06-05
I encountered another error while installing the package - 

This is the error message I get

```
configure: WARNING: no mkoctfile found on path
./configure: line 2386: conftest.cc: command not found
configure: error: Could not run
error: The configure script returned the following error: checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for mkoctfile... no

```

Any clues on how to fix this will really help, also because I plan to use mkoctfile command later on also. 

Thanks
Ayesha

---

### Post by ayesha kalra on 2007-06-05
Never mind I got mkoctfile to work. Atleast now it is showing the usage. I have to test it though and I was able to set gvim as the editor. Thanks to all

---

