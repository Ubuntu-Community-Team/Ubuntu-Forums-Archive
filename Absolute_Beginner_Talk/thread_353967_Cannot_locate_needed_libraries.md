---
title: "Cannot locate needed libraries"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by chaplanger on 2007-02-05
I am seeking to install the Basilisk II emulator.  This will run the Mac Bible Application "Accordance."

I have been told that I need the following libraries.

devel/pkgconfig
required libraries: x11/XFree86-4-libraries, audio/esound,
devel/glib12,
x11-toolkits/gtk12 

I was also told that if I did a full install of Linux I would have these libraries.
Quote ----My suggestion, since you are a newbie to Linux is just to do a full
installation of Linux. That is what I usually do.-----End Quote

Here's the problem -- I am running Ubuntu 6.10 -- and it is flawless and can do everything I need or want (except for installing this program).  I do not want to reinstall Ubuntu 6.10 from scratch and begin again.

Where can I find these libraries without having to do a complete reinstall?

---

### Post by az on 2007-02-05
Just install it from the repositories instead of compiling it from source.

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=basilisk2](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=basilisk2)

You need to enable the multiverse repository:
[https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096](https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096)

To compile something from source, you need the developmental headers.  They are not included with the standard linux install.  They once were, like years ago.  I would say that documentation is pretty old.

---

### Post by chaplanger on 2007-02-05
> **az said:**
> Just install it from the repositories instead of compiling it from source.

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=basilisk2](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=basilisk2)

You need to enable the multiverse repository:
[https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096](https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096)

To compile something from source, you need the developmental headers.  They are not included with the standard linux install.  They once were, like years ago.  I would say that documentation is pretty old.

I've visited the first site and am unsure where to proceed form here. . .

The second site is set up for Dapper instructions (there is quite a difference with Edgy (6.10).   Details from the Dapper install don't fit with Edgy. . .  I'm still lost. . . if you have done this in Edgy, any additional details would be appreciated.

---

### Post by az on 2007-02-05
The Repositories page is for both Dapper and Edgy.

"This page describes how to manage software repositories in Ubuntu 6.10 (Edgy Eft) and Ubuntu 6.06 (Dapper Drake)."

You need to enable the universe and multiverse repositories and then update.  You will then be able to install the basilisk package from the repositories.

---

### Post by chaplanger on 2007-02-05
> **az said:**
> The Repositories page is for both Dapper and Edgy.

"This page describes how to manage software repositories in Ubuntu 6.10 (Edgy Eft) and Ubuntu 6.06 (Dapper Drake)."

You need to enable the universe and multiverse repositories and then update.  You will then be able to install the basilisk package from the repositories.

I understand the need to enable the universe and multiverse repositories -- but I don't know how to do this.  

My guess is that there must be a simple command line "apt get" to do this, but I do not know the proper syntax to accomplish it. . . and working within the GUI, I cannot configure it.

---

### Post by ComplexNumber on 2007-02-05
> I understand the need to enable the universe and multiverse repositoriesfire up synaptic. then go to 'settings', then 'repositories' in the menu. then reload.

---

### Post by chaplanger on 2007-02-05
When I go into synaptic I get the following screen (see the attached pic file).

Also: I looked into the "sources.list.d" and found these lines:
# automatically added by gnome-app-install on 2007-01-03 06:40:56.476946
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates multiverse

# automatically added by gnome-app-install on 2007-01-03 06:33:14.153647
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates universe

If I'm not mistaken -- these repositories are already enabled.  Still, the needed components as listed in the first post cannot be found.

---

### Post by punx45 on 2007-02-05
> My guess is that there must be a simple command line "apt get" to do this, but I do not know the proper syntax to accomplish it. . . and working within the GUI, I cannot configure it.
try
```
sudo apt-get install basilisk2
```

--------------------------------------------

i was able to find basilisk (its a 68k mac emulator right?)

```
geoff@toaster:~$ aptitude search basilisk
p   basilisk2                                 - 68k Macintosh emulator 
```
i then simulated an apt-get install and there weren't any complaints about missing libraries or dependencies,

```
geoff@toaster:~$ sudo apt-get install -s basilisk2
Password:
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  basilisk2
0 upgraded, 1 newly installed, 0 to remove and 18 not upgraded.
Inst basilisk2 (0.9.20050730-1 Ubuntu:6.06/dapper)
Conf basilisk2 (0.9.20050730-1 Ubuntu:6.06/dapper)

``` so ill attach my sources.list maybe there is a third party repository you need to add..

sources.list in a few..

and here it is:
```

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/plf dapper free non-free
deb-src http://packages.freecontrib.org/plf dapper free non-free                                               
                                                                                                                                          
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb http://archive.canonical.com/ubuntu dapper-commercial main

## AUTOMATIX SCRIPT
deb http://www.getautomatix.com/apt dapper main



```

---

### Post by chaplanger on 2007-02-05
> **punx45 said:**
> try
```
sudo apt-get install basilisk2
```

--------------------------------------------

i was able to find basilisk (its a 68k mac emulator right?)

```
geoff@toaster:~$ aptitude search basilisk
p   basilisk2                                 - 68k Macintosh emulator 
```
i then simulated an apt-get install and there weren't any complaints about missing libraries or dependencies,

```
geoff@toaster:~$ sudo apt-get install -s basilisk2
Password:
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  basilisk2
0 upgraded, 1 newly installed, 0 to remove and 18 not upgraded.
Inst basilisk2 (0.9.20050730-1 Ubuntu:6.06/dapper)
Conf basilisk2 (0.9.20050730-1 Ubuntu:6.06/dapper)

``` so ill attach my sources.list maybe there is a third party repository you need to add..

sources.list in a few..

and here it is:
```

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/plf dapper free non-free
deb-src http://packages.freecontrib.org/plf dapper free non-free                                               
                                                                                                                                          
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb http://archive.canonical.com/ubuntu dapper-commercial main

## AUTOMATIX SCRIPT
deb http://www.getautomatix.com/apt dapper main



```

I followed your steps and enabled the third party repositories in sources.list (even added PLF) -- but still, when I run
> sudo apt-get install basilisk2

the code runs but comes back with 
> david@david-desktop:~$ sudo apt-get install basilisk2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
basilisk2 is already the newest version.
The following packages were automatically installed and are no longer required:
  libsword6 mysql-common libmysqlclient15off python-qt3 python-sip4
  libtunepimp3 libifp4 libpq4 libclucene0 libid3-3.8.3c2a
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
david@david-desktop:~$ 

so it is still not installing. . .  I am baffled.

---

### Post by punx45 on 2007-02-05
the line that says "Basilisk2 is already the newest version" would indicate it is already installed.  that may or may not be from when you were attempting to install it manually. 

first i would see if it is in fact installed and you are able to use it.
'whereis basilisk2' should spit out a path and that would indicate it was installed.   also try 'man basilisk2' and if it came with a man page that will display.   i would then read it and see how you are supposed to use the program and try it out.

if none of that works..

you could try 
```
sudo apt-get remove basilisk2
```

and then apt-get install it again.

after that I am out of ideas :(

oh also, note that my sources.list is for dapper, while you are running edgy, so you should replace everywhere it says dapper with edgy (i think that is appropriate)

also also note that you should run ```
apt-get update
``` after you make changes to the sources.list

---

### Post by chaplanger on 2007-02-05
> **punx45 said:**
> the line that says "Basilisk2 is already the newest version" would indicate it is already installed.  that may or may not be from when you were attempting to install it manually. 

first i would see if it is in fact installed and you are able to use it.
'whereis basilisk2' should spit out a path and that would indicate it was installed.

Thanks for the tip!  I have found Basilisk2 -- now it's down to getting it set up properly.  I'll be in contact with the good folks at Accordance to try and get this set up now.  I'll post back here when that solution comes along.

Thanks for all of your assistance!

---

