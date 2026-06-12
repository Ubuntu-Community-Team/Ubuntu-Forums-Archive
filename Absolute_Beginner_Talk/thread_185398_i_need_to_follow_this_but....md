---
title: "i need to follow this but..."
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by ph7klw on 2006-05-31
[I]Most of the software below, including this software, installs under /usr/local by default; that is, libraries go in /usr/local/lib, programs in /usr/local/bin, etc. If you don't have root privileges on your machine, you may need to install somewhere else, e.g. under $HOME/install (the install/ subdirectory of your home directory). Most of the programs below use a GNU-style configure script, which means that all you would do to install there would be: 

./configure --prefix=$HOME/install
when configuring the program; the directories $HOME/install/lib etc. are created automatically as needed[/I]



I need to create a lib to put all my lib files when installing a new program...how am I going to do that?

---

### Post by meng on 2006-05-31
> the directories $HOME/install/lib etc. are created automatically as needed

What is it that you're trying to install? And where? And do you not have root privileges on this machine?

---

