---
title: "A Few Issues"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by Valency on 2007-10-11
Hey everyone :)

I've used Windows for as long as I can remember, but Vista's been giving me the shits, so I thought I might give ol' Ubuntu a try.

Right now, I'm using Ubuntu from the live CD, so I haven't actually installed it yet. However, from the live CD I've encountered a number of issues that hopefully, someone can help me with. :)

Bit of information first:

I'm running the Gutsy Gibbon RC at the moment, but the problems were apparent with the Feisty Fawn too.
AMD64 X2 AM2 3800+
nVidia 7600 GT
2GB DDR2 RAM

Upon booting from the live CD, when Ubuntu started up, everything on my display was all *jumbly*.. which is probably the best way to describe it. It looked like some form of graphics card issue (I'm using an nVidia 7600 GT). While the display was all jumbly, I was unable to do anything with any input, neither mouse nor keyboard. However, I did hear a *jungley* sound when it first booted, which is probably indicative that it did successfully load, just something's gone a bit screwy with the graphics side.

I restarted and went into 'Safe Graphics Mode', which is working fine as far as I can tell. 

There are some programs I'll still need that only run on Windows based machines, so I'll hopefully be dual booting, using Ubuntu as my primary OS, and only going to Windows when I absolutely need it.

Windows is installed on a small IDE drive (I'm livin' in the past). All my other media and files are installed on a 300GB SATA, which, from the looks of things, I can't access using Ubuntu. I'm guessing that this might be because it's formatted in some weirdo windows way (NTFS?), and I was curious as to what I could do to have both operating systems having the ability to access this HDD.

I plan on partitioning the Windows drive and sticking Ubuntu there with it, but I'm unsure as to whether this might cause any issues.

Will installing Ubuntu - rather than running it from the live CD - fix any of the issues I'm having?

Thanks for reading it (if you could be bothered), and thanks in advance.

- Moe

---

### Post by defrex on 2007-10-11
Your right about your issue probably being a graphics card one. I'm not sure what to suggest, but perhaps someone else will. 

As to the hard drives. The installer will set up a dual-boot for you pretty easily. You can either edit the partitions yourself (only if you know how, as it can be dangerous) or just let the install do it for you automatically. Either way it'll detect Windows and add it to Grub, the boot-loader.

And for NTFS support (which works quite well) you'll just need to install a package called ntfs-config. That's as simple as running *sudo apt-get install ntfs-config* from the command line or, if you prefer, searching for it and installing it using Synaptic. That's found under the administration menu. Then go to System Tools>NTFS Configuration Tool, and turning it on.

---

### Post by borris.morris on 2007-10-11
using feisty and/or gusty you can read and write to ntfs partitions quite easily. also, installing ubuntu wont necisarraly fix your video card problems. but, because its nvidia, i would say go for it. if it doesnt, its a very easy thing to install. (drivers that is.)

---

### Post by Valency on 2007-10-12
Thanks for that guys. I think perhaps installing Ubuntu and then getting the drivers for the graphics card might be able to solve the graphics issue.

I had a bit of a poke around in the system panel and had a gander at the display options, and it seems more than capable for supporting dual screens (which is what I'll be using), which is excellent.

Another question, rather than installing the Gutsy Gibbon Release Candidate, would it be wise to wait the 6 days to get the final release? Or is the upgrade quick and easy, so I could be able to install it now with no issues when I want to upgrade in a few days time?

---

### Post by Valency on 2007-10-12
I hate to do this.. but:

Bump.

---

### Post by Valency on 2007-10-12
Bump again..

Sorry :S

---

### Post by UbuntuniX on 2007-10-12
I'm using that graphics card, with no problems whatsoever. You probably just need to change driver.

---

