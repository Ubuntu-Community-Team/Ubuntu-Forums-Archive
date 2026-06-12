---
title: "BSD users, I have some questions!"
date: 2008-01-30
forum: BSD
---

### Post by snakeeyes on 2008-01-30
I want to try Desktop BSD 1.6, since I heard and read reviews that it works really well, and has good hardware support as well.

The things I need to know r:

What file system does it use and how does it need to be partitioned?

What is their package management system?

Is hardware support really a lot worse than Linux?

What about multimedia such as flash, java and stuff?

Thanks!

---

### Post by mips on 2008-01-31
> **snakeeyes said:**
> 

What file system does it use and how does it need to be partitioned?

UFS. Leave blank space on your hd. The bsd partitioner will create a disk slice on this, then you create your partitions inside the slice, next you set the disklabel and thats it I think or what I can remember. [http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/install-steps.html](http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/install-steps.html)


> What is their package management system?

They use the Ports Collection system. This you can access via cli or gui. You can install binary or source packages.
[http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/ports.html](http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/ports.html) [http://www.freebsd.org/ports/index.html](http://www.freebsd.org/ports/index.html)


> Is hardware support really a lot worse than Linux?

I would not say so. In some cases bsd actually has better drivers than linux.
See the following to see if your hardware is supported:
[http://www.freebsd.org/releases/6.3R/hardware-i386.html](http://www.freebsd.org/releases/6.3R/hardware-i386.html)
[http://www.freebsd.org/releases/6.3R/hardware-amd64.html](http://www.freebsd.org/releases/6.3R/hardware-amd64.html)

> What about multimedia such as flash, java and stuff?

The only one you will have an issue with is flash, the rest are all fine. However there are workarounds to the flash issue.
1. You can run flash in linux emulation mode.
2. You can use a combination of Gnash, Mplayer and some plugings and stuff to make it work. 
See [http://www.riondabsd.net/2007/05/23/flash-on-freebsd-using-gnash/](http://www.riondabsd.net/2007/05/23/flash-on-freebsd-using-gnash/)

---

### Post by snakeeyes on 2008-01-31
Thanks, I will check out the links u gave me right now.

---

### Post by mips on 2008-01-31
> **snakeeyes said:**
> Thanks, I will check out the links u gave me right now.

Just keep in mind that they are for FBSD, the partitioner will probably be a nice gui in in DBSD.

---

### Post by -Rick- on 2008-02-01
Also keep in mind that BSD's want primary partitions to work with.

---

### Post by snakeeyes on 2008-02-01
I just downloaded it, I am going to check it out now.

---

### Post by snakeeyes on 2008-02-01
Desktop BSD is really good, actually the system seems very smooth. All I have to do know is configure power management and may consider keeping it on that machine. In LInux I had to enter:

Option "NvAGP"    "1"

Can this work in BSD?

Also if I want to blacklist modules in BSD such as sis_agp or agpgart then is it the same in BSD as in Linux such as:

/etc/modprobe.d/blacklist

Thanks!

---

### Post by Bachstelze on 2008-02-02
> **snakeeyes said:**
> In LInux I had to enter:

Option "NvAGP"    "1"

Can this work in BSD?

DesktopBSD also uses Xorg, and the nvidia drivers are basically the same. So yes, this would work.

> **snakeeyes said:**
> Also if I want to blacklist modules in BSD such as sis_agp or agpgart

This, however, wouldn't, since it is specific to the Linux kernel. FreeBSD (which DesktopBSD is based on) has almost everything built into the kernel by default, so if you want to disable something, you must recompile your kernel (this is *very* rarely needed, though).

---

### Post by snakeeyes on 2008-02-03
> **HymnToLife said:**
> DesktopBSD also uses Xorg, and the nvidia drivers are basically the same. So yes, this would work.



This, however, wouldn't, since it is specific to the Linux kernel. FreeBSD (which DesktopBSD is based on) has almost everything built into the kernel by default, so if you want to disable something, you must recompile your kernel (this is *very* rarely needed, though).
Hi, thanks for the reply, but sis_agp keeps interfering with suspend so that means I won't be able to get it to work without compiling my own kernel?

---

### Post by Bachstelze on 2008-02-03
> **snakeeyes said:**
> Hi, thanks for the reply, but sis_agp keeps interfering with suspend so that means I won't be able to get it to work without compiling my own kernel?

It keeps interfering *in Linux*! As far as the kernel is concerned, there is about as much similarity between Linux and BSD than there is between Linux and Windows.

Linux is not Windows, BSD is not Linux ;)

---

### Post by snakeeyes on 2008-02-03
> **HymnToLife said:**
> It keeps interfering *in Linux*! As far as the kernel is concerned, there is about as much similarity between Linux and BSD than there is between Linux and Windows.

Linux is not Windows, BSD is not Linux ;)
oh so that means that any modules that interfere automatically won't load?

---

### Post by snakeeyes on 2008-02-03
Hey BSD is actually pretty good, I can't believe Desktop BSD is more stable then OpenSUSE and suse has been the most stable and polished linux distro I ever used. 

If I install this on a laptop, how is wireless support, bluetooth and camera and stuff on BSD? Can any printer, scanner or all in one working on Linux work on BSD?

---

### Post by Bachstelze on 2008-02-03
> **snakeeyes said:**
> If I install this on a laptop, how is wireless support, bluetooth and camera and stuff on BSD? Can any printer, scanner or all in one working on Linux work on BSD?

For the wireless, it depends very much on what card you have. Bluetooth and webcams are, I guess (not 100% sure) a lost cause. Printers and scanners use CUPS and SANE, just like in Linux, so you should have no problems with those.

---

### Post by snakeeyes on 2008-02-03
> **HymnToLife said:**
> For the wireless, it depends very much on what card you have. Bluetooth and webcams are, I guess (not 100% sure) a lost cause. Printers and scanners use CUPS and SANE, just like in Linux, so you should have no problems with those.
Thats too bad cause everything else was working smooth. I am going to try to set it up but if it doesn't work then I am already booting with SUSE and that works great as well.

How come no one is developing for BSD, its a great system.

---

