---
title: "Problems getting .deb packages installed (linked to Wireless problem)"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by stuh84 on 2006-08-18
Hi I've just installed Ubuntu (well okay for the second time today after it went haywire trying to load the network hardware again on boot and just hung).

I have a wireless card in my PC (a Safecom 54Mbps/SWLPT-54125), and its not seeming to recognise it correctly.

I've downloaded drivers from Safecom's site, but am having problems installing them.

I have a tar.gz, rpm, and what I assume to be whats needed, the .deb package.

It seems to start installing fine with dpkg -i, but it then askes "Where is the linux source build directory that matches your running kernel?". Unfortunately, I have no idea where to point it to. If this worked maybe there wouldn't be any problems, and it seems like a simple problem but I dunno.

I tried the #ubuntu channel and they recommended downloading the linux-headers and using dpkg -i on them which I did. This led me no further to the solution though, well maybe it did but I once I installed this no one seemed to help me as to what to do next.

This may turn into a wireless problem soon but for the moment I just need help installing this damn driver.

Thanks in advance to you guys

Stuart

---

### Post by stuh84 on 2006-08-18
Bump

---

### Post by &#12465;&#12452;&#12488; on 2006-08-18
I don't know which architecture you're running on, but I assume it's 386 or 686. If you're on 386 and have a fairly new computer, you might want to run *sudo aptitude install linux-image-686* (or linux-image-k7 if you've got an AMD Athlon/Duron CPU) to get a better suited kernel for your computer. After that, you'll want to reboot.

The kernel headers are installed by running the command *sudo aptitude install linux-headers-686* (swap away 686 with 386, k7 or whatever if it doesn't match your kernel). Then you can try that driver installation again.

---

### Post by stuh84 on 2006-08-18
Yep tried that, but every time it couldn't find them at all. I assume that requires an internet connection via Ubuntu....which is exactly the problem I'm having as I can't get the wireless card to work :cry:

---

### Post by &#12465;&#12452;&#12488; on 2006-08-19
I see... Can't you connect it to the internet by cable temporarily to fix the wireless?

---

### Post by stuh84 on 2006-08-20
Hmm, I'm tempted to try it again now. Uninstalled Ubuntu because of this and gave up, but I'd gone into Kubuntu with a wire via my laptop's wireless (the laptop's using XP) to connect to the internet. I'll give it another try today I reckon.

---

### Post by stuh84 on 2006-08-20
Right update on the problem, here is the terminal output:

stuh84@stubuntu:~$ sudo dpkg -i driverloader_2.26tiabocom_i386.deb
Password:
(Reading database ... 130492 files and directories currently installed.)
Preparing to replace driverloader 2.26tiabocom (using driverloader_2.26tiabocom_i386.deb) ...
Unpacking replacement driverloader ...
Setting up driverloader (2.26tiabocom) ...
Linuxant DriverLoader for Wireless LAN devices, version 2.26tiabocom

No pre-built modules for: Debian-testing/unstable linux-2.6.12-10-686 i686

Trying to automatically build the driver modules...
(this requires a C compiler and proper kernel sources to be installed)

Where is the linux source build directory that matches your running kernel?
[/lib/modules/2.6.12-10-686/build]
/usr/sbin/dldrconfig: line 597: gcc: command not found

WARNING: the kernel version () defined in
/lib/modules/2.6.12-10-686/build/include/linux/version.h
does not match the currently running kernel (2.6.12-10-686)
The cause of this problem is an incorrect kernel source path.
Please check that /lib/modules/2.6.12-10-686/build points to the right tree.
The cause of this is usually a missing or unconfigured
kernel source tree (and sometimes an incorrect directory or symbolic link).

However, proper /boot/config-2.6.12-10-686 was found.
Would you like to try using it (in a temporary kernel tree)? [yes] y

Unable to prepare temporary kernel tree

First, ensure that the proper kernel source and compiler packages
from your distribution vendor and/or the community are installed.

The Linux kernel can then be reconfigured by running "make menuconfig"
under the kernel source directory (usually /usr/src/linux).

Verify that the proper options for your system are selected.

Then compile and install your new kernel (for more information about
this procedure, see the README file under the kernel source directory),
reboot the system using the new kernel, and re-run "dldrconfig".
dpkg: error processing driverloader (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 driverloader
stuh84@stubuntu:~$

I have installed the linux headers and the linux image, and still coming up with the same problems

---

### Post by stuh84 on 2006-08-20
Bump

---

