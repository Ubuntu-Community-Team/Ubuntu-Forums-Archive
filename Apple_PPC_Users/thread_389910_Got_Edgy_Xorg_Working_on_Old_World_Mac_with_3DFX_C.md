---
title: "Got Edgy Xorg Working on Old World Mac with 3DFX Card"
date: 2007-03-21
forum: Apple PPC Users
---

### Post by jcr13 on 2007-03-21
Whew!  I've been banging my head against this one for days (I've always said that installing Linux is a great way to waste a weekend).  Finally got it working... thought I should share.

Machine:
PowerComputing PowerTower Pro 250Mhz
128 MB Ram
Two SCSI hard drives with lots of different partitions on them
3DFX Voodoo3 2000 graphics card

I've been using Debian Woody on this machine for years.  I don't think I ever got 3DFX acceleration working (though I have seen it work on an X86 machine).  Anyway, as I recall, in accelerated mode, it only has 16-bit color, so that's not something I wanted to use.  Thus, I've been using the card in framebuffer (fbdev driver) mode for years at 1024x768 (if you want to get acceleration working with tdfx on LinuxPPC, good luck!)

I just did a clean install of Edgy on this machine using the hd-media technique (did I mention that I don't have a working CD burner?)

There were a whole host of problems along the way, partly due to known bugs in the hd-media install for Edgy, and partly due to bugs in the default kernel's support for SCSI (after installing and rebooting, the kernel's ramdisk does not tell the kernel to load its SCSI modules, so the kernel cannot find the root filesystem on a scsi drive).  There were also all the usual hurdles involved in getting this stuff working on Old World (like using BootX, and such).

Okay... but I got through all that... and got Ubuntu to boot up.

But then X failed to find any devices.

I re-ran the config for X:     dpkg-reconfigure xserver-xorg

I told it to use the fbdev driver instead of the tdfx driver.  Then I left the PCI address blank.  Both parts seemed to be necessary to get X to launch and find the card.  (How'd I figure this out?  I saved a back-up of my X-config from Woody and looked at the settings in there).

Okay, so I had X working, and GDM, etc...  pretty login prompt, pretty desktop.... but in 640x480 mode.

I re-ran the xorg reconfigure a bunch of times, trying to specify only 1024x768 resolution, but it kept defaulting to 640x480.  No coincidence that this is my terminal resolution on boot-up.  I read somewhere that X will default to this resolution if it can't detect any other usable resolution.  I also read that if you can get your kernel boot-up terminal to be a higher resolution, then X will use that resolution.

I tried passing boot args to the kernel to set a different resolution, but I saw no effect (the kernel boot screen was still 640x480)


Okay...  so I needed the fbset package (which lets you tweak the resolution of a framebuffer from the command line).

apt-get install fbset

For me, it worked with    fbset 1024x768-75

If I called this from one of the virtual terminals (control-option-f2, for example), it would up the resolution of that terminal.  The problem is to get this to happen on the F7 terminal where X will display.  You also need to do it *before* X is running there (tried doing it after X was already running, and got a garbled screen).

I found the part of the rc.d scripts where GDM is launched.   /etc/rc5.d/S13gdm

On the first line, above   set -e    I added the fbset line:
fbset 1024x768-75

At the next boot, I saw the kernel output in its normal 640x480 mode, and then right before launching GDM, I saw the kernel screen jump to a lovely 1024x768.  Then I saw the Ubuntu login screen at the desired resolution.

Ta-da!

Kind of a hack, certainly.  I'm not sure if this is a bug, or a bad fbdev configuration on my part.  Identical x settings for fbdev used to produce 1024x768 in Woody (though as I recall, maybe the boot screen ran at a higher res using Woody's kernel---not sure).   

Certainly, though, the default tdfx configuration (autodetected by the installer) does NOT work, so I guess that counts as a bug.

Anyway, I hope this helps someone out there.

Jason Rohrer

---

