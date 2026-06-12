---
title: "Help with installing Ubuntu onto External HDD (iPod mini)"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by blahdieblah on 2007-09-29
Hi, I tried out Ubuntu a couple of months ago with Wubi and ended up screwing up my MBR and having to reinstall windows. But I've been thinking that I might be able to install it onto my old iPod mini, after seeing   this: [http://ubuntuforums.org/showthread.php?t=226638](http://ubuntuforums.org/showthread.php?t=226638)

I would be using a 7.04 live CD. The only thing is that I'm pretty sure my BIOS doesn't support booting from USB. So I was thinking of using a Super Grub Disk CD, to boot into the iPod. But if you need to reboot after installation, would I be able to switch the live CD to SGD to load the iPod? Or would that be not possible... Or, could I install it, and then just continue to shut down the computer, boot into windows, (just to get the disk drive to pop out) put in SGD and reboot into SGD?

Sorry, that was confusing. I'd really like to get into Ubuntu again, and this seems like a safer way than last time. If this will work, I'd love a response, and if it most definitely will not, I'd like to see if there's a different way. Either way, responses are greatly appreciated!

---

### Post by ryanVickers on 2007-10-03
I think in theory, this should work (install to mini and use grub disk to boot).  Just, ubuntu will be slow running on a USB drive, and you'll need enough room for the OS (maybe 1GB) and then your files (unless your home's on the normal drive(good idea:))).  Also, 1Gb of swap is usually good.  If you've got more than like 2Gb of ram, then 512 or 256 woould also be fine! :)

---

### Post by ofb on 2007-10-03
Well, that sounds like an adventure.

A few questions: Have you indeed checked BIOS to see if there's an option to boot from USB? (If it's not there, then you can be sure, instead of pretty sure. :) )

If you can't boot from USB, then confirm first that SGD actually will do that. (SGB is very versatile, but it's let me down before. It can't boot the third HD, for example.)

But if BIOS or SGD can boot USB, then I think you've talking good sense.

Note the LiveCD usually ejects the CD itself when shutting down for the reboot. And if not, you can usually get the CD to eject using the physical button while BIOS is loading up. You shouldn't have to boot Win just to get the disk out.

Disclaimer: I certainly haven't done what you're attempting.

---

