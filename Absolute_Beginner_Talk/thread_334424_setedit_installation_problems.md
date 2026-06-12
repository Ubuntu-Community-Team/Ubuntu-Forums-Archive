---
title: "setedit installation problems"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by xfred on 2007-01-08
In my long search for a dos-like (6.0) text editor, and after exhausting most of the options directly offered by ubuntu (nedit came close, but for some reason kept "losing" the keyboard (ie. no response until I moved the cursor with the mouse), and fte came very close, except using sudo to avoid a segfault was a pain), I thought I'd give setedit a try after seeing a number of recommendations on the forums.  But I just cannot get the darn thing to install.

Here's what I've done:

1) downloaded setedit_0.5.5-1_i386.ubu61.deb from sourceforge.
2) sudo dpkg -i setedit_0.5.5-1_i386.ubu61.deb

> Selecting previously deselected package setedit.
(Reading database ... 129723 files and directories currently installed.)
Unpacking setedit (from setedit_0.5.5-1_i386.ubu61.deb) ...
dpkg: dependency problems prevent configuration of setedit:
 setedit depends on libc6 (>= 2.4-1); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.
 setedit depends on libgcc1 (>= 1:4.1.1-12); however:
  Version of libgcc1 on system is 1:4.0.3-1ubuntu5.
 setedit depends on rhtvision2.1.0; however:
  Package rhtvision2.1.0 is not installed.
dpkg: error processing setedit (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 setedit

OK, so that requires libc6, and I have absolutely no idea how to update it.  Let's try an older version, so:

3) sudo apt-get install -f
4) get setedit_0.5.4-3_i386.deb
5) sudo dpkg -i setedit_0.5.4-3_i386.deb

> Selecting previously deselected package setedit.
(Reading database ... 129723 files and directories currently installed.)
Unpacking setedit (from setedit_0.5.4-3_i386.deb) ...
dpkg: dependency problems prevent configuration of setedit:
 setedit depends on aalib1 (>= 1.2); however:
  Package aalib1 is not installed.
 setedit depends on rhtvision2.0.3; however:
  Package rhtvision2.0.3 is not installed.
dpkg: error processing setedit (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 setedit

6) ok,  rhtvision2.0.3_2.0.3-3_i386 rings a bell - download  rhtvision2.0.3_2.0.3-3_i386.deb from the setedit sourceforge page and:
7) sudo dpkg -i rhtvision2.0.3_2.0.3-3_i386.deb

> Selecting previously deselected package rhtvision2.0.3.
(Reading database ... 129820 files and directories currently installed.)
Unpacking rhtvision2.0.3 (from rhtvision2.0.3_2.0.3-3_i386.deb) ...
dpkg: dependency problems prevent configuration of rhtvision2.0.3:
 rhtvision2.0.3 depends on xlibs (>> 4.1.0); however:
  Package xlibs is not installed.
dpkg: error processing rhtvision2.0.3 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 rhtvision2.0.3

8 ) search in vain for xlibs, no luck.

OK, that's what I'm up to.  I have absolutely no idea where to go from here (and to be honest I only half-understand most of the above).  Before I give up on the idea of installing setedit completely and go with one of the less-than-perfect alternatives, are there any suggestions as to what I need to do to get setedit installed?

---

### Post by shreevb on 2008-04-11
Note: When you attempt to install a package using dkpg, it can fail at times, but it will also let you know what is missing. The apt-get -f install seems to have enough awareness of the attempted install and can try to resolve anny package issues.
 
(I am a NEWBIE - and am learning as I go)
 
 
>  
cd /tmp
sudo mkdir setedit
cd setedit

>  
sudo wget [http://superb-west.dl.sourceforge.net/sourceforge/setedit/setedit_0.5.5-5etch_i386.deb](http://superb-west.dl.sourceforge.net/sourceforge/setedit/setedit_0.5.5-5etch_i386.deb)
sudo wget [http://superb-west.dl.sourceforge.net/sourceforge/tvision/rhtvision2.1.0_2.1.0-3etch_i386.deb](http://superb-west.dl.sourceforge.net/sourceforge/tvision/rhtvision2.1.0_2.1.0-3etch_i386.deb)


>  
sudo dpkg -i rhtvision2.1.0_2.1.0-3etch_i386.deb
sudo apt-get -f install

>  
sudo dpkg -i setedit_0.5.5-5etch_i386.deb
sudo apt-get -f install


 
To run setedit, type setedit
Not sure if you need to be in that directory or not to run setedit.
 
I did this on ubuntu server 7.1, with many failures but I believe that this set of commands shoud get you there.

---

