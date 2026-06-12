---
title: "performing dual boot without GRUB"
date: 2010-03-21
forum: Apple Hardware Users
---

### Post by wearyroad on 2010-03-21
Hey all, 

Recently I had to reinstall the Mac portion of my operating system from CD because the GRUB menu I installed was wreaking havoc on it. I know the "alt/option boot" way to start up a mac with a choice between different partitions/hard drives available to choose from, and I think it'd be safer to install linux on a partition and run it like that. Is this feasible? Has someone done this? 

Any and all help appreciated! :D

---

### Post by nixscripter on 2010-03-21
This is the only thing I know about. It's called yaboot, and works on PPC machines only (I did it a few times): [http://www.gentoo.org/doc/en/handbook/2004.2/handbook-ppc.xml?part=1&chap=10]("http://www.gentoo.org/doc/en/handbook/2004.2/handbook-ppc.xml?part=1&chap=10")

But I don't know if that is what you had in mind.

---

### Post by wearyroad on 2010-03-21
> **nixscripter said:**
> This is the only thing I know about. It's called yaboot, and works on PPC machines only (I did it a few times): [http://www.gentoo.org/doc/en/handbook/2004.2/handbook-ppc.xml?part=1&chap=10](http://www.gentoo.org/doc/en/handbook/2004.2/handbook-ppc.xml?part=1&chap=10)

But I don't know if that is what you had in mind.

Thanks for the quick reply! I am on an intel, though. Do you think it's possible to just install it on a partition? 
I think it is, but I've had enough of reinstalling the operating system on one computer.

---

### Post by linuxopjemac on 2010-03-22
You need [rEFIt]("http://refit.sourceforge.net/"), version 0.14. Install it in OSX. Sync the partition table from within refit (partition tool).

Then maybe you have to update Grub, first try rEFIt.

---

