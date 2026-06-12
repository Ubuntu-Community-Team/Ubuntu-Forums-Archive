---
title: "How to install Skype"
date: 2005-11-11
forum: Absolute Beginner Talk
---

### Post by discofro on 2005-11-11
Can someone please explain to me how to install the .deb version of skype? I just downloaded it and it simply will not respond to anything... 




This is what I've tried in the terminal:

robert@digitaloutcast:~/Desktop$ sudo dpkg -i skype.deb
Password:
Selecting previously deselected package skype.
(Reading database ... 69479 files and directories currently installed.)
Unpacking skype (from skype.deb) ...
dpkg: dependency problems prevent configuration of skype:
 skype depends on libqt3c102-mt (>= 3:3.3.3.2); however:
  Package libqt3c102-mt is not installed.
 skype depends on libstdc++5 (>= 1:3.3.4-1); however:
  Package libstdc++5 is not installed.
dpkg: error processing skype (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 skype
robert@digitaloutcast:~/Desktop$ sudo apt-get install libqt3c102-mt
Reading package lists... Done
Building dependency tree... Done
Package libqt3c102-mt is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libqt3-mt
E: Package libqt3c102-mt has no installation candidate
robert@digitaloutcast:~/Desktop$ sudo apt-get install libqt3-mt
Reading package lists... Done
Building dependency tree... Done
libqt3-mt is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  skype: Depends: libqt3c102-mt (>= 3:3.3.3.2) but it is not installable
         Depends: libstdc++5 (>= 1:3.3.4-1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
robert@digitaloutcast:~/Desktop$ sudo apt-get -f install libqt3-mt
Reading package lists... Done
Building dependency tree... Done
libqt3-mt is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  skype: Depends: libqt3c102-mt (>= 3:3.3.3.2) but it is not installable
         Depends: libstdc++5 (>= 1:3.3.4-1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
robert@digitaloutcast:~/Desktop$



As you can see I tried to install the dependancies it claimed to need but that also failed. I really don't know how to do this. Any ideas?

---

### Post by 23meg on 2005-11-11
[https://wiki.ubuntu.com/SkypeHowto](https://wiki.ubuntu.com/SkypeHowto)

I have installed the unofficial deb suggested here that has been tweaked to set the dependency correctly; no problems so far.

---

### Post by jan de beuker on 2005-11-11
Hello
    Read your problem
    On this forum a install called automatix.
    One of tha programs wher you can use it for is skype
    
    greetings jan

---

### Post by steevc on 2005-11-11
I just managed to mess up my system trying to re-install Skype. It had popped up a box saying I needed to re-install it, so I removed it with Adept and downloaded the latest Deb. Installing that complained about the dependency mentioned in the wiki, so I tried to install that. Then I got complaints about some package being broken so ran

sudo apt-get -f install

Then I ran

sudo apt-get install libqt3c102-mt

and it proceeded to uninstall all my KDE packages. Why would it do that? I've since re-installed Kubuntu, but I'm a bit wary of Skype now. Does anyone know if they are going to produce a package that works on Ubuntu?

---

### Post by Cuppa-Chino on 2005-11-11
check this thread:

[http://ubuntuforums.org/showthread.php?t=81831&highlight=skype]("http://ubuntuforums.org/showthread.php?t=81831&highlight=skype")

or just *alien* the rpm, for this use the synaptic package manager, download the fedora core (FC) rpm package from skype and:

**alien skype-xyz.rpm**
and install the resultant deb with dpkg

---

### Post by 23meg on 2005-11-11
Steevc: libqt3c102-mt was replaced by another package and the Skype deb has an incorrect dependency that points to it. This was fixed in the alternative unofficial deb linked on the wiki page I mentioned in my previous post.

---

### Post by patrick295767 on 2005-11-11
Download the version : Static binary tar.bz2 with Qt 3.2 compiled in (10.4 MB)
   
unpack it 
  
then install it 
u can start the program from the folder that will be created (where u unpack the file) 
  
Enjoy !!
  
Pat'

---

### Post by patrick295767 on 2005-11-11
[http://www.skype.com/products/skype/linux/](http://www.skype.com/products/skype/linux/)

---

### Post by steevc on 2005-11-12
Thanks for the info Patrick. I now have it working again.

As I prefer to just use one IM app for communicating with family I recommend Skype as it's easy to install on their Windows and we can do voice chat.

---

