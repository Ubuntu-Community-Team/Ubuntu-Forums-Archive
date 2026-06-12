---
title: "emulators ?"
date: 2007-10-22
forum: Apple PPC Users
---

### Post by sunnyhanda on 2007-10-22
Hi iam using ubuntu 7 in my imac g3.  i was wondering that is there any emulators that i can install so that i can run mac os 10.4 or any mac os x version within ubuntu 7.

imac 450, 1 gig RAM , 20 gig hard drive.

---

### Post by rjmdomingo2003 on 2007-10-22
> **sunnyhanda said:**
> Hi iam using ubuntu 7 in my imac g3.  i was wondering that is there any emulators that i can install so that i can run mac os 10.4 or any mac os x version within ubuntu 7.

imac 450, 1 gig RAM , 20 gig hard drive.

Either try Virtualbox or VMWare. Both employ virtual machines which run an OS within an OS.

---

### Post by frog_pilot on 2007-10-22
Look here

[MOL]("https://wiki.ubuntu.com/PowerPCFAQ#head-947c52de3db7e0bcf7b5842f2743895517eade25")

[qemu]("https://wiki.ubuntu.com/PowerPCFAQ#head-64cc8bf06e13df66fdc6d87ce37fe815cb3d18ae")

Virtualbox, Virtual Server, VM Ware arent designed for ppc Linux

I'm running Tiger in MOL on G4 Dual with good results. For installing MOL follow the linked howto in the MOL section of ppcfaq (link above).

---

### Post by frog_pilot on 2007-10-22
[QUOTE=sunnyhanda]hi dear friend thanks for your help and i have seen the MOL link you provide me even installed he MOL and subversion as shown, moreover it runs as well. i have used mac os 9 on it by DVD.

i want know that is it possible to mount mac os 10.3 iso(HFS file system) files which are in my external drive not CD or DVD, i mean mount from hard drive or from Ubuntu desktop(i have saved those 3 files on desktop).

thanks for your help.[/QUOTE]

I never tried to mount an iso. I by myself installed MOL from the source. I'm running my actual Tiger-Install on the internal drive inside MOL while running Linux. I never tried to mount iso files or other. But try it as described here and report if it works...

Maybe you find some more info on [MOL Wiki]("http://mac-on-linux.sourceforge.net/wiki/index.php/Main_Page") or this [discussion]("http://ubuntuforums.org/showthread.php?t=565388").

I'm actually working on my MOL-install. I want to manage to mount my internal data-hfs-volumes and get the network running.

---

