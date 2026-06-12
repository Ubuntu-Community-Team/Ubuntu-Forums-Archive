---
title: "Virtual Machine"
date: 2007-07-03
forum: Apple PPC Users
---

### Post by aantn on 2007-07-03
What virtual machine is best to run a different version of Linux with Ubuntu as the host?

Also, besides for Mac On Linux (which won't work on my G5) are there any other ways to run OS X on Linux.

---

### Post by Calash on 2007-07-03
1 - I have had good success with both VMWare Server and Virtualbox.  Virtualbox is on my windows work PC, but has performed very well...and has sound, something VMWare does not have on the server edition.  VMWare server has a better interface IMHO, the tabs are nice and keep the screen very clear.

2 - There is a way to load OSX onto a VMWare session, and I assume Virtualbox as well.  It is against the EULA, and not supported...it is a pain to get working and runs very slow....but it does work.

[http://www.osx86project.org/](http://www.osx86project.org/)

I did this on VMWare server with 10.4...ran very slowly...too slowly to enjoy IMHO.

---

### Post by aantn on 2007-07-03
I suppose its possible that I'm wrong, but I'd assume that OSX86 is for intel chips ;)

Unfortunately, I have a ppc. Is there any virtual machine for ppc that supports os x as a guest os?

---

### Post by Calash on 2007-07-03
Bah....was not thinking when I posted.  Still, the site is a great resource for stuff like that :)

---

### Post by stmiller on 2007-07-03
There is a recent port of Xen in the works, if you are Xen savvy:

[http://wiki.xensource.com/xenwiki/XenPPC](http://wiki.xensource.com/xenwiki/XenPPC)

This should run any PPC OS inside PPC, in virtualization. Requires a G5 cpu though, as this port has been done by IBM for their cpus.

Or another option is qemu. Qemu can emulate other hardware, so you could run x86 OS inside PPC.

[http://fabrice.bellard.free.fr/qemu/](http://fabrice.bellard.free.fr/qemu/)

---

### Post by 3rdalbum on 2007-07-05
> **stmiller said:**
> There is a recent port of Xen in the works, if you are Xen savvy:

[http://wiki.xensource.com/xenwiki/XenPPC](http://wiki.xensource.com/xenwiki/XenPPC)

This should run any PPC OS inside PPC, in virtualization.

Doesn't look like it, I'm afraid:

> Operating System Support

Xen requires paravirtualization (operating system modifications) for performance. Other operating systems could certainly be ported to the Xen hypervisor interface,

As with Xen on x86, it looks like the operating systems need to be specially modified to run, and you can bet your bottom dollar that OS X has been designed not to run virtually.

---

