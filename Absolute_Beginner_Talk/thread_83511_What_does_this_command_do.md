---
title: "What does this command do?"
date: 2005-10-28
forum: Absolute Beginner Talk
---

### Post by racermike1967 on 2005-10-28
I'm interested in programming in C and C++ but I am new to ubuntu and the linux environment.  Can someone tell me what the following command does:
sudo apt-get install build-essential 

What EXACTLY gets installed?

---

### Post by matthew on 2005-10-28
I looked in Synaptic to find the list. Below I tell you how to do that for future reference...it's a nice thing to know. First off, here's what is installed if you install the package "build-essential:"

libc6-dev | libc-dev
gcc (>=4:4.0)
g++ (>=4:4.0)
make
dpkg-dev (>=1.13.5)

---
To find this info in Synaptic search until you find the package you are interested in in the list of packages.

Right click on the package and from the menu choose "properties."

Select the tab labeled "dependencies." This will tell you all/any other files necessary to install your highlighted file.

If you have already installed a package, the tab labeled "installed files" will tell you what and where files were installed when this package was installed, but only for this package, not for its dependencies. This won't tell you anything for packages not already installed.

---

### Post by darth_vector on 2005-10-28
note that "there is no authoratative list" to define the build-essential package, so it may vary a little from time to time depending on the current version of the package. i have the current version and the following were installed:

ISO standard C library
gcc
g++
make
dpkg-dev

---

