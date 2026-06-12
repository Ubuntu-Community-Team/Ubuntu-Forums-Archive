---
title: "sound  card drivers"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by johnapeterson on 2007-07-30
Hello all,

I am brand new to ubuntu, and am very excited about using it.

I need to set up my M-Audio Delta 44 card, and could use some help setting it up.  I was a computer science major way back in the early 80s, but after my sophmore year, I switched degree to Appalachia nStudies (a hillbilly degree).

Anyway, I downloaded the DEB package from opensound.com, and got a liscense file for th Delta 44.  Unfortunately, I am told that I need a 2.6 kernel with kernel sources, GCC Complier, Binutils, GNU Make, GTK/Glib 2.0 libraries in order to intall oss.  Do these items come with ubuntu, or do I need to download them from else where.  If they do not come with ubuntu, whee can I download them, and is there a specific file that they need to be put in on the computer?

PS I am using the current version of ubuntu 7.04

Thanks for your help,
John

---

### Post by ravenwere on 2007-07-30
Hi John and welcome,

Best place to start I found is the following link
[http://ubuntuguide.org/wiki/Ubuntu:Feisty]("http://ubuntuguide.org/wiki/Ubuntu:Feisty")

The explains many things for us noobs.

All the best,
r

---

### Post by ravenwere on 2007-07-30
Hi again John,

With regard to compiling drivers I would be better qualified as one of the subjects of your Appalachian studies.

In most cases the default drivers that install with Ubuntu are sufficient for the majority of hardware.

The packages you mentioned can be updated and installed using the package managers that are installed by default with kde or gnome (Adept or Synaptic respectively).

Alternatively using apt at the command line:
```
sudo apt-get install <package name>
```

I will leave it to others to comment on compiling.

r

---

### Post by Chilongola on 2007-07-30
[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/)

[http://www.nitehawk.com/linrad_dat/](http://www.nitehawk.com/linrad_dat/)

These may help you.

---

### Post by johnapeterson on 2007-07-31
Ok,
I think that I am beginning to get somewhere.

Visit the opensound forums I figured I can install GCC, Binutils, GNU make by using the following code in "terminal"

sudo apt-get install gcc
sudo apt-get install make
sudo apt-get install binutils

but  I dont know about gtk/glib 2.0.  what would I need to typeto install that?

The next step in opensource said to type
sudo apt-get install linux-headers-'uname -r'
Wehn I do it says it cannot find file

And then it say to type 
sudo apt-get install build-essential
but the again it say it cannot find file (or something to that extent.  The ubuntu computer is not hooked up to the net yet, so i am using my wife computer in a different part of the house.

Am I typing the code in wrong or am I not typing the right code in.  

Thanks for your help.

John

---

### Post by ravenwere on 2007-07-31
Hi John,

Personal opinion: I wouldn't tend to install much without getting the internet connection and updating the software already installed from the CD. For instance you may compile a sound driver for your current kernel version but as there is an updated kernel available you would have to recompile as soon as you updated.

To address some specific questions:

(1) If you type uname -r on the command line you get the kernel version you installed hence:
```
uname -r
```
on my PC returns:

2.6.20-16-generic

This is what they mean with the headers package hence I would install:
```
sudo apt-get install linux-headers-2.6.20-16-generic
```

(2) Once you get the correct package name apt will install the dependent files as well. Many of these will be library (lib) files similar to dll files which you may be more familiar with. These will be installed automatically. GTK is used to provide a visual frontend to a large number of programs hence if you eg install the *alsaplayer *package you may wish to install the *alsaplayer-gtk* frontend.

I would suggest using the info available in the synaptic or adept package managers to get familiar with what happens at the command line and when doing the install through a package manager turning on the detail option so you can see what is happening in a terminal.

Also you could use the man command in the console (or --help) to find out more about program you intend to use ie:
```
man apt
man apt-get
apt-get --help
```

regards,
r

---

### Post by johnapeterson on 2007-08-01
I am almost there.
Got up on the net and install the current version of what I was needing, but when I type in 
"sudo apt-get install build-essential" I get the following:


john@john-desktop:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essential
 Can't find it.

Thanks for any help.
John

---

