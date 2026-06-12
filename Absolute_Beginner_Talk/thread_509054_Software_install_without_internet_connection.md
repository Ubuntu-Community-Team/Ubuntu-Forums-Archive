---
title: "Software install without internet connection"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by NacIK on 2007-07-25
How do you?

---

### Post by waqas_butt0071 on 2007-07-25
well you can do it without internet but u will either need .bin,.deb,.rpm or source files of the software you want to install.

you can download .bin,.rpm,.deb or source files from internet 

or if u want you can give the repositories of you DVD instalation disk and install the software from the dvd.

---

### Post by the_analyzer on 2007-10-14
yes, but can anyone tell me how to compile those stuff, not .deb because that is like an installer, but that .bin or .rpm 
what about those .tar.gz or gz2
how can we compile those?

---

### Post by juantovarm on 2007-10-14
Easy, just download the tar file, extract it, go to the extracted folder, READ EVERYTHING take notes on what dependencies you need, install those and the run in the terminal:

sudo ./configure (if no errors then go to next line)

make (again, if no errors, go to next line)

sudo make install (if no errors then at the end of this cycle, you should have a working program)

This is of course considering you have the build-essentials package installed in your system.

2 things to consider: 

1- it is A LOT EASIER to work with .deb packages, someone else who knows more than your ordinary user took it to him/herself to give the community a working package, eliminating the hassle that comes with working with source code, take advanyage of that.

2-considering that Ubuntu cd images only have the minimal install packages, we can say that it is a distro built around the internet. If you do not have access to the web you won't be able to download packages that are required to install a specific program, since you are not connected to the repositories. You can create your own, but if i am not mistaken, yo also need the web to copy the programs you need. If you want a distro that gives you all the packages it has, try fedora, debian or mandriva (just to name some). You can download up to 3 dvd images in some cases.

This has a lot of information: [https://help.ubuntu.com/](https://help.ubuntu.com/)

My best advice: read and do your homework, when you've finished with that, read on some more and do more homework, that will help you avoid unnecessary headaches :) :guitar:

Remember, everything has a learning cycle

Juan

---

### Post by haldean on 2007-10-14
.deb is actually not an installer (but .bin is ;) ) it's just a compressed package of a precompiled program and necessary files which dpkg - the package installer - copies to the directory tree.

---

