---
title: "363 kernel vs 686 kernel - Core Duo"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by unconquerable on 2006-07-20
After starting over a few times, reinstalling ubuntu to figure out various wireless problems, I have that working.  I wanted to update to the 686 smp kernel as I am running an Intel Core Duo and would like to get the full functionality out of it.

The question:

I was looking throught automatix and the programs it contains which say they are for 363, and or 64bit and ppc.   Does this mean they will not work properly with the 686 kernel?  If so, should I just stick with the 383 kernel until better support is available?

---

### Post by mcduck on 2006-07-20
everything compiled for 386 kernel should work with k7-, 686- and 686-smp-kernels with no problems :)

---

### Post by tonyp1969 on 2006-07-20
I am running the 686 SMP and everything works lovely.

---

### Post by NewDisciple on 2006-07-20
Same here. Intel duo core working fine with 686-smp.  Why use only half of your computer when you can use all of it?

---

### Post by unconquerable on 2006-07-20
Do any of you have a 30-60 second delay when booting.  After installing the 686 kernel, my system, stalls when it says,

"mounting root file system"

Then it continues with the boot.

---

### Post by agurk on 2006-07-20
Yep, that is a known bug, see: [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/50313/](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/50313/)
Here's a similar one you might want to keep on your radar screen: [https://launchpad.net/distros/ubuntu/+source/linux-source-.6.15/+bug/49070/](https://launchpad.net/distros/ubuntu/+source/linux-source-.6.15/+bug/49070/)

(note the workaround mentioned: *If I change "Serial (ATA) mode" from "AHCI" to "Compatibility" in the BIOS, I don't experience this problem.*)

---

### Post by unconquerable on 2006-07-21
> **agurk said:**
> Yep, that is a known bug, see: [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/50313/](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/50313/)
Here's a similar one you might want to keep on your radar screen: [https://launchpad.net/distros/ubuntu/+source/linux-source-.6.15/+bug/49070/](https://launchpad.net/distros/ubuntu/+source/linux-source-.6.15/+bug/49070/)

(note the workaround mentioned: *If I change "Serial (ATA) mode" from "AHCI" to "Compatibility" in the BIOS, I don't experience this problem.*)

Thanks for that, I am still a n00b and do not know where to look for these things, I will try the work around when I get a chance.  You Ubuntu guys have been great!

---

