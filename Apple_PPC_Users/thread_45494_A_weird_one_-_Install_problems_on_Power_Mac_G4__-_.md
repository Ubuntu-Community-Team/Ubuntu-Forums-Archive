---
title: "A weird one - Install problems on Power Mac G4  - kernel panic"
date: 2005-06-30
forum: Apple PPC Users
---

### Post by mr_coon on 2005-06-30
Here's a weird one.  I've tried both the Live CD and the install CD and both give me a kernel panic during booting from the CD - I never even see the install menu (or Ubuntu in the case of the live CD).  The same CD's work fine on my other PowerMac sitting next door.

I'm using the 5.04 CD's.  The systems in question are:

PowerMac G4 dual 450MHz, 128MB RAM (the one that panics)
PowerMac G4 single 667 MHz, 256MB RAM (runs the live CD fine)

Could it be the RAM, I've seem posts that say they used even less RAM, but I'm at a loss otherwise.  Could there be a problem with the dual processor configuration? Also, the firmware on both machines are up to date per the Apple website.  Any ideas???

---

### Post by Ptero-4 on 2005-07-01
[QUOTE=mr_coon]Here's a weird one.  I've tried both the Live CD and the install CD and both give me a kernel panic during booting from the CD - I never even see the install menu (or Ubuntu in the case of the live CD).  The same CD's work fine on my other PowerMac sitting next door.

I'm using the 5.04 CD's.  The systems in question are:

PowerMac G4 dual 450MHz, 128MB RAM (the one that panics)
PowerMac G4 single 667 MHz, 256MB RAM (runs the live CD fine)

Could it be the RAM, I've seem posts that say they used even less RAM, but I'm at a loss otherwise.  Could there be a problem with the dual processor configuration? Also, the firmware on both machines are up to date per the Apple website.  Any ideas???[/QUOTE]
 It's probably the dual CPU, sometimes the SMP support tends to go quirky and make the computer act funny.

---

### Post by colinhayes on 2005-07-03
[QUOTE=Ptero-4]It's probably the dual CPU, sometimes the SMP support tends to go quirky and make the computer act funny.[/QUOTE]

But SMP is not enabled in the default kernel, so it just ignores CPU#2.

---

### Post by Len on 2005-07-06
It can't be the RAM as well, since the installer works with 64 MB here (and the full ubuntu, very slow). You could try a different kernel (choose it at that boot: prompt). Also, what is the error?

---

### Post by mr_coon on 2005-07-06
Well, I see the exact same thing with the Debian 3.1 installer, no surprise there.  Also, same errors with the Ubuntu Live CD.  They also work on my single processor 667MHz G4 tower, but not in the dual processor 450Mhz G4.


The errors (as far as I can tell) are:

Oops, kernal access of bad area, sig: 11[#1]

bunch of other stuff (doesn't look like errors -"call trace")

Kernel panic:  Attempted to kill init!

I appreciate your help!! :smile:  :smile:

---

### Post by Len on 2005-07-06
Very weird... According to the [YellowDog Linux compatibility page](http://www.terrasoftsolutions.com/support/hardware/breakdown/index.php?hw_cat_id=6) linux should run just fine on such a dual G4.

You could try if YellowDog Linux works (another huge download). Also, do you have any expansions installed like PCI cards? You could try to remove those. I've seen once that Linux can crash on some devices, just like OS X would panic on faulty SCSI settings where OS 9 happily worked on.

I hope you can do something with this info, otherwise I'm clueless :(.

Good luck ;-).

---

### Post by mr_coon on 2005-07-06
Len you rock !!

There was a PCI card (an old ADB for OS9).  Took it out and we booted.  Many thanks!! \\:D/

---

### Post by Len on 2005-07-07
Way cool! Have fun with your new system, and don't forget to get the SMP kernel (synaptic) or compile your own ;). I have no idea if it is installed by default (you can also check that with synaptic).

---

