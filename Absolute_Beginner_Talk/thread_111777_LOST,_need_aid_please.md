---
title: "LOST, need aid please"
date: 2006-01-02
forum: Absolute Beginner Talk
---

### Post by DeNorfolk on 2006-01-02
Hi all,

Although I have tried other Linux OS's before, what has attracted to Ubuntu is the forums and its active members participation. There is one major problem I have always ran into using a Linux OS and thats the ability to install programs. From my understanding, you down load a “package” that will be in a TGZ, RPM or DEB format. then use “ADD PROGRAMS” or “SYNAPTIC PACKAGE MANAGER” to install the program. I just don't seem to be getting this right. So can some one walk me through installing two programs?

My favorite web browser is OPERA and I have download this file onto my desktop  “opera_8.51-20051114.6-shared_qt_en_etch_i386.deb. The other program is an anti virus by Panda “pavcl_linux.i386.tgz”.

Any help would be appreciated.

Denorfolk

---

### Post by Iandefor on 2006-01-02
> 
Although I have tried other Linux OS's before, what has attracted to Ubuntu is the forums and its active members participation. There is one major problem I have always ran into using a Linux OS and thats the ability to install programs. From my understanding, you down load a &#8220;package&#8221; that will be in a TGZ, RPM or DEB format. then use &#8220;ADD PROGRAMS&#8221; or &#8220;SYNAPTIC PACKAGE MANAGER&#8221; to install the program. I just don't seem to be getting this right. So can some one walk me through installing two programs?

My favorite web browser is OPERA and I have download this file onto my desktop &#8220;opera_8.51-20051114.6-shared_qt_en_etch_i386.deb. The other program is an anti virus by Panda &#8220;pavcl_linux.i386.tgz&#8221;. You use a package manager to automate the downloading and installing of a package; it gets them from a repository on the internet, manages package dependencies, and installs the packages. To use Synaptic to manage your software, [check the wiki]("https://wiki.ubuntu.com/SynapticHowto"). 

However, you can install the packages you downloaded. To install a .deb file, open up a terminal and type in ```
sudo dpkg -i [name of .deb package]
``` which will then install the .deb package. To install a .tgz file, make sure you have build-essential installed- to get it, use the command ```
sudo apt-get install build-essential
``` Once it's installed, untar the file into it's own directory, then follow the instructions in any kind of documentation files you find (Usually called INSTALL or README).
I'll look around and see if I can find a page that explains it better than I, if all I did was confuse you.

---

### Post by dgbauer on 2006-01-02
After extracing a .tgz file, I almost always have to cd in to the directory in console and use the following three commands to install it:

```
./configure
```

```
make
```

```
sudo make install
```

That will install most .tgz files after they are exctracted for you...  Hope I didn't confuse you.  :D

---

### Post by jimrz on 2006-01-02
you can get/install Opera from Synaptic, but it looks like you will need to do Panda manually.

---

### Post by Madpilot on 2006-01-02
Opera on Ubuntu:
[https://wiki.ubuntu.com/OperaBrowser](https://wiki.ubuntu.com/OperaBrowser)

---

