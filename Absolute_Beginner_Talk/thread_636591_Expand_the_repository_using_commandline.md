---
title: "Expand the repository using commandline?"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by Vekin on 2007-12-10
I think I need to install a nvidia driver to fix my little white screen after log in problem. I know it's not compiz/beryl because I haven't even been able to see the desktop yet, it's a fresh install.  And either way, I've removed those through the command line just in case. I think the reason that the command line I'm using isn't working is because I haven't yet been able to expand my repository list.  Anyway to do this through the command line?

This is the command I'm using to install the driver, btw:

sudo apt-get install nvidia-glx-new linux-restricted-modules

It says it's unable to find linux-restricted-modules.  So what I stated up there is my best guess.  Any ideas?

Edit:  I have an Nvidia Geforce 7600 GT, and I'm using Feisty Fawn, if that helps at all.

---

### Post by kevdog on 2007-12-10
You need the version corresponding to your kernel version.

uname-r

Gives kernel version

Search for possible packages:
sudo apt-cache search linux-restricted

This gives lists of packages.  Review the list and then install the one you want.

---

### Post by CatKiller on 2007-12-10
If you want to add new repositories, or enable ones that aren't currently enabled, use ```
sudo nano /etc/apt/sources.list
``` Use ```
sudo aptitude update
``` to refresh the index with files from the new repositories.

---

