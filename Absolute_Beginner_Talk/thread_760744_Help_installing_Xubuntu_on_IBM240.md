---
title: "Help installing Xubuntu on IBM240"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by Brian_M on 2008-04-20
I've tried the options in the other 2 IBM240 threads without luck.

So, the IBM 240 has no floppy (there's an external available, but I don't have it), has no CD drive (and will not boot from an external), will not boot from USB and will not boot over PXE/Network.  I have a need for Win98 on the laptop to run proprietary car diagnostic software (that doesn't work in WINE, or at least I couldn't get it to work). Talk about a challenge. :D

The laptop has a fresh load of Win98 on a 6gb hard drive.  Maxed out memory (138 IIRC), and a 333mhz processor.

So, I've tried downloading Xubunu and using Unetbootin ~ this fails after the reboot (I forget the exact error, that was a week ago any my first attempt).

I tried WUBI (the internet version), which takes FOREVER to download Xubuntu, reboots and hangs at a splash screen that's got an abstract bird image.  I left this running as I slept one night with no change.

I've tried to use Daemon Tools to load the .iso within Win98, but it fails there as well (never even gets through the windoze installer).  Similarly, sharing a drive over my network with a CD in another computer also fails.  I also just tried using the "boot from cd", using GRUB for DOS ~ that got no response.

So, I've tried each option from here:

[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

With failure all around.  I've searched and worked on this for a week off and on now.  Normally I can figure this stuff out myself, but I'm at a loss here and would like some assistance.

Thanks in advance.

Brian

---

### Post by Brian_M on 2008-04-21
Bump:

I ended up trying a few different versions of WUBI yesterday, all failed when it came time to find my NIC (I have 4, 3 wired PCMCIA and one Wireless PCMCIA ~ no on-board nic available).  I almost got somewhere with Unetbootin when downloading the Xubuntu Alt disk and copying the contents to the hard drive.  It failed when looking for a CD drive though, and I could find no way around it.

So, without putting the HDD in another laptop with a CD drive, I don't see how I can get it loaded on this laptop.

Hope someone else has an idea to try.

Brian

---

### Post by hums07 on 2008-04-21
My laptop cannot boot from CD so I usually install using the method from the same link with your first post (i.e. from Windows). If you can tell in more detail what is wrong during installation. I may be able to help.
Note that because you have Win98, you can only use the method using Loadlin.
Edit: I even succeeded to run liveCD using similar approach (from WindowsXP). I blended the method from the above link with this one: [https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

---

### Post by Brian_M on 2008-04-22
> **hums07 said:**
> If you can tell in more detail what is wrong during installation. I may be able to help.


I'll get some specifics when I have some free time...

> **hums07 said:**
> 
Note that because you have Win98, you can only use the method using Loadlin.


I fail a main requirement of loadlin here...

> 3.2.  Things that are assumed:

  ·  You have successfully installed Linux.

Thanks for the reply though!

Brian

---

### Post by Brian_M on 2008-04-22
Okay, for unetbootin, I get to the Gui setup, through the Englich lang. and US keyboard, then it scans for hardware and kicks back that there are no network interfaces detected and none of the 4 PCMCIA NIC's will change this result.  1 is a 3com FE575CT-D, one is a 3com 3C589D-TP, one is a Xircom CEM56-100 and the last is a Netgear WAG511 (dual band wireless).  

Setting up the network manually makes no change.

---------------------------------------------------------

Using the most current version of Wubi (8.04-beta-rev495):

I get a Visual C++ Runtime error just after the initial settings screen (user name, password, version, etc...)  On another version I was able to get it to download and boot into a GUI, but it failed at some other point that I have no forgotten.  

Brian

---

