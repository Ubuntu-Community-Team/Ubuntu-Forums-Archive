---
title: "Installation Hangs on a Black Screen"
date: 2010-08-20
forum: Apple Hardware Users
---

### Post by flatman on 2010-08-20
Hi everyone!

I'm totally new to Linux and Ubuntu, but I've already hit a dead end. I'm trying to install Ubuntu on an iMac G4, and I had a promising situation the first time through but I botched the install due to my newbishness and haven't been able to boot from the install CD since.

Here's the situation:

**Hardware**
800 Mhz G4
256 MB RAM
15" LCD display
32 MB GeForce2 MX Video Card
"Standard" Airport Wireless Card
(more details [here](http://www.everymac.com/systems/apple/imac/stats/imac_800_fp.html))

**What Happened**
After poking around on the forums some and reading through some of the wiki pages, I decided that 8.04 would be a good place to start, so I downloaded and burned an install disc. My first attempt booted almost perfectly, but I confused the "booting from the CD" with "installed Ubuntu" (Iknow, I know...), and promptly rebooted back into OS X.

Since then, I've been unable to successfully boot from the CD. Using the 8.04 disc, I'm prompted for what style of install I'd like, and I feebly type "live," the ramdisk loads, and then the screen goes blank, reads "loading" in the upper left for a second, the optical drive whirs for a bit, and then everything hangs on a black screen with a white cursor in the upper left. I thought I might just be impatient, so I let it sit overnight, but there was no change in the situation.

I know this isn't much information to work with. Is there a way to enable a more robust boot description? Something that will let me know what's going on when the screen goes blank and the optical drive whirs? It seems to hang in the same place, so knowing what's going on at that moment might be helpful.

Either way, any help would be greatly appreciated. Thanks in advance!

---

### Post by avtolle on 2010-08-20
While ubuntu will run (slowly) with 256mb RAM using Gnome, 384mb RAM is the minimum required(?) to install via the Live CD. This is due to the graphic installer. You could try installing from the alternate install iso (same result, just the installer doesn't use the graphical interface); try Xubuntu (for 8.04, the "Live" (Desktop) CD will work with, IIRC, 192 mb RAM); using the alternate iso, do a command line install, adding a lightweight desktop environment such as LXDE after installation. These are some of the options available to you. There is also Debian you might want to consider.

Unfortunately, like Mr. Natural, I'm "just passing through", and can't stay around to offer more assistance today. Hopefully, others will see your post, and give their suggestions/assistance. Good luck.

---

### Post by shawnhcorey on 2010-08-20
Did you burn the CD on your iMac?  Sometimes older CD drives loose their alignment and don't burn properly even though they can still read CDs.  I have a PowerBook G4 and its CD drive is completely flaky.  Sometimes it won't even read a disk.  I have moved to USB drives for backup and installs.

---

### Post by flatman on 2010-08-20
> **avtolle said:**
> While ubuntu will run (slowly) with 256mb RAM using Gnome, 384mb RAM is the minimum required(?) to install via the Live CD. This is due to the graphic installer. You could try installing from the alternate install iso (same result, just the installer doesn't use the graphical interface); try Xubuntu (for 8.04, the "Live" (Desktop) CD will work with, IIRC, 192 mb RAM); using the alternate iso, do a command line install, adding a lightweight desktop environment such as LXDE after installation. These are some of the options available to you. There is also Debian you might want to consider.

Cool, I'll look into this and see how it goes.

[QUOTE= shawnhcorey]Did you burn the CD on your iMac? Sometimes older CD drives loose their alignment and don't burn properly even though they can still read CDs. I have a PowerBook G4 and its CD drive is completely flaky. Sometimes it won't even read a disk. I have moved to USB drives for backup and installs.
[/QUOTE]

I don't think there was an error burning the CD, as it booted just fine (if a little slowly) the first time around. I don't think the CD would have degraded in a matter of hours.

---

### Post by flatman on 2010-08-20
Well, I'm not sure how or why, or if it was a fluke, but it seems that I've found a solution. Rather than holding down 'C' during boot, I held down 'Option' and selected the CD manually. Oddly, the initial screen was white instead of the usual black, but I was able to install successfully.

I'm not sure if this counts as a solution or not, but I'll mark the thread as Solved anyway.

Thanks for the help!

---

