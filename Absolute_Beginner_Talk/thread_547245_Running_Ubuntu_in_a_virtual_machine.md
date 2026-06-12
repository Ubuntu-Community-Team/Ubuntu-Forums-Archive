---
title: "Running Ubuntu in a virtual machine?"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by TheOrangePeanut on 2007-09-09
Is there a virtual machine for Windows that I can use to run Ubuntu while I'm in Windows?  Something free, I can't pay for it.

I ask because I'm trying to make the switch to Ubuntu but the graphics drivers crash my system.  I'm sure there is a way to fix the problem, but I can't test out anything from a live cd because, obviously, you can't save information.  Since I'm in school and a CS major, having a working PC in my room is very important, and I don't want to format until I find a solution to my graphics drivers problems.

---

### Post by Maestro23 on 2007-09-09
It's not free, but you can take a look at Vmware.  They have a 30-day trial version.

Vmware: [http://www.vmware.com/products/desktop_virtualization.html](http://www.vmware.com/products/desktop_virtualization.html)

---

### Post by Orbital75 on 2007-09-09
Yes, **Virtual Box **is what your looking for....
I run Ubuntu in Virtual Box on my Windows XP Pro.
It works great !!!  :KS

It's free and does the job very well.
If you need any help, I'd be glad to walk you through.

[http://www.virtualbox.org](http://www.virtualbox.org)


***  **Just a Note**:  I wouldn't run a Virtual Machine with less than 1 gig of Ram  ***

---

### Post by Paulmd on 2007-09-09
> **TheOrangePeanut said:**
> Is there a virtual machine for Windows that I can use to run Ubuntu while I'm in Windows?  Something free, I can't pay for it.

I ask because I'm trying to make the switch to Ubuntu but the graphics drivers crash my system.  I'm sure there is a way to fix the problem, but I can't test out anything from a live cd because, obviously, you can't save information.  Since I'm in school and a CS major, having a working PC in my room is very important, and I don't want to format until I find a solution to my graphics drivers problems.

VirtualBox

[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by the.phantom on 2007-09-09
well you could look into wui ?

[http://wubi-installer.org/](http://wubi-installer.org/)

[http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)
it operates from a folder in your windows file system !

---

### Post by gn2 on 2007-09-09
There *is* a free version of VMWare Server:  [http://www.vmware.com/download/server/](http://www.vmware.com/download/server/)

---

### Post by Orbital75 on 2007-09-09
That's  " **Wubi** " 

Wubi's nice but it modifies your Boot loader.
Just as a duel boot would.

---

### Post by gn2 on 2007-09-09
> **TheOrangePeanut said:**
> I don't want to format until I find a solution to my graphics drivers problems.

You don't have to format to set up a dual boot Windows and Ubuntu set-up.

You can even install Ubuntu 6.10 on a USB flash drive: [http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610](http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610)

---

### Post by Bothered on 2007-09-09
I quite like qemu: [QEMU]("http://fabrice.bellard.free.fr/qemu/")

It will run on Windows, although I don't personally know how to set-up hardware acceleration for it on a Windows machine.

EDIT: Also, qemu is free software (and hence is free to use).

---

### Post by nonewmsgs on 2007-09-09
> **TheOrangePeanut said:**
> Is there a virtual machine for Windows that I can use to run Ubuntu while I'm in Windows?  Something free, I can't pay for it.

I ask because I'm trying to make the switch to Ubuntu but the graphics drivers crash my system.  I'm sure there is a way to fix the problem, but I can't test out anything from a live cd ....

can we back up here for a second and ask umm what's wrong with the graphics drivers?  what driver are you using? what is your videocard?

and while you certainly can't save the changes, if you can set it up with the livecd it's the same way for the real deal.

also are you using desktop effects or beryl

---

### Post by oilchangeguy on 2007-09-09
> **TheOrangePeanut said:**
> Is there a virtual machine for Windows that I can use to run Ubuntu while I'm in Windows?  Something free, I can't pay for it.

I ask because I'm trying to make the switch to Ubuntu but the graphics drivers crash my system.  I'm sure there is a way to fix the problem, but I can't test out anything from a live cd because, obviously, you can't save information.  Since I'm in school and a CS major, having a working PC in my room is very important, and I don't want to format until I find a solution to my graphics drivers problems.

from your friends at microsoft. and it's free:
[http://www.microsoft.com/windows/products/winfamily/virtualpc/default.mspx](http://www.microsoft.com/windows/products/winfamily/virtualpc/default.mspx)

---

### Post by TheOrangePeanut on 2007-09-09
Thanks, Virtualbox looks perfect.

As for the problem itself, I'm using an Ati graphics card (Radeon 9500 Pro).  The drivers in the LiveCD crash my system to a dead stop, usually within 30 seconds of staring xserver, sometimes before the desktop even loads.  I think those are the open-source Ati drivers, right?  Well, when I still had Ubuntu installed, I installed the restricted drivers via the menus, but it suffered the same symptoms.  I also tried installing the official Ati drivers from their site, but I'm not Linux savvy just yet and that didn't work; I'm not sure if I didn't follow the instructions correctly or if it was crashing because the drivers just have that effect.

I know it is a driver issue because vesa drivers work perfectly fine, except there is no hardware acceleration at all, which is slow and I'm not going to use.  I'm PRAYING that there is an option in xorg.conf that is turned on that is causing the crashes and not the drivers themselves, but I won't know unless I can install the OS.  It's not looking good though :(

Thanks for the help.

---

### Post by Orbital75 on 2007-09-09
Virtual PC works well but there is no USB support.
Other than that, it's very nice.

---

### Post by n3tfury on 2007-09-09
another vote for virtual box.  you won't be disappointed.

---

### Post by funrider on 2007-09-09
laziest method - download vmplayer which is free, and then download the vm image of ubuntu from vmware marketplace.(u dun have to run the set up, u dun have to download ubuntu setup cd)

the whole process wont take you more than 2 hours if you have fast internet connection.

here is the link for ultimate ubuntu 1.4 which is based on 7.04: [http://www.vmware.com/appliances/directory/975](http://www.vmware.com/appliances/directory/975)

u can search from the same site for other distributions as well

---

### Post by TheOrangePeanut on 2007-09-09
I guess I didn't realize Virtualbox woudln't recognize my video card.  Is that how it always works or is there an option I can change?  Right now, all it knows is I'm using 8mb of video (I suppose that is just the way Virtualbox handles it...?)

---

### Post by Brightbelt on 2007-09-09
As for your ATI video card problem, try the 'Envy' program. There's a 'Deb' package available (the ubuntu compatible software package) for downloading Envy and it's an easy double-click install. Then just run Envy, choose to install ATI drivers and it should work from there. That program has worked for me when nothing else would.

Here's the website [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) 

Good Luck,...Frank B.

---

### Post by Paulmd on 2007-09-10
> **TheOrangePeanut said:**
> I guess I didn't realize Virtualbox woudln't recognize my video card.  Is that how it always works or is there an option I can change?  Right now, all it knows is I'm using 8mb of video (I suppose that is just the way Virtualbox handles it...?)

Oh, That. 

When running in a VM, you don't have 'real' hardware. Virtualbox creates a pseudo-video device. All the device does is make a picture on the screen. Forget about anything using hardware acceleration. You can change how much memory virtualbox allocates to this "video device."

---

### Post by gn2 on 2007-09-10
> **oilchangeguy said:**
> from your friends at microsoft. and it's free:
[http://www.microsoft.com/windows/products/winfamily/virtualpc/default.mspx](http://www.microsoft.com/windows/products/winfamily/virtualpc/default.mspx)

Have you had any luck running/installing a Linux Virtual PC on it?

I tried and failed.....  :(

---

### Post by castalla on 2007-10-21
I have 710 under VMware player ... but HOW do I save any settings changes, so I can get personalised screens and firefox bookmarks saved?

---

### Post by ArcaneCode on 2007-10-22
> **gn2 said:**
> Have you had any luck running/installing a Linux Virtual PC on it?

I tried and failed.....  :(

I have complete instructions for installing 7.10 under Virtual PC, give them a try and see if you have more success:

[http://arcanecode.wordpress.com/2007/10/18/installing-ubuntu-710-under-virtual-pc-2007/]("http://arcanecode.wordpress.com/2007/10/18/installing-ubuntu-710-under-virtual-pc-2007/")

Good luck,

   Arcane



:popcorn:

---

### Post by sheer on 2008-04-28
i've installed KQemu on a USB key with Ubuntu but I can't get the network side of things working.  I use a proxy to access the interent but my ubuntu install can't access the proxy.

Any ideas how I can configure this ?

---

