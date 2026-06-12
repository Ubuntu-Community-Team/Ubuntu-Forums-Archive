---
title: "[SOLVED] Unable to update, remove or fix"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by OldTimeTech on 2007-10-13
My update manager froze this morning on a gnucash update.

I've tried to fix with Synaptic....but I get a message that gnucash has a problem and you should fix with....then doesn't give a fix.

Went to terminal....tried all of the below:

marianne@rebelwoman:~$ sudo dpkg -r gnucash
Password:
dpkg: error processing gnucash (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 gnucash
marianne@rebelwoman:~$ sudo apt-get install gnucash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  gnucash: Depends: gnucash-common (>= 2.2.1-1ubuntu4~feisty1) but 2.0.5-1ubuntu1~feisty1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
marianne@rebelwoman:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libgsf-gnome-1-114 guile-g-wrap mesa-common-dev libreadline5-dev
  libglu1-mesa-dev guile-1.6-dev guile-library libffi4-dev
  libgwrap-runtime0-dev g-wrap libgl1-mesa-dev libncurses5-dev
  libgwrap-runtime0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gnucash gnucash-common
Suggested packages:
  gnucash-sql
The following packages will be upgraded:
  gnucash gnucash-common
2 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B/5726kB of archives.
After unpacking 16.4kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error processing gnucash (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 gnucash
E: Sub-process /usr/bin/dpkg returned an error code (1)
marianne@rebelwoman:~$ 

At this point....I am willing to be rid of gnucash and all it's dependencies until I install the new gutsy.

But I need this version fixed at the moment, and I need to learn how to fix this if it happens on another program.

Thanks

---

### Post by Pumalite on 2007-10-13
you might want to try:

sudo dpkg --remove --force-remove-reinstreq gnucash

Then re-install if need be.

---

### Post by OldTimeTech on 2007-10-13
Thanks that worked.....had not seen that command before...not even in the help section.

Again thanks ;)

---

### Post by Pumalite on 2007-10-13
You are welcome. Good luck.

---

### Post by anacaona on 2008-04-10
Same package, same problem - and the solution worked for me, too! Thanks Pumalite!

---

