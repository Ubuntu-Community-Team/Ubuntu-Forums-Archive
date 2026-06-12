---
title: "Making NDISWrapper"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by jamesbrooks101 on 2007-12-06
Hey,

I am trying Linux again. How do I make the makefile found with NDIS wrapper?

I have a dir located in "James" in the home dir. Where do I go from there?

Thanks,
James

---

### Post by OldTimeTech on 2007-12-06
I'm not sure why your going at it that way....if you go to applications->add/remove and type in the search ndiswrapper, it gives you the installer, all you have to do is put check mark in box, click on apply and it will install that and any other dependancies it needs.

---

### Post by jamesbrooks101 on 2007-12-06
Even with no internet installed?

---

### Post by OldTimeTech on 2007-12-06
would of been nice if you had noted that on first submission.

accordingly, add/remove is suppose to be all packages that are in ubuntu when loaded on your machine....not going to say that absolutely....

doing it on your terminal doesn't mean you won't need internet either.

type this into the terminal window and it will ask for your password
Code:

sudo apt-get install ndiswrapper-utils

if you did it write and if its is able to install you should get this output,

Reading package lists... Done
Building dependency tree... Done
Suggested packages:
ndiswrapper-source
The following NEW packages will be installed:
ndiswrapper-utils
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/25.7kB of archives.
After unpacking 131kB of additional disk space will be used.

Preconfiguring packages ...
Selecting previously deselected package ndiswrapper-utils.
(Reading database ... 57910 files and directories currently installed.)
Unpacking ndiswrapper-utils (from .../ndiswrapper-utils_1.1-4ubuntu2_i386.deb) ...
Setting up ndiswrapper-utils (1.1-4ubuntu2) ...

if you cant install ndiswrapper, you need to get to a comp that has internet and download it manually, follow this link,
[http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/)
then follow the installation directions from this page
[http://ndiswrapper.sourceforge.net/m....php/Main_Page](http://ndiswrapper.sourceforge.net/m....php/Main_Page)
this is the main ndiswrapper page as well,
[http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)

---

### Post by Dr.Suse on 2007-12-06
> **jamesbrooks101 said:**
> Even with no internet installed?

it would help us (and you) if you told us what hardware youre using (wlan card, computer type... etc.)

---

