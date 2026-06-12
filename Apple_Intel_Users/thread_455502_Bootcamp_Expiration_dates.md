---
title: "Bootcamp? Expiration dates?"
date: 2007-05-26
forum: Apple Intel Users
---

### Post by keifer on 2007-05-26
Looking at installing fiesty, but the wikipages say to use bootcamp, but to uncheck the option to install drivers. Now, bootcamp (the betas) have a limited timespan before they expire, and I am weary of expiration dates. 

What I need to know is if bootcamp is just used for partition work, or if it does more (like installing a bootloader). If it use it without the drivers installed, reason tells me it will just partition, and the bootloader will be handled by grub/elilo. I *really* hate the idea of being dependent on bootcamp, and then having to pay to continue using it once the experation date comes up.

---

### Post by AWerner32 on 2007-05-26
Boot camp only partitions, Use refit, it works beautifully. Also since when does boot camp have an expiration date?

---

### Post by keifer on 2007-05-26
Thanks for the advice on refit.

As for the expiration, the manual for bootcamp says: 

"WARNING:  
Boot Camp Beta is prerelease software licensed for use on a trial basis for a limited time."

---

### Post by benanzo on 2007-05-26
The only technical use Bootcamp has if you've updated OS X past 10.4.6 is for burning the Windows driver disk.  If you have no interest in Windows, or already have the drivers, bootcamp is worthless.  The EFI on Apple machines already supports booting in BIOS emulation and Ubuntu can do all the partitioning for a multiboot system itself.

---

### Post by AWerner32 on 2007-05-26
boot camp also is helpful because it will restore the partition it creates to the original mac partition non destructively if you plan on using ubuntu only on a trial basis. If anybody can tell me another way to do this it would be awesome.

---

### Post by ivesjd on 2007-05-27
Im not sure, but you could try gparted (on the ubuntu livecd) but it may not be able to "grow" the partition.

---

### Post by ronocdh on 2007-05-28
> **ivesjd said:**
> Im not sure, but you could try gparted (on the ubuntu livecd) but it may not be able to "grow" the partition.
In my experience iPartition would be a wiser choice because it is friendlier to HFS+. I mean, can't you tell by the name alone? ;)

---

### Post by bauhaus on 2007-05-28
I've recently installed Fiesty on my new Intel Mac Mini  (Core 2 Duo) and did without Bootcamp alltogether. In the end after exploring the options (and having little interest in Windows) I booted up with my original CD and used Apple DiskUtility to partition the internal drive into two: OSX (J-HFS+) and FREE space for Ubuntu.

It worked beautifully and I was able to add an extra Swap partition out of the FREE space :)

I guess the only good use for Bootcamp is the non-destruction partition editing, that is you can restore OSX to the whole volume without re-formatting. Still you could always use a tool like CCC (CarbonCopyCloner) to duplicate your OSX partition before reformatting the drive. I know it's a bit more involved but it would work.

Incidently Bootcamp will ONLY work if you have a maximum of TWO partitions on the drive. In my case the extra swap partition would render the software useless.

---

