---
title: "mac type curved dock"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by stonecoldjha on 2008-03-17
how can i get a curved dock for my ubuntu,plz  reply in detail.

---

### Post by thenewgirl on 2008-03-17
Check out this thread:

[http://ubuntuforums.org/showthread.php?t=572019&highlight=avant]("http://ubuntuforums.org/showthread.php?t=572019&highlight=avant")

---

### Post by stonecoldjha on 2008-03-17
i executed commands in the terminal.but i was stuck as i was asked to insert a live cd of gutsy gibbon.i have ubuntu fiesty fawn,and not its predecessor.what should i do?

---

### Post by Lord Illidan on 2008-03-17
Upgrade to Gutsy Gibbon, then.

---

### Post by Vadi on 2008-03-17
Yes, you should upgrade. Here's a link: [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by stonecoldjha on 2008-03-17
i had fiesty fawn right from the time i switched to ubuntu,so my problem is not that of upgradation,but the installation of a curved type dock,that i failed to do,because i was asked  by the terminal to insert a gutsy gibbon live cd.

---

### Post by Vadi on 2008-03-17
You need to upgrade your Ubuntu first, before installing the dock. That's why it was asking for a CD too - it wants to upgrade!

Upgrading is free too. Just start it, and it'll do everything by itself.

---

### Post by billgoldberg on 2008-03-17
Except it's recommended to do a clean install (from cd) instead of an upgrade. 

Upgrades can break things.

---

### Post by stonecoldjha on 2008-03-18
i went to the update manager and checked for the updates,it said that the OS was up to date.what should i do now?

---

### Post by forrestcupp on 2008-03-18
I don't think you can do what you are wanting to do unless you have Gutsy, the newer version.

If you want to upgrade to Gutsy, type this in a terminal:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

And upgrading is different than updating.  Upgrading is what you need to do.

---

### Post by stonecoldjha on 2008-03-18
i went to the terminal and did exactly as you said above.so here is the output:
[B][SIZE="2"]sonu@sonu-desktop:~$ sudo apt-get update
[sudo] password for sonu:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_IN
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_IN
Get:1 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy/main Translation-en_IN
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy/universe Translation-en_IN
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy/restricted Translation-en_IN
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy/multiverse Translation-en_IN
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy Release 
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy/main Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy/universe Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy/universe Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy/main Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy/restricted Sources
Fetched 1B in 5s (0B/s)                        
Reading package lists... Done
sonu@sonu-desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[/SIZE][/B]

then i tried to install the dock,but again it asked me to insert a live cd of gutsy as can be seen below:

[B][SIZE="2"]sonu@sonu-desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
sonu@sonu-desktop:~$ sudo apt-get install bzr m4 gnome-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  autoconf automake1.9 autotools-dev gettext intltool libc6-dev libtool linux-libc-dev patch
Suggested packages:
  autoconf2.13 autobook autoconf-archive gnu-standards autoconf-doc automake1.9-doc cvs gettext-doc glibc-doc manpages-dev
  libtool-doc g77 fortran77-compiler gcj diff-doc
Recommended packages:
  automaken python-paramiko python-pycurl libltdl3-dev
The following NEW packages will be installed:
  autoconf automake1.9 autotools-dev bzr gettext gnome-common intltool libc6-dev libtool linux-libc-dev m4 patch
0 upgraded, 12 newly installed, 0 to remove and 0 not upgraded.
Need to get 4451kB/9202kB of archives.
After unpacking 39.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)'
in the drive '/cdrom/' and press enter

[/SIZE][/B]
what do i do now?

---

### Post by forrestcupp on 2008-03-18
It looks like you already had Gutsy and didn't know it.

Go to System->Administration->Software Sources.  At the bottom of the Ubuntu Software tab, there is a box that says 'cd-rom.'  Uncheck it.  Then type
```
sudo apt-get update
```
And try what you were doing, and it shouldn't ask for a cd this time.

---

