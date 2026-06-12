---
title: "DPKG is giving me troubles, probably a simple answer for a non-beginner! pls help."
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by ijason on 2007-09-17
hey all. i'm trying to remove a package that's giving me some trouble, i got some good advice on how to do so, but i'm not able to get it to work. here's what i've got :
> 
jason@jason-laptop:~$ sudo dpkg --force-remove-reinstreq --remove awcommon
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 164032 files and directories currently installed.)
Removing awcommon ...
/usr/bin/test: invalid integer `remove'
exit: 26: Illegal number: -0
dpkg: error processing awcommon (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 awcommon


---

### Post by alienexplorers on 2007-09-17
Try like it says to reinstall using:
> sudo aptitude reinstall packagename

---

### Post by ijason on 2007-09-17
i've tried that, and it didn't work.

> root@jason-laptop:/home/jason/Desktop/mayainstalls# ls
AWCommon-10.80-13.i686.rpm  maya_8.5-112_i386.deb
awcommon_10.80-14_i386.deb  Maya-docs_en_US-8.5-119.i686.rpm
Maya-8.5-111.i686.rpm       maya-docs-en-us_8.5-120_i386.deb

root@jason-laptop:/home/jason/Desktop/mayainstalls# sudo aptitude reinstall awcommon_10.80-14_i386.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "awcommon_10.80-14_i386.deb"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
E: I wasn't able to locate file for the awcommon package. This might mean you need to manually fix this package.
E: Couldn't lock list directory..are you root?
root@jason-laptop:/home/jason/Desktop/mayainstalls#

---

### Post by alienexplorers on 2007-09-17
Try
> sudo aptitude purge awcommon

---

### Post by ijason on 2007-09-17
ah, that did it! <3 for ya, alien!

did that actually delete the package, or just dump it from memory?

---

### Post by alienexplorers on 2007-09-17
That should have deleted the program and other packages associated with it.

---

### Post by ijason on 2007-09-17
damn.. it still says that awcommon needs to be reinstalled :( that pops up when i try to start the package manager.

---

### Post by ijason on 2007-09-17
ok... i tried reinstalling the package like the error message (and alien) said to do, but i get error messages doing that. here's what it outputs :

> root@jason-laptop:/home/jason/Desktop/mayainstalls# 
root@jason-laptop:/home/jason/Desktop/mayainstalls# ls aw*
awcommon_10.80-14_i386.deb
root@jason-laptop:/home/jason/Desktop/mayainstalls# 
root@jason-laptop:/home/jason/Desktop/mayainstalls# aptitude reinstall awcommon_10.80-14_i386.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "awcommon_10.80-14_i386.deb"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
E: I wasn't able to locate file for the awcommon package. This might mean you need to manually fix this package.
E: Couldn't lock list directory..are you root?
root@jason-laptop:/home/jason/Desktop/mayainstalls# 


---

### Post by alienexplorers on 2007-09-17
When you reinstall awcommon just type
> sudo aptitude reinstall awcommon

leave off the version number and .deb......

---

### Post by ijason on 2007-09-17
no, not saving sessions. i'll try the purge again and then reboot.

---

### Post by ijason on 2007-09-17
while i'm booting. here's the output from the purge command :

> root@jason-laptop:/home/jason/Desktop/mayainstalls# sudo aptitude purge awcommonReading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages will be automatically REMOVED:
  awcommon{p} 
The following packages will be REMOVED:
  awcommon{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 4100kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
dpkg: error processing awcommon (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 awcommon
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
root@jason-laptop:/home/jason/Desktop/mayainstalls# 

---

### Post by ijason on 2007-09-17
here's the output of the purge command :

> root@jason-laptop:/home/jason/Desktop/mayainstalls# sudo aptitude purge awcommonReading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages will be automatically REMOVED:
  awcommon{p} 
The following packages will be REMOVED:
  awcommon{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 4100kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
dpkg: error processing awcommon (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 awcommon
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
root@jason-laptop:/home/jason/Desktop/mayainstalls# 

---

### Post by ijason on 2007-09-18
the reinstall failed out in the same way with "awcommon" as it did when i specified the exact file name. i think it might have something to do with the error code i get when i try to run the purge command that you suggested. here's the output :

> jason@jason-laptop:~$ 
jason@jason-laptop:~$ sudo aptitude purge awcommon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages will be REMOVED:
  awcommon{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 4100kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
dpkg: error processing awcommon (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 awcommon
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
jason@jason-laptop:~$ 
jason@jason-laptop:~$

---

### Post by alienexplorers on 2007-09-18
Try one more thing and then I am out of ideas.
> sudo dpkg -i awcommon_10.80-14_i386.deb
then once that is done do a:
> sudo dpkg -r awcommon_10.80-14_i386.deb

---

### Post by ijason on 2007-09-18
>sigh< nice triple-post from me. jeeze.

---

### Post by ijason on 2007-09-18
ok, i appreciate all of your assistance. but i don't think that solved it yet :/... here's the output from your two commands :

> jason@jason-laptop:~/Desktop/mayainstalls$ sudo dpkg -i awcommon_10.80-14_i386.deb
Selecting previously deselected package awcommon.
(Reading database ... 164033 files and directories currently installed.)
Preparing to replace awcommon 10.80-14 (using awcommon_10.80-14_i386.deb) ...
Unpacking replacement awcommon ...
/usr/bin/test: invalid integer `upgrade'
exit: 26: Illegal number: -0
dpkg: warning - old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
/usr/bin/test: invalid integer `failed-upgrade'
exit: 26: Illegal number: -0
dpkg: error processing awcommon_10.80-14_i386.deb (--install):
 subprocess new post-removal script returned error exit status 2
/usr/bin/test: invalid integer `abort-upgrade'
exit: 26: Illegal number: -0
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 awcommon_10.80-14_i386.deb


jason@jason-laptop:~/Desktop/mayainstalls$ sudo dpkg -r awcommon_10.80-14_i386.deb
dpkg: you must specify packages by their own names, not by quoting the names of the files they come in

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
jason@jason-laptop:~/Desktop/mayainstalls$ 

---

### Post by alienexplorers on 2007-09-18
Try > sudo dpkg --remove --purge awcommon

---

### Post by ijason on 2007-09-18
hmm. might be on to something, except that running the --remove and --purge gets me an error for conflicting actions.

> jason@jason-laptop:~/Desktop/mayainstalls$ sudo dpkg --remove --purge awcommon
Password:
dpkg: conflicting actions -P (--purge) and -r (--remove)

---

### Post by alienexplorers on 2007-09-18
so just try;    >  sudo dpkg --purge awcommon

---

### Post by ijason on 2007-09-18
didn't we try the purge before? it always wants me to reinstall it, and then says it can't find a matching name when i try to reinstall o,O

> jason@jason-laptop:~/Desktop/mayainstalls$ sudo dpkg --purge awcommon
Password:
dpkg: error processing awcommon (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 awcommon
jason@jason-laptop:~/Desktop/mayainstalls$ 

---

### Post by alienexplorers on 2007-09-18
Well I'm stuck now.  Don't know what to try.  Sorry.....

---

### Post by splintercellguy on 2007-09-18
Ouch, at this point, a reinstall would be faster. If APT has screwed up that seriously, you should file a bug.

---

### Post by alienexplorers on 2007-09-18
I agree with Splintercellguy go for a new install.

---

