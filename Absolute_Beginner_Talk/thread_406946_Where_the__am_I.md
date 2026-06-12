---
title: "Where the ? am I"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by liverwurst on 2007-04-11
Excuse the French...but yesterday I was looking for a good reason, actually any reason to get off Windows and I took the leap.  

On a brand new AMD64(opteron) system, I installed Ubuntu (6.10 i386)...nice and easy....

  Now I'm going thru the pain of getting a linksys pci or usb to work...... NOT too nice and easy..

I read about installing ndisgtk  but any/all of the packages that were downloaded give problems.   

ndisgtk_0.3-1_all.deb: Error:  Dependancy is not satisfiable:  ndiswrapper-utils

ndisgtk_0.5-1ubuntu1_all.deb :   Error:  Dependancy is not satisfiable:  ndiswrapper-utils

ndisgtk_ndiswrapper_GUI_0_3.mo  Error;  no program available for installation...

ndiswrapper-utils_1.1-4ubuntu2_amd64.deb   Error : Wrong Architecture AMD64

That last one is a real confuser...

I just tried to unwind and compile  ndiswrapper-1.41.tar, following the instructions provided and it bombs because it can't find the correct header files and a bunch of other problems...

So, what now?   There are so many flavors of everything, and nothing to define what they are or what goes with it.   Is there a version of Linux that will size and install a wireless card, without all the headbanging, or is it back to Win98?

thanks

---

### Post by igknighted on 2007-04-11
The AMD64 packages are only for a 64bit OS.  Since you installed i386 Ubuntu, then you need to have the i386 package.

To get around the circular dependencies, install them all with one command:
```
sudo dpkg -i package1.deb package2.deb ... packageLast.deb
```

There are certainly easier distros, especially for wireless.  Try SAM Linux, it recognized my wireless that Ubuntu did not.  Also Mepis or Linux Mint would be good choices.

---

### Post by annda on 2007-04-11
if you can avoid it, DO NOT download packages. install through synaptic (system > administration > synaptic) or apt-get in the terminal. that way all the dependencies will be downloaded and installed automatically.

you might need to enable all repositories with with packages in order to maximize the pool of available packages. in synaptic go to settings > repositories and check all the boxes with universe, multiverse etc.

---

