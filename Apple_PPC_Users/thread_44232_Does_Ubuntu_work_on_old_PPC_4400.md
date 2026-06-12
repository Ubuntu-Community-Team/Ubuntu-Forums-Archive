---
title: "Does Ubuntu work on old PPC 4400?"
date: 2005-06-25
forum: Apple PPC Users
---

### Post by newuser on 2005-06-25
Hi there,

Tried booting from old power PC (model before iMacs) but keeps booting into OS8.1. Does Ubuntu work on old machines (this one has 32MB of memory)? Thanks.

---

### Post by Ptero-4 on 2005-06-27
[QUOTE=newuser]Hi there,

Tried booting from old power PC (model before iMacs) but keeps booting into OS8.1. Does Ubuntu work on old machines (this one has 32MB of memory)? Thanks.[/QUOTE]
 That machine is an oldWorld Mac, to use Linux on it you need BootX (and your OS8.1) or quik.

---

### Post by Rxke on 2005-06-29
getting Ubuntu to work on oldworld macs is not always straightforward, though, so you'd do good to read up a lot on it, search both these forums and google for it, then decide if it's worth to try. 

IMO, your machine might be a bit underpowered, to put things polite, esp. the limited memory will make stuff crawl.

---

### Post by leverknight1 on 2005-07-06
ewwww you might want to go [here](http://sonnettech.com/product/crescendo_l2.html) this is a g3 upgrade that should work to speed it up but idk if it is suported under linux

---

### Post by Len on 2005-07-06
On some oldworlds I tried I get a 'timezone' error after which Ubuntu refuses to run, and on others BootX crashes instantly... Since most Mac distros officially don't support oldworlds (only G3 and up) you can expect some problems, though most should work fine.

Anyway, a G3 upgrade is nice but not a big speed improvement compared to the speed improvement you will get with extra RAM. Ubuntu with a fancy GUI can't run on 32 MB memory (well, with giant swap space it could theoretically, if you want to wait days for your apps to launch...). It requires 128 MB or more to run acceptable and 256 - 512 MB to run fine. And a supported graphics card with 2 MB VRam. This goes for all Gnome/KDE Linux distributions; IceWM might run acceptable on 96 MB, but forget about OpenOffice then.

Without the bloated X11 GUI it is a different story though, then Linux will run just fine on your 32 MB RAM. With a command line general desktop work (office, webbrowsing, etc) is not doable, but you can run a file/web server with bells and whistles, or function as router or printer share. Nice if you want to have an online database for your work that can be accessed anywhere and spit out PDFs of the data you specify for example.

Now to the part of actually running Linux. You'll need [BootX](http://penguinppc.org/bootloaders/bootx/). You will also need the kernel and the ramdisk image of the system you want to install. Ramdisk images often end at .gz (e.g. initrd.gz)

Make a new folder in your System Folder (or whatever you called your system folder) called "Linux Kernels". Inside this folder you'll have to put the kernel image you want to use, and the RAM disk image. Get them from your Ubuntu install or live CD (sorry, don't have them right here so can't give you the names).

Now install the BootX control panel (or launch it as if it was an application). You'll have to select the kernel image and RAM disk. Additional command lines aren't neccesary yet, unless your screen refuses to display anything. Click on the Linux button and Linux will boot. If you have installed a Linux you'll have to copy the kernel of your installation and provide the root device in BootX. There are numerous documents available on this topic (search google).

For web, server and other command line purposes Gentoo Linux (easy) and FreeBDS  (moderate) are my favorite systems. For PPC Desktops I prefer Gentoo, Ubuntu and YellowDog. Mandrake is one to check out as well. I just wished they'd port Syllable to PPC. Would make a great system for old and newworlds since it doesn't rely on X11 ( [http://www.syllable.org/](http://www.syllable.org/) ). Mac OS 7.x and 8.1 are nice desktops for your machine as well (OS 9 is rather useless), in combination with the iCab webbrowser and ClarisWorks.

Good luck!

---

