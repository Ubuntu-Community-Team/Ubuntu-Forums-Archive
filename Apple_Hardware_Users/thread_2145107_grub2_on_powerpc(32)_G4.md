---
title: "grub2 on powerpc(32) G4"
date: 2013-05-14
forum: Apple Hardware Users
---

### Post by sacarde on 2013-05-14
hi,   I installed , from minimal-iso, lubuntu-Quantal and grub2-common ...

then I run:update-grub2

and it find kernel and initrd

then I run:grub-install /dev/sda

but I have error
> source_dir doesn't exist. Please specify --target or --directory

what can I do?
strange is that in /boot/grub I have only 2 files: grub.cfg e grubenv



thank you

---

### Post by este.el.paz on 2013-05-18
> **sacarde said:**
> hi,   I installed , from minimal-iso, lubuntu-Quantal and grub2-common ...
then I run:update-grub2
and it find kernel and initrd
then I run:grub-install /dev/sda
but I have error
what can I do?
strange is that in /boot/grub I have only 2 files: grub.cfg e grubenv
thank you

@sacarde:

You probably know more than I do, but I've done a fair number of installations on two G4 units . . . one thing, if you aren't doing "Guided" install you have to set up the "boot" partition and flag it so that the installer knows where to put it.  If you use "Guided" the installer will install it in the partition that it made.  However, for PPC it's "Yaboot" that is the boot manager, not GRUB; but an anonymous buddy hero of mine who posts here recently said that "Yaboot is GRUB, but it's for PPC . . . " . . . I'm paraphrasing and I probably didn't understand what he was talking about, but, rather than GRUB . . . look for Yaboot, I think it's version "1.3.16"????? 

e.e.p.

---

### Post by sacarde on 2013-05-19
with yaboot I have this error:

[http://digilander.libero.it/sacarde/data/err-grub-ppc4.png](http://digilander.libero.it/sacarde/data/err-grub-ppc4.png) 

whai is "guided" ?


thanks

---

### Post by este.el.paz on 2013-05-19
> **sacarde said:**
> with yaboot I have this error:
[http://digilander.libero.it/sacarde/data/err-grub-ppc4.png](http://digilander.libero.it/sacarde/data/err-grub-ppc4.png) 
whai is "guided" ?
thanks

@sacarde:

"Guided" is the choice made in the graphical installer to use the "automatic" install, after a number of times doing "manual" install I've found it's just easier to use "Guided, use largest free space" after I've used OSX Disc Utility to set up a partition as "free space" . . . and just let the installer set up the bootstrap partition . . . and the swap.  I've been doing dual boot installs . . . .

From your link it looks like you are doing CLI installs, and I don't know how to do that, but in doing a fair number of installs I know that getting the bootstrap partition set up has been a problem, even in Linux Mint . . . .  So, however you do your installs should identify the partition where you want Yaboot installed . . . also, "Quantal" is older, and if you have G4 it might be easier to try Lubuntu 12.04 for PPC and then try to use the graphical installer, it doesn't take too long to run, and try one of the "Guided" choices and just let it set up the system for you.  The only reason that might be a problem is if you are trying to share a "home" folder with several distros . . . .

e.e.p.

---

