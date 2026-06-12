---
title: "Installation Software Failure... Xerces headers not found"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by BeingThere on 2006-10-09
I am trying to install a software and when I type "./configure" I obtained the error that it is detailed below.

I have installed in a machine the Ubuntu Dapper Drake Server. I have not any idea how to set up XERCESCROOT to point to the xerces libraries.

I am pretty sure that libxerces2 are installed in my computer but no idea how to set it up properly.

Thanks a lot to everybody.

[SIZE="1"]checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking for gccmakedep... no
checking for makedepend... makedepend
checking for Xerces 2.x headers in system includes... configure: error: Xerces 2.0 not found.  Ensure XERCESCROOT points to base directory of Xerces and Xerces 2.0 or later is available[/SIZE]

---

### Post by Perfect Storm on 2006-10-09
Make sure it's the -dev version you have installed.

---

### Post by BeingThere on 2006-10-09
Are you referring to the libxerces2-dev? I have not installed this package? Where can I get it?

Thanks for your reply...

---

### Post by Perfect Storm on 2006-10-09
I guess you don't have a gui/Desktop because you are running server so here it is. There's two version of v26 and v27

```
sudo aptitude install libxerces26-dev
```

for v27

```
sudo aptitude install libxerces27-dev
```

---

### Post by BeingThere on 2006-10-09
Thanks a lot! I am going to check it this afternoon.

I really glad with your wuick reply!

Cheers.

---

### Post by BeingThere on 2006-10-09
Thanks a lot! I am going to check it this afternoon.

I am really glad with your quick reply!

Cheers.

This is better! :-)

---

### Post by BeingThere on 2006-10-09
This is my error now, I try to update everything.
and no results.

sudo aptitude install libxerces26-dev Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "libxerces26-dev"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

---

### Post by Perfect Storm on 2006-10-09
Make sure that you have enable universe in your sourcelist first.

```
sudo nano /etc/apt/sources.list
```

Then uncomment the universe source.

---

### Post by BeingThere on 2006-10-09
Yes! Thank you, but now I am struggling again in...whats the name of the package I need?

checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

---

### Post by Perfect Storm on 2006-10-09
Hmmm....that means you need a Desktop envoriment, I dunno why it need that, what are you trying to compiling again?

---

### Post by BeingThere on 2006-10-09
I install lib-x11-dev and its sorted but now I obtained 

checking for Qt... configure: error: Qt (>= Qt 3.1 (20021021)) (headers and libraries) not found. Please check your installation!

I am trying to install a software called kjabata.

---

### Post by Perfect Storm on 2006-10-09
```
sudo aptitude install libqt3-headers libqt3-mt-dev
```

What do you need it for?

---

### Post by BeingThere on 2006-10-10
Thank you very much indeed AI. :-)

I worked out everything with your advices!

I am starting to love this system!

---

### Post by BeingThere on 2006-10-10
The software kjabata and wjabata is to manage the scheduling broadcasting of your radio station. Do you know any software that is more suitable for that, or more famous?

Cheers,

Being there...

---

### Post by Perfect Storm on 2006-10-10
No, sorry. I have no idea.

---

