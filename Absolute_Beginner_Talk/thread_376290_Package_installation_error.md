---
title: "Package installation error"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by gewitty on 2007-03-04
I've been trying to install Virtualbox on my system, but have been getting an error message every time, saying that I need to shut down another installer program that is running. There is no other application running, so this is a mystery. However, when I switched on this morning, the update manager popped up to tell me there were some new updates waiting to be installed. These also failed. When I hover the mouse over the update icon I get the following message:

An error occurred, please run Package Manager from the right click menu or apt-get on a terminal to see what is wrong. The error message was: 'Unknown Error: 'exceptions, SystemError' (E:The package Virtualbox needs to be reinstalled, but I can't find and archive for it.)'

When I right click and select, 'Start Package Manager', it opens, but give the following message:

'An Error Occurred: E:The package Virtualbox needs to be reinstalled, but I can't find and archive for it. E: Internal error opening cache (1). Please report.'

Can anyone tell me what's going on and how I fix it?

---

### Post by mozkaynak on 2007-03-04
> There is no other application running, so this is a mystery. 
I so have same problem. When I ask how to fix this I am always told check the processes and kill the one that causes the confusion. But in each case I failed to find such a process.

On virtual box issue, you might wanna deinstall/install it.
But before some other suggestions from pros.

---

### Post by Jussi01 on 2007-03-04
Hei,

try moving the virtualbox package to your home directory. 

then go to terminal, and type:

sudo dpkg -i nameofvirtualboxpakagehere.deb

let us know if this works

cheers


jussi

---

### Post by gewitty on 2007-03-05
Hi Jussi,

That appeared to work, but I'm not sure about some of the warnings that appeared before the installation (see below) which look as if they are to do with my previous attempts to load the package. I'm also not sure how to run the application as it hasn't appeared in any menus and I can't see it in the file system.

This is what happened in terminal:

dave@dave-desktop:~$ sudo dpkg -i VirtualBox_1.3.6_Ubuntu_edgy_i386.deb
(Reading database ... 
dpkg: serious warning: files list file for package `virtualbox' missing, assuming package has no files currently installed.
126105 files and directories currently installed.)
Preparing to replace virtualbox 1.3.6_Ubuntu_edgy (using VirtualBox_1.3.6_Ubuntu_edgy_i386.deb) ...
Unpacking replacement virtualbox ...
Setting up virtualbox (1.3.6_Ubuntu_edgy) ...

Creating group 'vboxusers'. VM users must be member of that group!

 * Starting VirtualBox kernel module vboxdrv                             [ ok ] 

dave@dave-desktop:~$

---

### Post by gewitty on 2007-03-05
Just figured out that I needed to add myself to the vbox user group before it would appear in the menu.  All seems to be working OK now.

Many thanks for the help.

---

