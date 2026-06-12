---
title: "Emacs Problem"
date: 2006-01-04
forum: Absolute Beginner Talk
---

### Post by mesocool on 2006-01-04
I just installed emacs from Synaptic but I cannot see any word from it. It all displays little rectangles instead. When I run it from terminal, I get the following error message. Can someone help me out? Thanks..

guanyu@home:~$ emacs
Warning: Cannot convert string "-*-courier-medium-r-*-*-*-120-*-*-*-*-iso8859-*" to type FontStruct
Warning: Cannot convert string "-*-helvetica-medium-r-*--*-120-*-*-*-*-iso8859-1" to type FontStruct

---

### Post by Kyral on 2006-01-04
Hmm...

What package did you select to install it? Try emacs21

---

### Post by darth_vector on 2006-01-04
the best fix to this problem is to switch to vi ;)

---

### Post by mesocool on 2006-01-04
[QUOTE=Kyral]Hmm...

What package did you select to install it? Try emacs21[/QUOTE]

I did install emacs21.. I just uploaded a pic of it... dont know why.. :confused:

---

### Post by viscount on 2006-01-04
Thats strange, I dont know if it will help at all, but you can try 

`apt-get remove --purge emacs21 emacs21-common emacs21-bin-common` 

and then 

`apt-get install emacs21` and see if it fixes anything.

Also, you can try to rename or remove your ~/.emacs file, this could somehow
be causing issues, although thats also a longshot.

Bug squishing is mostly just eliminating options until you either find the
problem, or go mad trying. :)

---

### Post by mesocool on 2006-01-04
[QUOTE=viscount]Thats strange, I dont know if it will help at all, but you can try 

`apt-get remove --purge emacs21 emacs21-common emacs21-bin-common` 

and then 

`apt-get install emacs21` and see if it fixes anything.

Also, you can try to rename or remove your ~/.emacs file, this could somehow
be causing issues, although thats also a longshot.

Bug squishing is mostly just eliminating options until you either find the
problem, or go mad trying. :)[/QUOTE]

Alright, I am trying it. But does it make any difference from installing from the Synaptic..

---

### Post by mesocool on 2006-01-04
Same as usual..  The problem is still there.. :confused: 


guanyu@home:~$ sudo apt-get remove --purge emacs21 emacs21-common emacs21-bin-common
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  emacs21* emacs21-bin-common* emacs21-common*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 43.4MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 94231 files and directories currently installed.)
Removing emacs21 ...
emacs-remove emacs21
emacsen-common: Handling removal of emacsen flavor emacs21
emacsen-common: purging byte-compiled files for emacs21
remove/dictionaries-common: Purging byte-compiled files for flavour emacs21
Purging configuration files for emacs21 ...
Removing emacs21-bin-common ...
Purging configuration files for emacs21-bin-common ...
Removing emacs21-common ...
guanyu@home:~$ sudo apt-get install emacs21 Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  emacs21-bin-common emacs21-common
Suggested packages:
  emacs21-el
The following NEW packages will be installed:
  emacs21 emacs21-bin-common emacs21-common
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/13.1MB of archives.
After unpacking 43.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
Selecting previously deselected package emacs21-common.
(Reading database ... 92985 files and directories currently installed.)
Unpacking emacs21-common (from .../emacs21-common_21.4a-1ubuntu1_all.deb) ...
Selecting previously deselected package emacs21-bin-common.
Unpacking emacs21-bin-common (from .../emacs21-bin-common_21.4a-1ubuntu1_i386.deb) ...
Selecting previously deselected package emacs21.
Unpacking emacs21 (from .../emacs21_21.4a-1ubuntu1_i386.deb) ...
Setting up emacs21-common (21.4a-1ubuntu1) ...

Setting up emacs21-bin-common (21.4a-1ubuntu1) ...

Setting up emacs21 (21.4a-1ubuntu1) ...
emacs-install emacs21
install/dictionaries-common: Byte-compiling for emacsen flavour emacs21
Wrote /usr/share/emacs21/site-lisp/dictionaries-common/debian-ispell.elc
Wrote /usr/share/emacs21/site-lisp/dictionaries-common/ispell.elc
Done
emacsen-common: Handling install of emacsen flavor emacs21
emacsen-common: byte-compiling for emacs21
Loading 00debian-vars (source)...
No /etc/mailname. Reverting to default...
Loading 50dictionaries-common (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...
Loading 50sml-mode (source)...
Package sml-mode removed but not purged.  Skipping setup.
Wrote /etc/emacs21/site-start.d/00debian-vars.elc
Wrote /usr/share/emacs21/site-lisp/debian-startup.elc
Done

---

### Post by mesocool on 2006-01-04
Got the soln @ [http://ubuntuforums.org/showthread.php?t=77591&highlight=emacs+fontStruct](http://ubuntuforums.org/showthread.php?t=77591&highlight=emacs+fontStruct)

---

