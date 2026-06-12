---
title: "Downdloading and Install"
date: 2005-07-03
forum: Absolute Beginner Talk
---

### Post by AsburyPark on 2005-07-03
I have a problem installing programs.  I'm sure its operator error.  When downloading open with (????) or save to disk (desktop)???

One downloaded how to install?

example, firefox1.0,4, thunderbird, drivers, etc....

I dont know what I'm doing, and I'm proud to say it.

---

### Post by Kyral on 2005-07-03
Here is the best part of Ubuntu.

The power of ***APT*** (Yes, I love Apt so much to Bold AND Italicize it!)

Either fire up Synaptic and point and click your way to the software, or (my preferred method) command line.

First make sure your /etc/apt/sources.list is updated.

I'll post up mine so you can just paste it in there

```
deb http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted universe multiverse

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

#deb ftp://ftp.nerim.net/debian-marillat/ stable main
#deb ftp://ftp.nerim.net/debian-marillat/ unstable main
#deb ftp://ftp.nerim.net/debian-marillat/ testing main

#Primary Mirror (5/17/2005) overloaded :)
#deb http://backports.ubuntuforums.org/backports hoary-backports main universe multiverse restricted
#deb http://backports.ubuntuforums.org/backports hoary-extras main universe multiverse restricted

#backup Mirror - FAST
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

#Backport TESTING Mirror - Experimental
deb http://ubuntu-backports.mirrormax.net/ hoary-extras-staging main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-backports-staging main universe multiverse restricted

```

NOTE TO ALL THE EXPERIANCED USERS: Nerim is commented out, and I have never b roken anything using Backports/Backports-staging

Anyway, just replace your sources.list with this one, then open a terminal and type
```
 sudo apt-get update 
```

Afterwards just use the apt-cache command to search, like this
```
apt-cache search <software>
```

After that, installing it is just as easy as issuing this command
```
sudo apt-get install <package>
```

And to upgrade all packages in your system
```
sudo apt-get dist-upgrade
```

Have fun! And welcome to the Wonderful World of Linux*insert copyleft symbol here*

---

### Post by codejunkie on 2005-07-03
well thats the one thing about linux how to install software there is so many different ways because not every file you download is the same type for instance firefox that you mentioned there is really no need to download it from [www.mozilla.org](www.mozilla.org) because you can install it very easy by using synaptic and installing it there but to get the latest version of it you have to add these repos to your /etc/apt/sources.list file 
```

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

```
you can find instructions on this and many other things at [www.ubuntuguide.org](www.ubuntuguide.org)
by using synaptic this eliminates alot of things like missing dependencies with packages and by using synaptic it automaticly updates all your software so you always have the latest stable version. so if you find a package on the web that you want open synaptic click search and search for that package if it's in there install it. if it's not in synaptic it really depends on the package you downloaded if you downloaded a .deb file you install it by opening a terminal and typing
```

sudo dpkg -i nameofpackage.deb

```
if you download an auto package [http://autopackage.org/](http://autopackage.org/)
you just double click on it and install it.

if you downloaded something like say firefox from [www.mozilla.org](www.mozilla.org) it comes with an automatic install script first you have to extract it from the compressed file example: 
```

.tar   
.bz2 
.tar.gz 
.gz 
.zip

```
by right clicking on it and choose extract, or opening an archive manager like fileroller Applications/Accessories/Archive Manager and extracting it for example firefox you doubleclick on the firefox-installer.sh and choose run and it runs the gui
installer answer some questions and your done.
but some of these automatic install scripts don't have a gui they are all text based 
so with these you open these in the terminal by changing to the directory where they are located and running ```
sh name-of-file.sh
``` when you press enter it will open a text based installer you just follow the steps and your done.

if you download the sorce file you have to compile it and install.

but basicly its all up to you how you install software if one way seems to complicated use an autopackage or a .deb package it's by far the safest easiest way since  ubuntu in a debian based distro hope this helps.

---

### Post by Kvark on 2005-07-03
*reads two previous posts*

Geez, all that just to install something. Newcommers will run away if you guys keep telling them to use the command line.



Just do this...
Open the synaptic package manager...
Look in the sections or use the search function to find the programs you want...
Put checkboxes for the programs you want...
Click apply...
Start using the programs.

Can't be easier then that.

You will need to edit your sources.list file first to add the backports though, but thats just a one time thing.

---

### Post by AsburyPark on 2005-07-03
[QUOTE=Kvark]*reads two previous posts*

Geez, all that just to install something. Newcommers will run away if you guys keep telling them to use the command line.

You will need to edit your sources.list file first to add the backports though, but thats just a one time thing.[/QUOTE]

I'm not running yet....

Another how to question:

How to edit sources.list file to add backports?

I figured out how to use synaptic, but it doesn't have what I'm looking for (ipw2200 + fw 2.3) 

I am having trouble executing some apt-get commands.

---

### Post by Kyral on 2005-07-03
sudo gedit /etc/apt/sources.list

Then just replace what is in there with what I pasted in :D

---

### Post by poofyhairguy on 2005-07-04
[QUOTE=Kyral]sudo gedit /etc/apt/sources.list

Then just replace what is in there with what I pasted in :D[/QUOTE]


then do this command:

> sudo apt-get update

---

### Post by AsburyPark on 2005-07-04
[QUOTE=Kyral]sudo gedit /etc/apt/sources.list[/QUOTE]

I get this....

```
root@liger:/home/steve # sudo gedit /ect/apt/sources.list

(gedit:7783): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
```

---

### Post by poofyhairguy on 2005-07-04
[QUOTE=AsburyPark]I get this....

```
root@liger:/home/steve # sudo gedit /ect/apt/sources.list

(gedit:7783): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
```[/QUOTE]


dont do it in root terminal. regular terminal.

in the root terminal....don't use sudo. Sudo gives you the power of root in the regular terminal.

---

### Post by AsburyPark on 2005-07-04
> dont do it in root terminal. regular terminal.

in the root terminal....don't use sudo. Sudo gives you the power of root in the regular terminal.

That is an answer I have been looking for all day!  Thankyou!

Thanks to all...

 \\:D/

---

### Post by AsburyPark on 2005-07-04
[QUOTE=AsburyPark]That is an answer I have been looking for all day!  Thankyou!

Thanks to all...

 \\:D/[/QUOTE]
 That cleared up most of my problems

Now, when I download from a mirror, should I save to disk?

I am confused at how to "UNTAR" a package, my terminal will show that the package is not found..

What am I missing?

---

### Post by aysiu on 2005-07-04
[QUOTE=AsburyPark]
I am confused at how to "UNTAR" a package, my terminal will show that the package is not found.. [/QUOTE] If you insist on doing it from the command line, it's something like *tar xvcf filename.tar.gz*. I believe if you just double-click on the .tar.gz file, though, it should extract the files.

---

### Post by ozzie123 on 2005-07-04
[QUOTE=aysiu]If you insist on doing it from the command line, it's something like *tar xvcf filename.tar.gz*. I believe if you just double-click on the .tar.gz file, though, it should extract the files.[/QUOTE]
 Just to make some note... Firefox version on Ubuntu's Synaptic is 1.0.2 while the newest version of Firefox (in Mozilla's site) is 1.0.4. Is there any good explanation why they haven't updated it?

---

### Post by Kyral on 2005-07-04
Backports IS the latest version, you just have to tweak the version number in about:config for MozUpdate to see it

---

### Post by Vorian on 2005-07-04
I figured out the Firefox upgrade thanks again...

Is there a backport for fw 2.3, or the IPW2200 driver?  I am trying to follow the insructions on [ipw2200 + ipw](http://www.ubuntuforums.org/showthread.php?t=26623)

---

### Post by AsburyPark on 2005-07-04
I figured out the firefox upgrade, thaks for your help with that....

Is there a backport for programs like fw 2.3 or the ipw 2200 driver?  I am trying to follow the instructions on ipw2200 + ipw tips and trick.  I have been downloading them, and I haven't been able to untar them.  My terminal will show " package not found"

---

### Post by poofyhairguy on 2005-07-04
[QUOTE=ozzie123]Just to make some note... Firefox version on Ubuntu's Synaptic is 1.0.2 while the newest version of Firefox (in Mozilla's site) is 1.0.4. Is there any good explanation why they haven't updated it?[/QUOTE]


Because officially Ubuntu doesn't update its packages because the new packages might bring about new problems.

Thats why the backports project (currently unofficial) was created.

---

