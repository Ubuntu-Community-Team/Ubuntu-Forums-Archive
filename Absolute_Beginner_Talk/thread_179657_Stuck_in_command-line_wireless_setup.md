---
title: "Stuck in command-line wireless setup"
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by Metacarpal on 2006-05-20
Hi!  I'm trying to install the linux drivers for my Orinoco 11b Silver (8421-WD "model 0110") wireless PCMCIA card using [these instructions]("http://wiki.splitbrain.org/wlan:orinocosilver"), and I'm a bit stuck.  After downloading and tar-ing both the pcmcia-cs and driver sources, it tells me to run ./Configure - When I do, I get this:

> metacarpal@musecatcher:~/pcmcia-cs-3.2.8$ ./Configure

    -------- Linux PCMCIA Configuration Script --------

The default responses for each question are correct for most users.
Consult the PCMCIA-HOWTO for additional info about each option.

Linux kernel source directory [/usr/src/linux]:
Linux source tree '/usr/src/linux' is incomplete or missing!
    See the HOWTO for a list of FTP sites for current kernel sources.

Configuration failed.

metacarpal@musecatcher:~/pcmcia-cs-3.2.8$

What do I do to fix this?  How would I go about finding the kernel source directory?

---

### Post by tonyr on 2006-05-20
Install package **linux-source** with your favorite package management utility
(apt-get, Synaptic, aptitude, etc etc etc)  Make sure the the packages that
actually get installed have the same version number as your installed
kernel image.  I'm not sure what it is in Breezy right now. In Dapper
it's **2.6.15-23**.  The source package is large, and shows up as
/usr/src/linux, which is what your configure/install process is looking for.

---

### Post by Metacarpal on 2006-05-20
OK - installed kernel-source using Synaptic.  It only downloaded the tar.bz2 file, so I ended up having to run file-roller as root to get it unpacked there (it went into /usr/src/linux-source-2.6.12/).  When I ran ./Configure:

> metacarpal@musecatcher:~/pcmcia-cs-3.2.8$ ./Configure

    -------- Linux PCMCIA Configuration Script --------

The default responses for each question are correct for most users.
Consult the PCMCIA-HOWTO for additional info about each option.

Linux kernel source directory [/usr/src/linux]: /usr/src/linux-source-2.6.12/

The kernel source tree is version 2.6.12.
  WARNING: the current kernel is sublevel 2.6.12-10-686.
The current kernel build date is Fri Apr 28 13:21:56 2006.

Build 'trusting' versions of card utilities (y/n) [n]: n
Include 32-bit (CardBus) card support (y/n) [y]: y
Include PnP BIOS resource checking (y/n) [n]: n
Module install directory [/lib/modules/2.6.12-10-686]:

Hmmm... /sbin/ksyms is broken.  Using /proc/ksyms...
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
Kernel configuration options:
    Kernel-tree PCMCIA support is disabled.
    Symmetric multiprocessing support is disabled.
    Preemptive kernel support is disabled.
    Realtime Hardware Abstraction Layer is disabled.
    High memory support is disabled.
    PCI BIOS support is disabled.
    Power management (APM) support is disabled.
    SCSI support is disabled.
    IEEE 1394 (FireWire) support is disabled.
    Networking support is disabled.
     Radio network interface support is enabled.
     Token Ring device support is disabled.
     Fast switching is disabled.
     Frame Diverter is disabled.
    Module version checking is disabled.
    Kernel debugging support is disabled.
    /proc filesystem support is disabled.
    PAE support is disabled.

Cardbus support requires kernel PCI bus support!
    To fix, re-run 'make config' and disable Cardbus support.

Configuration failed.

metacarpal@musecatcher:~/pcmcia-cs-3.2.8$ 

Any thoughts?  (Other than just breaking down and buying a new card ](*,) )

---

### Post by tonyr on 2006-05-20
[QUOTE=Metacarpal]
Any thoughts?  (Other than just breaking down and buying a new card ](*,))[/QUOTE]

Nope, we're outside of my expertise now.  I started with Dapper and know nothing
about Breezy and earlier.  What little research I did suggested that **/proc/ksyms** is gone with 2.6.x generation kernels, and that it has
something to do with a change in module management therein.  I draw
a conclusion that the configure/installation process you are using (they
provided?) is based on pre-2.6.x kernel expectations.  That's only a guess.

---

