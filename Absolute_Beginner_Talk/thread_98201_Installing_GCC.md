---
title: "Installing GCC"
date: 2005-12-02
forum: Absolute Beginner Talk
---

### Post by khoma on 2005-12-02
I found a bunch of GCC packages on the install DVD. Since I've never used debians package system, I'm having some trouble getting it installed. I ran dpkg -i gcc-version-this-or-that, got a list of dependencies needed, installed those from the same disc and then everything seemed fine. Except, gcc is nowhere to be found.

I need GCC before I can get my wlan card working.

---

### Post by juicybananahead on 2005-12-02
Did you try...```
sudo apt-get install gcc
```

---

### Post by khoma on 2005-12-02
[QUOTE=juicybananahead]Did you try...```
sudo apt-get install gcc
```[/QUOTE]

Like I said, I need to compile the wlan drivers before I can get the wlan card working, thus I have no network, thus no apt-get.

---

### Post by Kvark on 2005-12-02
```
sudo apt-get install build-essential
```
Will install the various stuff you need to compile stuff from the CD. If that command doesn't work then you need to uncomment the line in /etc/apt/sources.list that says something about cdrom.

---

### Post by az on 2005-12-02
[QUOTE=khoma]I found a bunch of GCC packages on the install DVD. Since I've never used debians package system, I'm having some trouble getting it installed. I ran dpkg -i gcc-version-this-or-that, got a list of dependencies needed, installed those from the same disc and then everything seemed fine. Except, gcc is nowhere to be found.

I need GCC before I can get my wlan card working.[/QUOTE]


What wlan card?  Just about all the available drivers are already made and available to you on the install cd.

To compile something, you need to install the build-essential package.  It pulls in all the neccessary packages.  In this release (Breezy) the kernel was built with a different version of the gcc compiler than is provided by gcc.  You need to additionally install the gcc-3.4 package.  It too will pull in two other dependancies.

sudo apt-get install build-essential gcc-3.4

Or use synaptic and install those packages.  Instead of using the full kernel source, just use the header files in the linux-headers package.

sudo apt-get install linux-headers-2.6.12-9-386 (or 686 or k7 whatever version you are running)
Again, you can also install it with synaptic.

---

