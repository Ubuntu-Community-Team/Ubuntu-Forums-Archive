---
title: "Installing Ndiswrapper 1.39"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by Shmook on 2007-03-27
My overall problem is Edgy not recognizing my wireless adapter, but one thing at a time. I've been going through the [ndiswrapper install wiki ]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation") as well as the install under Ubuntu page, but I'm still having trouble in the "make uninstall, make, make install" area.

Also, it seems different instruction pages have different make commands to use "make distclean instead of make uninstall?" 

I do alright extracting the files into a new ndiswrapper subfolder, it's the install that gives me errors. I'm hoping someone can go through the instructions simply for me, maybe even briefly describe what these *make* commands do?

Oh and I'm running Windows on the same machine now to write this, as, obviously I can't connect yet in Ubuntu -- thus can't copy the error messages easily. 

Oh, also, since I've already extracted it, but had errors installing it, is there a way to clean out the junk I've already installed before reinstalling?

---

### Post by Kobalt on 2007-03-27
Ok, one thing at a time. To install ndiswrapper you need to compile it. That means, download the sources (that you managed to do), then you need to compile the sources : that's what the *make* command does. 
You need some packages before starting the compilation though, so open up a Terminal and install build-essential and linux-headers-$(uname -r) with this command line : 
```
sudo aptitude install build-essential linux-headers-$(uname -r)
```
Then go into the ndiswrapper folder with the cd command line like this :
```
cd /path/to/ndiswrapper/folder
```
and finally compile it like this :
```
./configure
make
sudo make install
```
If it went smoothly, you successfully installed ndiswrapper.

---

