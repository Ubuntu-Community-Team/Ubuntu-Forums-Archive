---
title: "Disable Ubuntu CD source"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by moondoggy17 on 2008-01-06
trying to install awn dock with this guide [http://www.uluga.ubuntuforums.org/showthread.php?t=572019&highlight=awn+curves]("http://www.uluga.ubuntuforums.org/showthread.php?t=572019&highlight=awn+curves")

don't have the ubuntu install disk is there away to get around this without the disk
```
drew@dieyoufool:~$ sudo apt-get install bzr m4 gnome-common
[sudo] password for drew:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  autoconf automake1.9 autotools-dev gettext intltool libc6 libc6-dev
  libc6-i686 libtool linux-libc-dev patch
Suggested packages:
  autoconf2.13 autobook autoconf-archive gnu-standards autoconf-doc
  automake1.9-doc cvs gettext-doc glibc-doc manpages-dev libtool-doc g77
  fortran77-compiler gcj diff-doc
Recommended packages:
  automaken python-paramiko python-pycurl libltdl3-dev
The following NEW packages will be installed:
  autoconf automake1.9 autotools-dev bzr gettext gnome-common intltool
  libc6-dev libtool linux-libc-dev m4 patch
The following packages will be upgraded:
  libc6 libc6-i686
2 upgraded, 12 newly installed, 0 to remove and 143 not upgraded.
Need to get 10.7MB/14.5MB of archives.
After unpacking 39.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)'
in the drive '/cdrom/' and press enter

```

---

### Post by Perfect Storm on 2008-01-06
Go to System tab ---> Administration ---> System Sources.

Here you can disable the Ubuntu CD.

/me changed Title thread to something more useful.

---

### Post by taurus on 2008-01-06
Go into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and uncheck the CDROM option at the bottom window.  Make sure there is a check mark for everything else in there except the last one, Source code.  Close it and press Refresh.  It will not ask for the installer CDROM again.

---

### Post by lolzlolz on 2008-01-06
no im afraid there might be an easier way more in tune with artificials
System-->Administration-->Software Sources
once on this menu you may modify all your software sources, what you are looking for would be at the bottom of the ubuntu software tab 
uncheck the cdrom with ubuntu 7.10 'Gutsy Gibbon' option
i also reccomend checking the others in the ubuntu software tab, unchecking the cd, and going to the third party software tab and checking both of these

---

