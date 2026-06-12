---
title: "old world install problems"
date: 2005-07-04
forum: Apple PPC Users
---

### Post by zxee on 2005-07-04
I have a beige G3 300Mhz, recently upgraded ram to 320MB two hard drives one is off a sata card so it isn't recoginzed-that's not the problem though. I have a 20Gb drive partitioned, but I can't get past the "probing for network" issue I posted about weeks ago.
I tried modprobe mace and also cded /lib/modules2.6.10-powerpc/... and tried modprobe there also but I just get back "fatal mace not found". 
The keyboard is a problem also I'm using a ADB apple design keyboad (model M298D) if I just select us english the keys are a total mess. The best I can come up with is portegese-although some of the keys are incorrect for my keyboard with that layout too, but it's managable. 
I have been able to get  linuxppc (2000) to install from cd. I wonder if it's possible to use that install to get ubuntu installed? Any ideas appreciated.

---

### Post by Len on 2005-07-06
Do you use BootX to boot your Linux (don't know if that's needed with the beige G3s)?

If so, make sure you are using the proper Linux kernel from the Ubuntu CD (there are three, you want the general ppc, NOT the Power3). Only thing I can think of...

---

### Post by zxee on 2005-07-07
[QUOTE=Len]Do you use BootX to boot your Linux (don't know if that's needed with the beige G3s)?

If so, make sure you are using the proper Linux kernel from the Ubuntu CD (there are three, you want the general ppc, NOT the Power3). Only thing I can think of...[/QUOTE]

Yes I am using the powerpc kernel and of course bootx ( the old world macs won't boot a non-mac cd w/o bootx) Macs (old world anyway) are awful to get linux on. Compared to the pc world where there are many "light" distros for older pcs :-? 
Oh well just another reason to stay away from apple products.

---

### Post by Len on 2005-07-07
> Oh well just another reason to stay away from apple products.
For Linux you sure want a well supported PC. There are not too much people working on old Apples (actually no one right now, probably lack of interest... BootX and miBoot are dead). But I have a Mac for the Mac OS, no one keeps me away from that ;-). 

In your case I think that if another distro installs fine it is just the lack of Mac support of Ubuntu PPC. You could try YellowDog Linux or Mandrake PPC. They are doable, and can be configured to be light. Gentoo PPC also works like a charm on older macs, but in that case I'd hook up your G4/G5 to help compile, unless you want to wait for 2 days :P. My poor 8600 took a week alone... but works fast. Debian is also an option, as well as Darwin. With an ATI card with 8 MB RAM OS X 10.4 Tiger will also run on your machine with a little hack (search for XPostFacto). Or you just keep it with OS 8 or 9.

So, don't trash it yet.

EDIT:
[quote=Tommy]I've tried the hints on the wiki at
[https://wiki.ubuntu.com/InstallOnOldWorldMacs](https://wiki.ubuntu.com/InstallOnOldWorldMacs) but no luck. The relevant modules do seem to load... the mesh module loads fine, mace is not on the Hoary CD... ( [http://ubuntuforums.org/showthread.php?t=27831](http://ubuntuforums.org/showthread.php?t=27831) )[/quote]
There you have it, they replaced mace with something else. Just try the Warty CD and update everything with Synaptic.

---

