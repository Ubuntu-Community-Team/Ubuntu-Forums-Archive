---
title: "Dell Latitude C800 problems"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by Bright Carver on 2007-12-12
Hi there

I'm trying to install Ubuntu on a laptop my girlfriend's sister gave us.

It's a Dell Latidute C800.  I've not been able to find much info on it, and the info I do find is a bit cryptic and esoteric.  Probably because I'm a moron or something...

Anyway, I tried the main CD and the alternative CD with the same result: The Ubuntu logo comes up, gives the list of boot options, and when I hit enter to install the screen goes blank and the computer freezes.

Has anyone got the same laptop?  How did you do it?

Thanks

Karl

(I seem to be cursed when it comes to Linux.  I've had so many hardware issues.  My home computer has a recovery partition and no floppy drive, so dual-booting is out until I can figure out a way to back up my recovery partition, my laptop has only USB internet so it's useless for Ubuntu, and the latest addition to the household, well, that's why I'm here today.  I keep trying, though!)

---

### Post by spiderbatdad on 2007-12-12
when the boot screen comes up you made need to hit F6 for boot options and at the end of the list of boot option at the bottom of your screen add noapic nolapic

try a search of boot issues. I will too, and see if I can post back for you more specifics

---

### Post by spiderbatdad on 2007-12-12
First things first: if your laptop fails to boot the LiveCD (i.e. hangs at a certain point), then you most likely have a common problem with "apic."

Solution: When given boot options for the LiveCD, press F6 for other options and you should see a command line with commands already entered. Simply add as required.

noapic nolapic

to the end of the line and press enter. The system should now boot without stalling.

if that did not work, try this:

noapic nolapic noapci noirqpoll nosmp

Note I've been informed :-just boot with "noapic", the usb ports will not function... also, when I boot with "nolapic", Xorg doesn't load the nvidia drivers correctly... however, when u boot with BOTH options, ("noapic nolapic"), the USB ports function fine, and xorg has no problems running at all (beryl and AIGLX run great). if others find this please tell me so I know it's common issue Follow On With HP dv6113us and Gutsy Gibbon installed, this worked, mostly. Modified the startup to include "-noapic -nolapic" but usb would only auto-mount when I used "-noapic -irqfixup". Now everything works wonderfully.

installed but not booting

As with the above, but at grub we need to hit the "e" key to edit our boot options. look for the longest kernel boot line if you've put the command no irqpoll on the linux image line in your boot loader (grub menu.lst) eg... example Linux-2.6-12-XXX blah noirqpoll splash and try booting. when you find the one that works-in terminal

---

### Post by Bright Carver on 2007-12-12
Hi, thanks for replying

I tried everything there.  It seemed to get a split second and a couple of boot messages further, but then it froze again.

If it means anything, a big green box appeared for a split second before it all went dark... ???

---

