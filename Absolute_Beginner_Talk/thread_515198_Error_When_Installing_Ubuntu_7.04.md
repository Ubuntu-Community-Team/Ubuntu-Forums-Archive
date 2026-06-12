---
title: "Error When Installing Ubuntu 7.04"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by amneziac on 2007-08-01
I am trying to install ubuntu but when I boot the CD after restarting my computer, I click 'Start or Install Ubuntu'. After I select that I get an error that says:

MP-BIOS bug: 8254 timer not connected to IO-APIC
Kernel panic - not syncing: IO-APIC + timer doesn't work!
Boot with apic=debug and send a report with the 'noapic' option

Also I am partitioning my hardrive, so I have the C drive for Ubuntu and the D drive for Windows. After I install Ubuntu, how do I install Windows on the D drive?

Please Help

---

### Post by Tux Aubrey on 2007-08-01
Sorry to hear you are having problems.

I probably can't help directly but if you give details of your machine (processor, RAM etc) and which version of Ubuntu you are using, someone here will help.

And you might want to reconsider your boot sequence and choice of drives.  In general Windows is a bit touchy if it doesn't get the master drive (C drive) whereas Linux will be happy anywhere.  And Vista and XP are a bit different in terms of how they co-exist with Linux.

Take it slow and you will get there!

---

### Post by kebes on 2007-08-01
First of all if you are planning on installing both Windows and Ubuntu, it's usually better to partition your drive, then install Windows, then install Ubuntu last. If you install Windows last, it over-writes the master boot record, so that only Windows boots. Then you have to go through a few steps to fix the MBR. By installing Ubuntu last, it sets up the MBR for dual-boot and everything should work.


As for your install issue... you might be able to work-around the problem by passing boot flags to the kernel. When you boot the LiveCD, you get some options. Normally you just pick "Start or Install Ubuntu." However, instead, press "F6" (other options). This will then allow you to add options to the boot command.

Then try adding the option "noapic" and then press enter. See if it works better. If that doesn't work there are some other boot options you can try:
noapic
irqpoll
pci=nommconf
all-generic-ide
acpi=off
nolapic

Try each one individually, or all of them together, or various combinations. I know that doesn't sound very specific ("just try it and see what works!")...

If you tell us the exact make and model of your hardware (especially motherboard), and the version of Ubuntu you are trying to install, someone may be able to isolate the exact thing you need to do.


Hope that helps...

---

