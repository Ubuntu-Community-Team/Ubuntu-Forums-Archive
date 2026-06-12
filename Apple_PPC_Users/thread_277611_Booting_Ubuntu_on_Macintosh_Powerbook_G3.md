---
title: "Booting Ubuntu on Macintosh Powerbook G3"
date: 2006-10-14
forum: Apple PPC Users
---

### Post by jaradronald on 2006-10-14
I'm trying to boot a Mac Powerbook G3 Computer from the CD-ROM.  I can't get the darned thing to give me any boot options...  I've read the documentation on the distro cd and googled the issue, but none of the following are helping:

hold c before boot (post)
use Cmd-Opt-Shtf-Del to start Open Firmware
use Cmd-Opt-o-f to start Open Firmware

Here's my system specs:
G3 Processor
266 Mhz
128 MBs RAM
10 GB Hard Drive
Mac OS 9.2

There is lots of discussion as to "Old World" and "New World" Macs, but I'm not entirely sure what world mine comes from...  :-p

---

### Post by Videobeagle on 2006-10-16
From the specs, you have a Wallstreet powerbook, so Old World, in which case you need a bootloader like BootX to boot to the CD.

I've been ](*,) my head against the wall to get it to load to a live CD, but no luck (but getting to the install menu is no problem).

---

### Post by taurus on 2006-10-16
Gonna move this post over to the Mac section...

---

### Post by jaradronald on 2006-10-16
RE: Videobeagle - booting live CD

I'm using bootX now to run Ubuntu 6.06 from the hard drive, and I was playing around with running the live version from CD...  I think if I knew the correct "root=/dev/???" parameter for the "Live CD" I could pass that along using the kernel arguments in bootX...  Does anybody know where the root system is (how it is referenced) when booting the live version of 6.06 for PPC?  I would assume it's somewhere on /dev/cdrom or /dev/hdc but I'm not sure...

---

### Post by jaradronald on 2006-10-16
RE: Videobeagle - booting live CD

I'm using bootX now to run Ubuntu 6.06 from the hard drive, and I was playing around with running the live version from CD (that is, booting the vmlinux and initrd.gz from the hard drive, but making the root filesystem load (rw) from the cd-rom)...  I think if I knew the correct "root=/dev/???" parameter for the "Live CD" I could pass that along using the kernel arguments in bootX...  Does anybody know where the root system is (how it is referenced) when booting the live version of 6.06 for PPC?  I would assume it's somewhere on /dev/cdrom or /dev/hdc but I'm not sure...

---

### Post by Windows_Apple_Linux on 2006-12-04
Well, I also need help with that, but what is bootX and what do i have to do in order to run linux on powerbook g3

---

