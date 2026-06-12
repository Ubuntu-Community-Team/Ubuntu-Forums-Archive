---
title: "why 3 different software install applications for ubuntu"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by silent1643 on 2007-05-08
can someome explain why there are 3 different install applications for ubuntu?
automatrix
add and remove programs
and synap

why can't there just be one?

---

### Post by LaRoza on 2007-05-08
Many program rely on other programs, downloading a single file will not work in many cases. If you want to get a single file you can, and if you want an entire package it is just as easy.

edit-Add / Remove programs is good if you want a single application, if you wanted a new desktop environment or a collection of tools, use synaptic.

---

### Post by compmodder26 on 2007-05-08
Well automatix is not an official ubuntu application and is not supported.  It is simply a program that automates installation of certain packages.  Add/Remove applications is a more user-friendly front-end for synaptic.  Synaptic is used for more advanced purposes.  It should be used by more advanced users or when you can't find what you are looking for in Add/Remove applications.

---

### Post by Cypher on 2007-05-08
> **compmodder26 said:**
> Well automatix is not an official ubuntu application and is not supported.  It is simply a program that automates installation of certain packages.  Add/Remove applications is a more user-friendly front-end for synaptic.  Synaptic is used for more advanced purposes.  It should be used by more advanced users or when you can't find what you are looking for in Add/Remove applications.
Spot on, also Add/Remove will automatically direct you to Synaptic if it encounters something that is hard for it to accomplish. I've always just used Synaptic and Automatix2..

---

### Post by Nythain on 2007-05-08
because of one of the main key pro's of linux...
CHOICE

personal preference, theres actually more, dont forget adept (wich blows)
they are all different softwares, written by different people, available to everyone...

---

### Post by starcraft.man on 2007-05-08
> **silent1643 said:**
> can someome explain why there are 3 different install applications for ubuntu?
automatrix
add and remove programs
and synap

why can't there just be one?

First off, Automatix2 isn't an official means of installing things in Ubuntu. You use that at your own discretion to install unofficial apps, you may and often do run into problems when upgrading later.

The one you did miss, is apt-get from the command line.

They each perform a  different function if you ask me. Synaptic package manager lets you modify specific packages or apps installed on your computer (I manually downgraded libwnck to the old version to get Beryl working completely, stupid little workspaces...). Add/Remove is a dumb down version of apt-get in GUI form which will allow novice and new users access to a complete (somewhat) list of programs available for install and then need only push to install. Apt-get is the command line method for installing, its for the more advanced, or those running without a gui, server for instance.

---

### Post by silent1643 on 2007-05-08
right i see both points, just seems like all of them at least add / remove and synap could be under one program.. and maybe have a power mode and a regular mode or something.. but im just nit picking i still love ubuntu :D

---

### Post by mcduck on 2007-05-08
Synaptic is the real thing, giving you all the power of Ubuntu's package management.

Add/Remove was added to get a nice & easy tool for beginners to install selection of the most commpnly used software.

Automatix2 is unofficial, unsupported (by Ubuntu) tool to install some stuff of non-free stuff in an easy way. All the same things can be installed without it, but that requires you to actually read some manual and learn things, which some people don't want to do.

(you forgot about gdebi, apt-get, aptitude, compiling, and whatever tools there are. Linux is all about freedom of choice, including freedom to choose the tool you most like to use.)

I use the Add/Remove thing when I just want to get some new app, but don't really know what I' looking for. If I know the exact name of a package I need, I use apt-get, and for all serious package management Synaptic is my tool of choice :)

---

### Post by Nythain on 2007-05-08
i use synaptic to search package descriptions and browse repos for exact package names... and use aptitude from terminal for any installing and removing needs

---

### Post by mthakur2006 on 2007-05-08
> **silent1643 said:**
> right i see both points, just seems like all of them at least add / remove and synap could be under one program.. and maybe have a power mode and a regular mode or something.. but im just nit picking i still love ubuntu :D

well there is the 'advance' button in add/remove programs ;p

---

### Post by silent1643 on 2007-05-08
> **mcduck said:**
> 
(you forgot about gdebi, apt-get, aptitude, compiling, and whatever tools there are. Linux is all about freedom of choice, including freedom to choose the tool you most like to use.)
)

i had no idea there were that many! lol guess it is a good thing ;)

---

### Post by meborc on 2007-05-08
acctually... there are 3 main ways to install stuff in ubuntu...

1) APT (sudo apt-get install <package>)... synaptic is just a gui for apt
2) DEB (sudo dpkg -i <packagename>.deb)... you can find deb packages of most software in internet and after download you can install them just like that
3) src (./configure && make && sudo make install)... install the package from source code... the most time consuming, but the best (so some would say) way to install software to fit your system perfectly...

automatix, synaptic and add/remove are just frontends of APT... so there are acctually manymanymany ways to install different soft :)

---

### Post by mcduck on 2007-05-08
> **meborc said:**
> acctually... there are 3 main ways to install stuff in ubuntu...

1) APT (sudo apt-get install <package>)... synaptic is just a gui for apt
2) DEB (sudo dpkg -i <packagename>.deb)... you can find deb packages of most software in internet and after download you can install them just like that
3) src (./configure && make && sudo make install)... install the package from source code... the most time consuming, but the best (so some would say) way to install software to fit your system perfectly...

automatix, synaptic and add/remove are just frontends of APT... so there are acctually manymanymany ways to install different soft :)
If you think about it that way then it's just 2 tools :D apt-get, in the end, uses dpkg to install the packages ;)

---

### Post by meborc on 2007-05-08
> **mcduck said:**
> If you think about it that way then it's just 2 tools :D apt-get, in the end, uses dpkg to install the packages ;)

straight from wiki :) > Advanced Packaging Tool, or APT, is a package management system used by Debian GNU/Linux and its derivatives. APT simplifies the process of managing software on Unix-like operating systems, by automating the retrieval, configuration and installation of software packages, either from binary files or by compiling source code.

APT was originally designed as a front-end for dpkg to work with Debian's .deb packages, but it has since been modified to work with the RPM Package Manager system via apt-rpm. The Fink project has ported APT to Mac OS X for some of its own package management tasks, and APT is also available in OpenSolaris (included in Nexenta OS distribution). APT is free software, distributed under the GNU General Public License.

so yes... you are right... but dpkg -i will never figure out the dependencies like apt will :D

EDIT: probably my point was that 1) you can use the repos to install stuff (apt) 2) you can use deb packages to install stuff (ubuntu - debian) 3) you can use src, which works with all linux distros

---

