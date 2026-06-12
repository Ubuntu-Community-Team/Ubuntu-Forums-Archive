---
title: "Linux Program Compatibility"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by navymom on 2006-07-20
I've seen literally dozens of different Linux distributions and am wondering how it works with programs for Linux.  Will any program written for Linux work on a Linux distribution or does it have to be specifically written for a particular distribution?  Such as will something like The Gimp or Gimp Shop work on for any distribution of Linux I chose to install?

---

### Post by goobers on 2006-07-20
Mostly, yes, what you've got to look for is that you have the right binary for your computer, i.e most people on pcs would download an i386 binary unless they have a 64 bit processor , in which case they would get a 64 bit binary

---

### Post by nalmeth on 2006-07-20
Such is the nature of Open Source :)

---

### Post by slimdog360 on 2006-07-20
pretty much, though sometimes you may have to download new libraries to get the programs running.  This is evident in Ubuntu as it comes on one cd, thus it has to leave out certain things. For example Ubuntu comes with gnome by default so it doesn't have the KDE libs installed, you have to do that separately, so if you want to run a program made for KDE you first have to download the libs(which are free anyway, but can be a hassle for dial-up users). 
 But this is the way I and many others like it.

---

### Post by fatsheep on 2006-07-20
Check out this link:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Now here's my rant. :-D 

This is a loaded question.  For gimp files (.xcf) and OpenOffice writer (.odt), they work in both Linux and Windows.  However, there are tons of different ways programs can be installed.  Ubuntu is debian based so it makes use of .deb files (debian packages).  These are the files that the repositories make use of so to enable programs like Add/Remove and Synaptic package manager.  Another type of package file is an .RPM which is used by Suse, Fedora, and a lot of other distrobutions.  There are, however, ways of converting .RPM files to .deb files (see the link above).  There's also source, .bash, .sh, .run, and .bin.  You can even run a lot of .exe files if you have wine installed.

---

### Post by LinuxLemur on 2006-07-20
I think this is what they claim happened to Unix in the past.  They had so many companies making their own unix that a program made for unix would not work on another unix distrobution (or whatever it was).  I have read articles in the past that said this cannot happen to Linux.  Maybe because all distros stick with the same Linux Kernel (give or take a version) adn the community tries to keep some kind of standard.  I don't know. I can only understand and recall a certain amount of the rant.:confused:

---

