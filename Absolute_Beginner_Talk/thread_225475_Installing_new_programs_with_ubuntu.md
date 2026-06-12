---
title: "Installing new programs with ubuntu"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by StaticNexxus on 2006-07-29
i have tried to install airsnort with ubuntu but for some reason it doesnt work i got the the latest version of make by typing sudo apt-get install make into the terminal and it worked but when i type make all or make install after i have configured the package it comes up with an error message saying no tarket specified and no make file found.

What do i do to fix this problem?

---

### Post by Smandola on 2006-07-29
StaticNexxus,

I haven't used the 
```
sudo apt-get install make 
```

before, instead, I used the 
```
sudo apt-get install build-essential
```
which I think includes the make as part of a larger packages.

I think you should also be able to use Synaptic Package Manager
Navigation from the menu is: System > Administration >Synaptic Package Manager.  From there you can search for build-essential.

Good luck and post back if this doesn't work, or need more help.
s.

---

### Post by abowman on 2006-07-29
It looks like you may need to have the kernel headers installed.

---

### Post by fensirien on 2006-07-29
It sounds like the configure script failed.

> To compile AirSnort, do the following:

    * Get your drivers working! To do this you may need one or more of the following
          o Kernel source
          o PCMCIA CS package
          o wlan-ng package
          o Orinoco driver patches
          o Host AP drivers

    * Install the LATEST version of libpcap. Please make sure that you have removed any old version of pcap that may be resident on your system. (not required for Windows users.)

    * Make sure you have gtk+-2.2 installed as AirSnort is a gui application. You will also need gtk+-devel

    * Linux users perform the following steps

          # tar -xzf airsnort-0.2.6.tar.gz
          # cd airsnort-0.2.6
          # ./configure
          # make
          # make install       (optional)
          

    * Poof you're done. The airsnort executable is in the airsnort-0.2.6/src subdirectory, do with it what you will. There are some man pages in airsnort-0.2.6/man 

Make sure you have all the dependencies. The configure script is quite verbose and will tell you why it failed.

---

