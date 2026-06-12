---
title: "Mystery of the Disappearing Programs."
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by AGadfly on 2008-03-16
I've tried searching the archives but don't really know what to look for and the automatic suggested threads don't cover my query..

I am finally able to connect to the net with Ubuntu (discovered the DHCP address was my router address only after many attempts at installation) and now I am finally ready to give it an honest try.  The problem I am having is with programs I install - no matter how I install them.  They all seem to disappear into a black hole somewhere inside my computer.

For example:  one legacy program that held me from switching was the Eudora mail handler which now has an open source and Linux version.  I searched, marked for install, and installed the program using Synaptic Package Manager.  However after install I cannot find the program on my HD and can not figure how to open it if I do. 

Am I missing a step or does the newly installed program not automatically add a "launcher" to the Applications menu.  If it does not then how do I

A- find out where my program went?

B- make my own launcher for the program.

C- add the launcher to the appropriate part of the App's menu.

D - as an adjunct I have installed Ubuntu on a 10.5Gb and would prefer to install programs to their own partitions - eg my "mail and communications" partition. How do I direct the package manager to install the program files in a specific directory on a specific partition?

I think that's enough for a start - so thank you in advance for any help you can give this nooby to get thai OS running in a more user friendly fashion.

Gad

---

### Post by jan quark on 2008-03-16
linux does not install applications like windows does

linux rather splits applications up into different parts and stores for instance all types A files here, and all types B files there

so I think you cannot have all the files of one applications in one folder

to check where all the files  of a specific applications were installed, open up synaptic, search for your application, right click on it, select properties and installed files

the executables are usually in usr/share or usr/bin

---

### Post by Ub1476 on 2008-03-16
To install applications on a separate partition, you need to separate /home and /. 

You can use the "whereis" command to find out where the application is installed.

```
whereis firefox
```

The application launcher is located under Applications>Any of the menus or System>Preferences/Administration.

To add a launcher for a program to the panel, right click on the panel, "Custom Application Launcher" or "Application Launcher".

To add a program to the Applications menu, right-click on the menu bar/main menu and select "edit menus", then "new item".

---

### Post by JKeefe on 2008-03-16
First of all, make sure that you hit 'Apply' in Synaptic to actually install the packages that you have marked for installation.  If a package is installed, the square next to the package name will be filled with greenish-blue.  An arrow means that the package has been merely marked for installation.  

Once a package is installed, right-click the package name and choose Properties.  The Installed Files tab will show you the locations of the installed program.  

Also, what is the name of the package that you are trying to install?  This will allow us to provide a more focused solution to your problem.

---

### Post by AGadfly on 2008-03-16
Thank you - you've all given me some paths to follow.  I'll get back after I've tried them.

Gad

---

### Post by AGadfly on 2008-04-23
I'm still stumbling around when I can get the time to sit down and learn by trying.

I have installed Glipper, and attempted to install the Debian menu as discussed **[ -HERE-]("http://www.monkeyblog.org/ubuntu/installing/#where_did_it_go")**
I have also attempted to install Virtualbox so that I can run some of my proprietary M$ programs under Ubuntu in a virtual way.

Still the programs disappear once I install them.  

I managed to add a "launcher" for Glipper but that's about as far as I got.

Is there any program, or menu system, or way, that I can install so that a new link/launcher to the new programs will be automatically added to the applications menu.  I find this the most frustrating part of using Ubuntu (or any of the distros of Linux I have tried).

Again thank you.

GAD

---

### Post by AGadfly on 2008-04-24
Eureka!!  (I think)

This page **_[- on ReallyLinux.com - ]("http://www.reallylinux.com/docs/windowstolinux.shtml")_** has the information I needed in order to find my programs and then install launchers to them.  

I highly recommend it for other newbies to Linux because it goes through the steps to not only accomplish the task but also to understand the basics required to do so in an orderly way.

Thank you for the help I got and I hope this thread will prove useful to others.

GAD

---

