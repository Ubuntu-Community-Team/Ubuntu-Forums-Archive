---
title: "mol (Mac-on-Linux) won't install"
date: 2008-11-24
forum: Apple Hardware Users
---

### Post by E-Rackattack on 2008-11-24
I'm using a 17" PowerBook G4 1.67 GHz running Mac OS X 10.3.9, openSUSE 11.0 (KDE 4.0), and Xubuntu 7.10 (Gutsy Gibbon)

I'm having a problem using aptitude/apt-get to install mol. It gives me this:

eric@PantherSUSE-XL:~$ sudo aptitude install mol mol-drivers-macosx
[sudo] password for eric:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  mol 
The following NEW packages will be installed:
  mol-drivers-macosx 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 311kB of archives. After unpacking 459kB will be used.
The following packages have unmet dependencies:
  mol: Conflicts: mol-drivers-macosx (< 0.9.72.1-1) but 0.9.71-1 is to be installed.
Resolving dependencies...
Unable to resolve dependencies!  Giving up...
Abort.
eric@PantherSUSE-XL:~$ 

Any help, please?

---

### Post by mfox on 2008-11-24
I don't believe that MOL will work on any Ubuntu distro newer than 7.04 anyway.  If the lack of MOL is a show-stopper, your choices are Ubuntu 7.04 or older, openSUSE 11 or Debian.  I can confirm that MOL works with openSUSE 11, Debian Etch and Debian Lenny on my PowerBook G4/1.33.  I tried Ubuntu 7.10 and 8.04 and was unable to get it to work.  As I understand it, a patch is required for newer kernels, and only openSUSE and Debian have implemented it thus far.  I really wanted it to run on my PowerBook and I removed Ubuntu 8.04 because it didn't.

---

