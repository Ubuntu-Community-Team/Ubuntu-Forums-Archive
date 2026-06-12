---
title: "Please help me with the live cd."
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by jcolepdx on 2007-08-31
I would like to make the switch from windows to linux for several reasons.  I want to give ubuntu a test run before installing it.  I have downloaded, mounted and verified the live cd.  When booting from the cd and selecting start or install, I eventually end up with a black screen.  I have tried just letting it sit for over half an hour, but nothing. When I try to start in safe graphics mode I get the following:


(WW) VESA: no matching device section for instance (BUS ID PCI:1:11:0)
(EE) VESA (0): cannot read v_bios
(EE) screen found, but none have usable configuration

(WW) open ACPI failed (/var/run/acpid.socket)

THE X SERVER IS NOW DISABLED. RESTART GDM WHEN IT IS CONFIGURED CORRECTLY.


so after reading several hours worth of posts that relate generally, but not specifically to my problems... here I am.  Any assistance would be greatly appreciated.  Thanks!

HP Pavilion XT853
866mhz Pentium 3
384mb ram
nvidia geforce4 mx 420

---

### Post by Jimmyfj on 2007-08-31
Hi and welcome to Ubuntu

You can chose one of two things: First you can try to boot up the live Cd in Safe graphics mode. If this does not work, you could try and download the alternate install Cd and make a dual boot. But before you do that. Check the MD5SUM on the iso file you downloaded. Does this add up then there's the alternate install Cd.

---

### Post by diatribe on 2007-08-31
try adding -noacpi to your boot options

---

### Post by jcolepdx on 2007-08-31
[I]Hi and welcome to Ubuntu

You can chose one of two things: First you can try to boot up the live Cd in Safe graphics mode. If this does not work, you could try and download the alternate install Cd and make a dual boot. But before you do that. Check the MD5SUM on the iso file you downloaded. Does this add up then there's the alternate install Cd.[/I]

Thanks Jimmy.

I have attempted to boot in safe graphics mode.  That is where I found the error codes.  I checked the md5sum before mounting the iso and ran the check disk option at the boot screen.  I would like to run the live cd before I install.

---

### Post by jcolepdx on 2007-08-31
*try adding -noacpi to your boot options*

Where do I do this?  At the prompt after being booted out of safe graphics mode or is there an option at the initial boot graphical boot screen?

---

### Post by diatribe on 2007-08-31
at the screen where it asks install ubuntu run in safe graphics mode etc that is where you need to add it

---

### Post by jcolepdx on 2007-08-31
Thanks.  I'll give it a try.

---

### Post by jcolepdx on 2007-08-31
From the boot options screen:

F6
-noacpi

doesn't work, I still end up with a black screen after the system attempts to load.

I also tried:

F6
apci=off

same result.

any more ideas?  anyone?  Beuhler?

---

### Post by csixx on 2007-08-31
There are a number of options you can try at bootup.
All for various issues. Best Idea is try them, one option is sure to boot for you.

Good list/tutorial here:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by alienexplorers on 2007-08-31
Did you try running in safe graphics mode.  By the errors you got it almost seemed like the live cd could not set up a proper graphics mode for your system.  as for the ACPI error is there a option in your BIOS to enable or disable it.  If so enable it.  You could also check for a BIOS update and see if one is availible for your machine.  You would not be suprised how many errrors can be fixed by updating the BIOS.

---

