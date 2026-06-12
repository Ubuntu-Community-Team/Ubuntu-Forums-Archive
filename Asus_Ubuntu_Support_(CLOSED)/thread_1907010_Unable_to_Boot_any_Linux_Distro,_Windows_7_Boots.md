---
title: "Unable to Boot any Linux Distro, Windows 7 Boots"
date: 2012-01-10
forum: Asus Ubuntu Support (CLOSED)
---

### Post by darmok on 2012-01-10
Background
-------------------------------------------------------------

I've been running both Fedora 14 and Windows 7 Professional on a home-built machine for about a year. The two operating systems are installed on different internal hard disks, and boot using Grub v1.99. The motherboard is an Asus M4A87TD/USB3 equipped with an AMD Phenom II 1075T processor and 16GB of RAM (G.Skill running at 1333Mhz). I'm posting to this forum because you guys are the only forum I've found with a dedicated Asus support board, and I really need to switch back from Fedora anyway.


The Problem
-------------------------------------------------------------

Since the beginning of December, Fedora 14 and all other distributions of Linux have been unable to boot. During the boot process, the Grub screen appears and allows me to select between the operating systems installed. When I attempt to boot Fedora 14, the Grub screen is replaced with a screen of kernel errors, which run until I shut off the machine. 

The same behavior occurs with all other distributions of Linux I've tried, including Ubuntu 11.10,  both as Live CDs and bootable USB sticks, regardless of whether the internal hard disks are connected to the motherboard.

All the while, the computer boots Windows 7 Professional without incident. I suspect that I may have allowed Windows 7 to update some kind of Asus motherboard driver or firmware, but I cannot find evidence of that in the "uninstall programs" control panel in Windows 7. Further, the Asus website does not appear to have any firmware update for the motherboard other than a BIOS update, which I have yet to perform.


Attempted Solutions
-------------------------------------------------------------

* Booting from a USB stick with the latest available Linux kernel
* Booting from Linux LiveCD
* Booting from LiveCD or USB stick with the internal harddrives disconnected
* Uninstalling all Windows 7 updates back to October 2011 (long before the problem started)


Solutions Under Consideration
-------------------------------------------------------------

* Updating the BIOS
* Replacing the motherboard


Questions to the Community
-------------------------------------------------------------

* Have you noticed such behavior in Linux-Windows machines before?
* Under what circumstances have you noticed this similar behavior?
* What do you think might be the cause of my problem?
* What solutions would you recommend I try?
* Do you think updating the BIOS might cause further problems?

Thanks everyone!

---

### Post by BC59 on 2012-01-10
Did you think to try installing older Ubuntu versions with old kernels? If your system was working before, maybe the new kernels are causing the problem.
Or you could try installing Ubuntu 12.04 alpha with the new kernel 3.2 RC.

---

### Post by darmok on 2012-01-10
For the record, I've tried LiveCDs of the following distributions:

Ubuntu 11.10 64-bit ............................................. Kernel errors
ArchLinux Core x86-64 .......................................... Black screen hangs until reboot
Linux Mint 11 AMD-64 ........................................... Kernel errors
Linux Mint 10 AMD-64 ........................................... Kernel errors
LInux Mint 9 AMD-64 ............................................. Kernel errors
Fedora 16 LXDE x86-64 ........................................ Kernel errors
Fedora 10 x86-64 ................................................ Black screen hangs until reboot
OpenSuSE 11.1 x86-64 ........................................ Kernel errors

I then realized that these all have one thing in common, namely, that they're all 64-bit. For grins, I tried two 32-bit distributions, and found:

Ubuntu 11.10 i386 ................................................ Nominal boot!
Fedora 14 Security Lab Spin ................................. Nominal boot!

It would appear that 64-bit kernel support has somehow failed for both new and older 64-bit kernels. Thanks for encouraging me to try more distros, BC59! I don't suppose you have any insight into this new discovery? What's curious now is that the version of Fedora 14 I was using was 64-bit and had been for a year. Thanks for the help!

---

### Post by Basher101 on 2012-01-10
it is definateley the newer kernels bugging with something here... If you want to run the 32 bit versions, be aware that not all your ram is detected, only 3 GB max. I can only agree to BC59's suggestion on trying the 12.04 Alpha kernel.

(whats funny for my home-built setup, i had to fight 4 hours with windows just to start the install, for ubuntu it took me 2 minutes lol)

---

### Post by BC59 on 2012-01-10
Did you try minimal installation?
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
I would suggest you to try the older versions first.

---

### Post by oldfred on 2012-01-10
With Ubuntu is it actual kernel error message or booting log error messages? If you did a BIOS update it resets BIOS to defaults, Did you have some other settings?

Sometimes a parameter is needed:

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)
Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

Sometime BIOS settings like AHCI or SATA drive in large or LBA not IDE?

---

### Post by darmok on 2012-01-10
Regarding Basher101's post: I certainly want to avoid having to use a 32-bit kernel. I built this system for doing a lot of virtualization work for school, so restoring 64-bit Linux functionality is my top priority. I'll probably remove the Windows install, too, just in case it was responsible for this mess.

I've just tried BC59's suggestions, and can report the following:

* Ubuntu 11.10 64-bit (Minimal CD) .......................... Black screen hangs until reboot
* Ubuntu 12.04 64-bit Alpha 1 Desktop .................... Kernel errors

I think it's particularly odd that both old *and* new 64-bit kernels suddenly stopped working. Shouldn't that indicate that something's changed on the machine and not in the Linux 64-bit kernels?

To answer oldfred's post: the errors feature on each row what appears to be a time-stamp, then a 16-digit hexadecimal number, then an error. The errors come in sets called "traces," and include such terms as:

rcu_sched detected stalls on CPUs/tasks
check_cpu_stall 
update process times
Call Trace:
amd_e400_idel_09a/0x120

At the end of some traces, the following term is printed:

Fixing recursive fault but reboot is needed!

This runs ad infinitum each time I try to boot a 64-bit kernel. As for the BIOS; I haven't made any modifictions to it. It's the same version that shipped with the motherboard, and there's been one update made to the M4A87TD/USB3 BIOS. I haven't fiddled with any of the settings, and can report the following:

* Overclocking is not active (and has never been)
* Core locker is disabled (and has never been)
* I've never needed to set NOMODESET in Grub
* All SATA drives are in IDE mode (and always have been)

I will try the other recommendations made by oldfred, though I'm concerned that updating the BIOS might make the problem worse. Is this a rational fear, you think?

Thanks!

---

### Post by Basher101 on 2012-01-10
all i can say is, as long as you can boot windows fine, it is not a hardware failure.

good luck onwards..

---

### Post by BC59 on 2012-01-10
And if you try Ubuntu 8.04 Minimal installation from the link I posted?

---

### Post by BC59 on 2012-01-10
To be sure there is no Hard drive issue (because you mentioned you are using separate HDDs) try only Ubuntu 8.04 on a Live CD and don't install it.

---

### Post by spacecheck on 2012-01-10
You'd probably want to want to try (scroll through a variety of) different memory configurations. If a Dimm were to go bad on dual-channel set-up, the kernel might have serious problems. 

You might make sure the system is not overclocked and check to ensure the BIOS is up to date and the settings are set to allow the OS to manage resource addressing.

If you can't get 64bit online, you may be able to crank-up a 32bit livecd, then go the the respective HDD & partition and examine the logfiles /var/log to see if there is an indication of what is causing the problem.

Good luck!

---

### Post by nothingspecial on 2012-01-10
Threads merged.

---

### Post by darmok on 2012-01-10
Just tried booting to an Ubuntu 8.04 LTS 64-bit live CD, with no success. Kernel errors consistent with the other Linux distributions appeared at bootstrapping. I'm virtually certain it's not a hard disk issue, as one of the things I tried early-on was to open up the case, disconnect the hard disks, and try to boot from the optical drive. I'm tempted to try updating the BIOS... any thoughts on whether that might cause more problems?

Thanks!

---

### Post by spacecheck on 2012-01-10
> **darmok said:**
> Just tried booting to an Ubuntu 8.04 LTS 64-bit live CD, with no success. Kernel errors consistent with the other Linux distributions appeared at bootstrapping. I'm virtually certain it's not a hard disk issue, as one of the things I tried early-on was to open up the case, disconnect the hard disks, and try to boot from the optical drive. I'm tempted to try updating the BIOS... any thoughts on whether that might cause more problems?

Thanks!
You'd probably want to want to try (scroll through a variety of)  different memory configurations. If a Dimm were to go bad on  dual-channel set-up, the kernel might have serious problems. 

You might make sure the system is not overclocked and check to ensure  the BIOS is up to date and the settings are set to allow the OS to  manage resource addressing.

If you can't get 64bit up and running, you may be able to crank-up a 32bit  livecd, then go to the respective HDD & partition and examine the  logfiles in /var/log to see if there is an indication of what is causing  the problem.

Good luck!

---

### Post by oldfred on 2012-01-10
Someone with same error and the parameters they used.

[http://askubuntu.com/questions/50451/error-fixing-recursive-fault-but-reboot-is-needed](http://askubuntu.com/questions/50451/error-fixing-recursive-fault-but-reboot-is-needed)

---

### Post by darmok on 2012-01-11
I tried the procedure posted by oldfred at [http://askubuntu.com/questions/50451/error-fixing-recursive-fault-but-reboot-is-needed](http://askubuntu.com/questions/50451/error-fixing-recursive-fault-but-reboot-is-needed) .

Unfortunately, it was unsuccessful. I'm going to attempt resetting the BIOS and/or updating the BIOS. After that, I think I might have to replace the motherboard, as I'm getting close to having to put the machine to serious use. Will advise.

---

### Post by Basher101 on 2012-01-11
you should try and see if a Ram stick went bad as _spacecheck_ suggested. Try booting with only one of the sticks inserted, then exchange it the one you took out and see if it is your ram that causes the errors.

It would suck if you replace the mobo and it turns out it is other hardware thats failing.

---

### Post by darmok on 2012-01-11
I just tried flashing the CMOS on the motherboard and updating the motherboard's BIOS to the latest version, version 2001. Neither procedure solved the problem, as Linux still produces kernel errors on boot. Further, I can't seem to select my boot disk using the boot menu by pressing F8. Instead, I now have to enter BIOS setup in order to change the boot disk manually. I'm tempted to revert to the original BIOS that I had, version 1102.

I'll try now the RAM test as Basher101 suggests, but I don't think the RAM is a problem as Windows 7 boots fine and recognizes all 16GB of it.

---

### Post by linux_tech on 2012-01-16
sys bd is listed in hcl.
[http://linuxhcl.com/browse/product?id=7584](http://linuxhcl.com/browse/product?id=7584)  
But did not see the cpu.

---

### Post by darmok on 2012-01-17
[SOLVED]

This issue has been resolved. Following the advice of Basher101 and Spacecheck, I inspected each of the four RAM sticks using memtest from the GRUB menu. One of the four was found to be defective. Upon restart using the three working RAM sticks, 64-bit Linux booted normally.

What had been throwing me off were the fact that both 32-bit Linux kernels and Windows 7 were booting just fine. I suppose that, since 32-bit Linux cannot resolve more than 3GB of RAM, it never looked past the functional 4GB RAM stick in the first RAM slot to the bad one, which was in slot 2. Windows 7 probably booted normally because it's too stupid to check for bad RAM.

Thanks to everyone who contributed to this thread, as I couldn't have managed without your suggestions and feedback. Special thanks to my friend, Mikhail, who assisted me with interpreting kernel errors.

---

