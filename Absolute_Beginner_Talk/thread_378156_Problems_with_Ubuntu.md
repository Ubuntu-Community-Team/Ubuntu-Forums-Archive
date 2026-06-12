---
title: "Problems with Ubuntu"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by weightgain4000 on 2007-03-06
Hello,

Im having some more problems with Ubuntu

Problem 1
Whenever I click on the open office icon, I get the splash screen but office doesnt load

Problem 2
I would like to watch some DVD's on my computer, Ive tried using automatrix and also Easy Ubuntu to install the codecs and also using the wiki guide to no sucess 

john@john-desktop:~/easyubuntu$ sudo python easyubuntu.in
System sanity check: Failed!
Errors:
--------
/var/lib/dpkg/info/ia32-libs-kde.postinst: line 3: 13967 Bus error  ldconfig
dpkg: error processing ia32-libs-kde (--configure):
 subprocess post-installation script returned error exit status 135
/var/lib/dpkg/info/lib32asound2.postinst: line 6: 13969 Bus error ldconfig
dpkg: error processing lib32asound2 (--configure):
 subprocess post-installation script returned error exit status 135
dpkg: dependency problems prevent configuration of ia32-libs-sdl:
 ia32-libs-sdl depends on lib32asound2; however:
  Package lib32asound2 is not configured yet.
dpkg: error processing ia32-libs-sdl (--configure):
 dependency problems - leaving unconfigured
/var/lib/dpkg/info/lib32bz2-1.0.postinst: line 7: 13971 Bus error ldconfig
dpkg: error processing lib32bz2-1.0 (--configure):
 subprocess post-installation script returned error exit status 135
/var/lib/dpkg/info/lib32gfortran0.postinst: line 6: 13973 Bus error   ldconfig
dpkg: error processing lib32gfortran0 (--configure):
 subprocess post-installation script returned error exit status 135
/var/lib/dpkg/info/lib32ncurses5.postinst: line 6: 13975 Bus error  ldconfig
dpkg: error processing lib32ncurses5 (--configure):
 subprocess post-installation script returned error exit status 135
/var/lib/dpkg/info/lib32objc1.postinst: line 6: 13977 Bus error               ldconfig
dpkg: error processing lib32objc1 (--configure):
 subprocess post-installation script returned error exit status 135
/var/lib/dpkg/info/libgii0.postinst: line 22: 13979 Bus error               ldconfig
dpkg: error processing libgii0 (--configure):
 subprocess post-installation script returned error exit status 135
dpkg: dependency problems prevent configuration of libggi2:
 libggi2 depends on libgii0 (>= 1:0.9.1-0.1ubuntu1); however:
  Package libgii0 is not configured yet.
dpkg: error processing libggi2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mplayer:
 mplayer depends on libggi2 (>= 1:2.0.5); however:
  Package libggi2 is not configured yet.
dpkg: error processing mplayer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mozilla-mplayer:
 mozilla-mplayer depends on mplayer (>= 1.0-pre5) | mplayer-nogui (>= 1.0-pre5) | mplayer-powerpc (>= 1.0-pre5) | mplayer-g4 (>= 1.0-pre5); however:
  Package mplayer is not configured yet.
  Package mplayer-nogui is not installed.
  Package mplayer-powerpc is not installed.
  Package mplayer-g4 is not installed.
dpkg: error processing mozilla-mplayer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mplayer-fonts:
 mplayer-fonts depends on mplayer; however:
  Package mplayer is not configured yet.
dpkg: error processing mplayer-fonts (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mplayer-amd64:
 mplayer-amd64 depends on mplayer; however:
  Package mplayer is not configured yet.
dpkg: error processing mplayer-amd64 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ia32-libs-kde
 lib32asound2
 ia32-libs-sdl
 lib32bz2-1.0
 lib32gfortran0
 lib32ncurses5
 lib32objc1
 libgii0
 libggi2
 mplayer
 mozilla-mplayer
 mplayer-fonts
 mplayer-amd64
E: Sub-process /usr/bin/dpkg returned an error code (1)

EasyUbuntu is now trying to run 'dpkg --configure -a'
System sanity check: Failed!
Errors:
--------
/var/lib/dpkg/info/lib32asound2.postinst: line 6: 13985 Bus error ldconfig
dpkg: error processing lib32asound2 (--configure):
 subprocess post-installation script returned error exit status 135
/var/lib/dpkg/info/lib32bz2-1.0.postinst: line 7: 13987 Bus error ldconfig
dpkg: error processing lib32bz2-1.0 (--configure):
 subprocess post-installation script returned error exit status 135
/var/lib/dpkg/info/lib32ncurses5.postinst: line 6: 13989 Bus error  ldconfig
dpkg: error processing lib32ncurses5 (--configure):
 subprocess post-installation script returned error exit status 135
/var/lib/dpkg/info/ia32-libs-kde.postinst: line 3: 13991 Bus error  ldconfig
dpkg: error processing ia32-libs-kde (--configure):
 subprocess post-installation script returned error exit status 135
/var/lib/dpkg/info/lib32objc1.postinst: line 6: 13993 Bus error               ldconfig
dpkg: error processing lib32objc1 (--configure):
 subprocess post-installation script returned error exit status 135
/var/lib/dpkg/info/lib32gfortran0.postinst: line 6: 13995 Bus error   ldconfig
dpkg: error processing lib32gfortran0 (--configure):
 subprocess post-installation script returned error exit status 135
/var/lib/dpkg/info/libgii0.postinst: line 22: 13997 Bus error               ldconfig
dpkg: error processing libgii0 (--configure):
 subprocess post-installation script returned error exit status 135
dpkg: dependency problems prevent configuration of libggi2:
 libggi2 depends on libgii0 (>= 1:0.9.1-0.1ubuntu1); however:
  Package libgii0 is not configured yet.
dpkg: error processing libggi2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ia32-libs-sdl:
 ia32-libs-sdl depends on lib32asound2; however:
  Package lib32asound2 is not configured yet.
dpkg: error processing ia32-libs-sdl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mplayer:
 mplayer depends on libggi2 (>= 1:2.0.5); however:
  Package libggi2 is not configured yet.
dpkg: error processing mplayer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mplayer-fonts:
 mplayer-fonts depends on mplayer; however:
  Package mplayer is not configured yet.
dpkg: error processing mplayer-fonts (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mplayer-amd64:
 mplayer-amd64 depends on mplayer; however:
  Package mplayer is not configured yet.
dpkg: error processing mplayer-amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mozilla-mplayer:
 mozilla-mplayer depends on mplayer (>= 1.0-pre5) | mplayer-nogui (>= 1.0-pre5) | mplayer-powerpc (>= 1.0-pre5) | mplayer-g4 (>= 1.0-pre5); however:
  Package mplayer is not configured yet.
  Package mplayer-nogui is not installed.
  Package mplayer-powerpc is not installed.
  Package mplayer-g4 is not installed.
dpkg: error processing mozilla-mplayer (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 lib32asound2
 lib32bz2-1.0
 lib32ncurses5
 ia32-libs-kde
 lib32objc1
 lib32gfortran0
 libgii0
 libggi2
 ia32-libs-sdl
 mplayer
 mplayer-fonts
 mplayer-amd64
 mozilla-mplayer

EasyUbuntu will not run before these errors are fixed. Please fix them and try again
john@john-desktop:~/easyubuntu$

Problem 3
I would like to open a PDF attachment which was sent to me via my email, Ive tried installing abobe using the wiki guide but get the following error

john@john-desktop:~$ sudo apt-get install acroread mozilla-acroread acroread-pluginsacroread-debian-files
Reading package lists... Done
Building dependency tree... Done
Package acroread is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  acroread-debian-files
E: Package acroread has no installation candidate
john@john-desktop:~$

any help on these issues would be greatly apprecatied

Thanks

John

---

### Post by jem7v on 2007-03-06
For the .pdf file, you should already have Evince Document Viewer installed if you're running Ubuntu, and it opens acrobat files.  I've never had an issue with it, and I usually find it loads faster than Acrobat does.

I have no experience with DVD playback, though, and I'm not sure what's going on with OpenOffice, but here's something you might try: open a terminal and try to run it from there to see if it spits back an error message of some sort. The word processor would be this, for example:
```
ooffice -writer %U
```

---

### Post by seshomaru samma on 2007-03-06
Open a terminal and run:
```
sudo apt-get install libdvdcss2
```
If you get any errors - post them here

You should be able to view PDF files by clicking on them 

Try jem7v idea and post any errors

---

### Post by weightgain4000 on 2007-03-06
> **jem7v said:**
> For the .pdf file, you should already have Evince Document Viewer installed if you're running Ubuntu, and it opens acrobat files.  I've never had an issue with it, and I usually find it loads faster than Acrobat does.

I have no experience with DVD playback, though, and I'm not sure what's going on with OpenOffice, but here's something you might try: open a terminal and try to run it from there to see if it spits back an error message of some sort. The word processor would be this, for example:
```
ooffice -writer %U
```

ok done :p

john@john-desktop:~$ ooffice -writer %U
Inconsistency detected by ld.so: ../sysdeps/i386/dl-machine.h: 657: elf_machine_rel_relative: Assertion `((reloc->r_info) & 0xff) == 8' failed!

** (process:15066): WARNING **: Unknown error forking main binary / abnormal early exit ...
john@john-desktop:~$

---

### Post by weightgain4000 on 2007-03-06
> **seshomaru samma said:**
> Open a terminal and run:
```
sudo apt-get install libdvdcss2
```
If you get any errors - post them here

You should be able to view PDF files by clicking on them 

Try jem7v idea and post any errors

done

john@john-desktop:~$ sudo apt-get install libdvdcss2
Password:
Reading package lists... Done
Building dependency tree... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate
john@john-desktop:~$

---

### Post by maniacmusician on 2007-03-07
try:
> sudo dpkg --configure -a
that should configure any packages that aren't set up right. And,
> sudo apt-get -f install
should fix any broken packages. 

What does your /etc/apt/sources.list look like? 

For DVD codecs, I would use Automatix. It works every time for me. Or you can manually track down libdvdcss2 and install it.

---

### Post by weightgain4000 on 2007-03-07
> **maniacmusician said:**
> try:

that should configure any packages that aren't set up right. And,

should fix any broken packages. 

What does your /etc/apt/sources.list look like? 

For DVD codecs, I would use Automatix. It works every time for me. Or you can manually track down libdvdcss2 and install it.

ok here is my sources.list

# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) dapper main restricted 
deb [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) dapper universe multiverse 
deb [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Medibuntu multimedia packages
# GPG key: 0C5A2783
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) dapper free non-free

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

#AUTOMATIX REPOS START

deb [http://ubuntu.moshen.de](http://ubuntu.moshen.de) dapper misc

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
#AUTOMATIX REPOS END

I tried this command sudo dpkg --configure -a

and got the following :P
john@john-desktop:~$ sudo dpkg --configure -a
Setting up lib32asound2 (1.0.10-2ubuntu4) ...
/var/lib/dpkg/info/lib32asound2.postinst: line 6: 16942 Bus error ldconfig
dpkg: error processing lib32asound2 (--configure):
 subprocess post-installation script returned error exit status 135
Setting up lib32bz2-1.0 (1.0.3-0ubuntu2) ...
/var/lib/dpkg/info/lib32bz2-1.0.postinst: line 7: 16944 Bus error ldconfig
dpkg: error processing lib32bz2-1.0 (--configure):
 subprocess post-installation script returned error exit status 135
Setting up lib32ncurses5 (5.5-1ubuntu3) ...
/var/lib/dpkg/info/lib32ncurses5.postinst: line 6: 16946 Bus error  ldconfig
dpkg: error processing lib32ncurses5 (--configure):
 subprocess post-installation script returned error exit status 135
Setting up ia32-libs-kde (7.2) ...
/var/lib/dpkg/info/ia32-libs-kde.postinst: line 3: 16948 Bus error  ldconfig
dpkg: error processing ia32-libs-kde (--configure):
 subprocess post-installation script returned error exit status 135
Setting up lib32objc1 (4.0.3-1ubuntu5) ...
/var/lib/dpkg/info/lib32objc1.postinst: line 6: 16950 Bus error               ldconfig
dpkg: error processing lib32objc1 (--configure):
 subprocess post-installation script returned error exit status 135
Setting up lib32gfortran0 (4.0.3-1ubuntu5) ...
/var/lib/dpkg/info/lib32gfortran0.postinst: line 6: 16952 Bus error   ldconfig
dpkg: error processing lib32gfortran0 (--configure):
 subprocess post-installation script returned error exit status 135
Setting up libgii0 (0.9.1-0.1ubuntu1) ...
/var/lib/dpkg/info/libgii0.postinst: line 22: 16954 Bus error               ldconfig
dpkg: error processing libgii0 (--configure):
 subprocess post-installation script returned error exit status 135
dpkg: dependency problems prevent configuration of libggi2:
 libggi2 depends on libgii0 (>= 1:0.9.1-0.1ubuntu1); however:
  Package libgii0 is not configured yet.
dpkg: error processing libggi2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ia32-libs-sdl:
 ia32-libs-sdl depends on lib32asound2; however:
  Package lib32asound2 is not configured yet.
dpkg: error processing ia32-libs-sdl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mplayer:
 mplayer depends on libggi2 (>= 1:2.0.5); however:
  Package libggi2 is not configured yet.
dpkg: error processing mplayer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mplayer-fonts:
 mplayer-fonts depends on mplayer; however:
  Package mplayer is not configured yet.
dpkg: error processing mplayer-fonts (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mplayer-amd64:
 mplayer-amd64 depends on mplayer; however:
  Package mplayer is not configured yet.
dpkg: error processing mplayer-amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mozilla-mplayer:
 mozilla-mplayer depends on mplayer (>= 1.0-pre5) | mplayer-nogui (>= 1.0-pre5) | mplayer-powerpc (>= 1.0-pre5) | mplayer-g4 (>= 1.0-pre5); however:
  Package mplayer is not configured yet.
  Package mplayer-nogui is not installed.
  Package mplayer-powerpc is not installed.
  Package mplayer-g4 is not installed.
dpkg: error processing mozilla-mplayer (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 lib32asound2
 lib32bz2-1.0
 lib32ncurses5
 ia32-libs-kde
 lib32objc1
 lib32gfortran0
 libgii0
 libggi2
 ia32-libs-sdl
 mplayer
 mplayer-fonts
 mplayer-amd64
 mozilla-mplayer
john@john-desktop:~$

---

### Post by maniacmusician on 2007-03-07
oO what the hell did you do to your system? I've never had an error like that. Did you try "sudo apt-get -f install"?

The only strange repos I see in your sources.list are the medibuntu repo and the [http://ubuntu.moshen.de](http://ubuntu.moshen.de) repo under Automatix.

---

### Post by seshomaru samma on 2007-03-07
It looks like your system is seriously messed up , at least aptitude is...

According to[ this thread]("http://ubuntuforums.org/showthread.php?t=358354") running fsck would solve it  (put 'man fsck' in the terminal for more info - it's basically a utility that repairs your file system)

However I would try to fix aptitude first , read the second post in the thread for how to do that.

---

### Post by slayerboy on 2007-03-07
did you have a power outage at all or shutdown your computer in a weird way?

How old is your computer/hard drive?  Could be a failing HD.

---

### Post by weightgain4000 on 2007-03-07
> **slayerboy said:**
> did you have a power outage at all or shutdown your computer in a weird way?

How old is your computer/hard drive?  Could be a failing HD.

Had lots of seprate issues over the last few days, :lolflag:  either from following directions in [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper) and some part not working 100% :P or through my own lack of knowledge with linux and stuffing something up :confused: 

Ive decided to do another re-install hopefully I wont get too many problems this time round! :P

---

