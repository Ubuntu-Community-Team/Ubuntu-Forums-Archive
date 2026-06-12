---
title: "Installing wireless card drivers"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by Espiox on 2006-08-20
I downloaded Ubuntu yesterday, and everything seems to be going fine. I got the Linux drivers for my wireless card (Safecom SWLPT-54125) and tried to install them. However, the terminal box asks me where the source or the kernel or something is, saying it's usually in usr/src/linux, but it doesn't appear to be there. What do I do here?

---

### Post by stuh84 on 2006-08-20
I can't offer any help, I've had exactly the same problem with the same card myself, which is why for now I've given up on Ubuntu. I had no problem with Ubuntu working on another PC I had at one point with wired network, but until I can find some help on making this work with Ubuntu, I'll stick with XP, and get a Mac at a later date, because of its JUST MAKE IT WORK feature.

---

### Post by secret_force on 2006-08-20
ey Espiox

can you copy --> paste the exact message of the terminal in your post, because now I don't really know what it's trying to say.

---

### Post by PedroDelGibbio on 2007-02-26
I've been trying to install these drivers too but with no luck.

I ran the driverloader_2.26tiabocom_i386.deb file, chose the 'install' button and away it went.

The window pops up and the progress bar spins around but it stays like that permanently and doesn't finish.

When I eventually had to restart the computer, install programs wouldn't run.  From the Synaptic error message I got to the point of clearing down (I think) the hung install by running dpkg --configure -a and accepting the default build location it gave me.

I think I'm back to where I was when I started now, but no closer to getting the wireless card working.

Help?!

---

### Post by PedroDelGibbio on 2007-02-26
Scratch that... it's working.  I'm not entirely sure how, but it's working.

I found in Device Manager that it had automatically detected my card which was a good start so I then had a poke around in 'Networking' and put in the SSID of my wireless network and the password.  It didn't work straight away but after a reboot, it appears to be working.... well, it IS working.

I'm not sure how much (if any) of this is down to my running that earlier dab file and how much may be Ubuntu just being 'plug and play'

Not quite sure how I got to this point so any thoughts would be appreciated.

---

### Post by PedroDelGibbio on 2007-02-26
Perhaps I spoke a little too soon.  I tried installing a wireless network utility to check available networks / signal strength and got the following report 

Errors were encountered while processing:
 driverloader
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up driverloader (2.26tiabocom) ...
Linuxant DriverLoader for Wireless LAN devices, version 2.26tiabocom

No pre-built modules for: Debian-testing/unstable linux-2.6.17.11-generic i686-SMP

Trying to automatically build the driver modules...
(this requires a C compiler and proper kernel sources to be installed)

Where is the linux source build directory that matches your running kernel?
[/lib/modules/2.6.17-11-generic/build]

Building modules for kernel 2.6.17-11-generic, using source directory
/lib/modules/2.6.17-11-generic/build.  Please wait...

ERROR: Module build failed!
Please examine the log file "/var/run/dldrconfig-buildlog.txt" to determine why.
dpkg: error processing driverloader (--configure):
 subprocess post-installation script returned error exit status 1


Is this a throwback to my earlier hanging install or a new problem??

---

