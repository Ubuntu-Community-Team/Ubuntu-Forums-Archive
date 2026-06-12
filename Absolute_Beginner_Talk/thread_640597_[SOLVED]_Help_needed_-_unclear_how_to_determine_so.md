---
title: "[SOLVED] Help needed - unclear how to determine software pre-requisites"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by vortex0007 on 2007-12-14
In general, I don't understand what steps to take in Ubuntu 7.10 to determine if my system meets prerequisites for software that I would like to install. 

For a specific example, I'm reading through the installation document for the ATI drivers and it says the following:

The following packages must be installed in order for the Catalyst™ Linux driver to install and work properly:

    * XFree86-Mesa-libGL
    * libstdc++
    * libgcc
    * XFree86-libs
    * fontconfig
    * freetype
    * zlib
    * gcc 


So how do I figure out if these packages are already installed?

---

### Post by elspiko on 2007-12-14
Two ways:

Go to Synaptic Package Manager and search for the indivdual packages.

Or

```
sudo apt get install XFree86-Mesa-libGL libstdc++ libgcc XFree86-libs fontconfig freetype zlib gcc 
``` 

This will check if the packages are already installed, and if not, install them and any dependencies that those packages have.

---

### Post by vortex0007 on 2007-12-14
Thank you Elspiko. Now I'm curious - when I run 

sudo apt get install 

I receive: 

command not found

---

### Post by arochester on 2007-12-14
It has a hyphen missing:apt-get

---

### Post by vortex0007 on 2007-12-14
Okay - figured out the command should have been "apt-get install" - as soon as I did that it worked - except for the new error: 

"Couldn't find package XFree86-Mesa-libGL"

Off to go searching.

---

### Post by mcduck on 2007-12-14
If you are just trying to get the Ati driver working, forget about their instructions. Simple 'sudo apt-get install xorg-driver-fglrx' will download and install the driver for you automatically.

You might need to run 'sudo aticonfig --initial' after that to get your desktop configured properly.

(Or just use the Restricted Drivers Manager in System/Administration ;))

---

### Post by vortex0007 on 2007-12-14
Thank you for the reply. About 2 minutes of google searching gave me the courage to run the install without having the XFree86-Mesa-libGL file installed and everything worked as expected.

---

### Post by chr15t4f4 on 2008-02-21
Vortex,

Did you run the install of the ATI driver without the Mesa file? or did you run the install for xorg-driver-fglrx? Curious also what your system specs are. I am having the same problem with my Radeon X1300 in Xubuntu. Thanks!

---

### Post by vortex0007 on 2008-02-21
chr15t4f4,

To answer your question, I ran the original install without the Mesa file.

The computer I'm running is a Dell OptiPlex GX620. It's a 2.8 Ghz Pentium D with 3GB of RAM and a 256MB ATI Radeon X1950Pro video card.

I feel your pain with this. I probably lost at least 5 days total over the course of a month trying to make Ubuntu use my video card and two different monitors. I was never able to make Ubuntu work for me the way I had hoped. This was one of my first posts to this forum and - so I fought with the Ubuntu OS from December of 2007 through about a month ago before I admitted defeat and went back to Windows XP. Now my display drivers work and I have no problems runnng multiple monitors. 

I wish you better luck than I had.

---

