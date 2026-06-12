---
title: "trouble on a b&amp;w g3"
date: 2004-10-11
forum: Apple PPC Users
---

### Post by Anonymous on 2004-10-11
i've had no trouble with the x86 version of ubuntu on 3 different computers, but when i tried to install the ppc version on my g3 it would install, but when it reboots to finish installation, the boot fails. it makes it to yaboot, and i can still boot into osx, but i almost immediatly get a kernel panic. it says that it can't find dev/console. my thinking is that it needs /dev/console, but im not sure what i could do to change how it looks. i have reinstalled a couple of times to make sure it isn't just a fluke on the install, and ive also tried expert mode and choose both of the standard ppc kernels included.

thanks for any help

---

### Post by rkts on 2004-10-17
I'm having the same problem on my B&amp;W G3.

---

### Post by umouklo on 2004-10-20
I am also having the same problem on my color G3.  Did either of you get a solution yet?

Thanks,

Lorie

---

### Post by anon on 2004-10-26
I have the same problem on my B&W G3, that is a kernel panic directly after installation complaining of a missing /dev/console.  I know that this issue has been raised in the mailing lists as well with no resolution.  Does anyone know if this error has been raised in Ubuntu bugzilla??

I am currently using the latest 4.10 Warty Warthog release with a CD image created on 20/10/04.

---

### Post by Castaa on 2004-10-27
[QUOTE=anon]I have the same problem on my B&W G3, that is a kernel panic directly after installation complaining of a missing /dev/console.  I know that this issue has been raised in the mailing lists as well with no resolution.  Does anyone know if this error has been raised in Ubuntu bugzilla??

I am currently using the latest 4.10 Warty Warthog release with a CD image created on 20/10/04.[/QUOTE]
 Is this a problem for other flavor of Linux?  Are these 'old world' or 'new world' machines?

---

### Post by umouklo on 2004-10-27
Mine is definitely a Blue and Clear new world mac.  It is a G3 with 512 Mb of memory.  This problem seems to be confined to G3 macs.  It should be reported in Bugzilla.

Thanks,

Lorie

---

### Post by anon on 2004-10-27
Definitely a new world G3 B&W.  It runs Gentoo fine.

---

### Post by anon on 2004-10-27
I think this may be in Bugzilla under Bug Id #2613

---

### Post by cali on 2004-11-02
hi,

the problem is that, by the reboot the kernel modules load in a
different order, then during the installation.

I solved the problem, by compiling the "CMD64{3|6|8|9} chipset
support" (Device Drivers -> ATA/ATAPI/MFM/RLL support) into the kernel.

A simple way for a successful installation is, install your system with
the Warty CD until the reboot, then open a shell, or boot with your
favorite live-distro, make a chroot to your ubuntu system, configure the
kernel, if you are a kernel newbie, use the config file unter /boot/ and
change the entry for CMD64 chipset, compile, install your new kernel and
reboot to finish your installation.

I hope I could help you,

PS: I posted this already on the mailinglist

---

