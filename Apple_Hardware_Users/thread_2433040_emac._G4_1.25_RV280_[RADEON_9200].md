---
title: "emac. G4 1.25 RV280 [RADEON 9200]"
date: 2019-12-12
forum: Apple Hardware Users
---

### Post by tiwmid on 2019-12-12
I am using nomodeset for any interaction with live or installed linux systems.
I have tried everything I thought was relevant to my hardware on the ubuntu and debian powerpc wikis.
KERNEL: 4.4.0-142-powerpc-smp ppc (32-bit GCC:5.4.0)
DESKTOP: Razor-Qt (Openbox 3.6.1)
DISTRO: Ubuntu 16.04 xenial
CARD: AMD/ATI RV280 [RADEON 9200]
DISPLAY SERVER: X.0rg 1.18.4 DRIVER:fbdev
RESOLUTION: 1024x768@116.00 (this resolution is not what I want but it does work).
GLXRENDERER: N/A GLX VERSION:N/A DIRECT RENDERING: N/A
glxinfo=Error: couldn't find RGB GLX visual or fbconfig
xrandr= Failed to get size of gamma for output default (resolution is same as above)

I had everything working as desired but I was worried ubuntu 16.04 was my last chance to update so I have reinstalled several versions of linux.
 I cannot configure a working GUI Display.
What I have now is readable for the most part. (But something like synaptic is just blank).
I would be grateful if someone could tell me in broad strokes how to proceed.
For example do I need non-free linux firmware or drivers for RADEON 9200? 
Do I need xorg.conf file?
Thank you in advance for any help.

---

### Post by gsahli on 2019-12-15
I had that problem, too. Can't test my result for you, but here's my yaboot.conf:

```

## For a dual-boot menu, add one or more of:
## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hdaZ

boot="/dev/disk/by-id/ata-ST3250823A_3ND27RB2-part9"
device=/pci@f2000000/mac-io@17/ata-4@1f000/@0
partition=3
root="UUID=3c9aa558-2a47-42bb-8a91-f0fedd29902c"
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macos="/dev/disk/by-id/ata-ST3250823A_3ND27RB2-part10"
macosx="/dev/disk/by-id/ata-WDC_WD1200JB-00GVA0_WD-WCALA1568821-part10"

image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="quiet splash radeon.agpmode=-1 modprobe.blacklist=ams"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="quiet splash"
```

(notice the linux command parameters: "quiet splash radeon.agpmode=-1 modprobe.blacklist=ams")

And here's the "required" /etc/X11/xorg.conf (to get right driver):

```
Section "Device"
	Identifier "Radeon"
	Driver "radeon"
EndSection
```

My card is the 9600XT, newer than yours. See this for radeon driver limitations with the 9200:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by tiwmid on 2019-12-16
Thanks for this gshali, I was just flailing without purpose.
I will work on my xorg.conf and yaboot.conf when I get home tonight.

---

### Post by tiwmid on 2019-12-17
The yaboot.conf and xorg.conf aren't working for me. I just boot to a black screen with no tty.
I am starting to think the xorg.conf is not being used.  /etc/X11/xorg.conf.
This time I had xorg create my configuration and then edited that. But I have tried other xorg.conf
files without success.

---

### Post by gsahli on 2019-12-17
After changing the yaboot.conf, did you run ybin -v to install the changes?

---

### Post by tiwmid on 2019-12-18
Yes I did. This has been my experience. No matter what I do, boot parameters, xorg.conf changes, drivers. I am always running headless without nomodeset.
My strategy has been install base system, install small WM or DE, install slim login manager,install mesa-utils. And try to configure things from there.
I have not been able to use a live disc installer. I can only use the n-curses installer.
Maybe this is part of the problem. I am not installing everything on the DVD or CD.

---

### Post by gsahli on 2019-12-20
If you get to the boot prompt, can you try this command:
Linux quiet splash radeon.agpmode=-1 modprobe.blacklist=ams

---

### Post by tiwmid on 2019-12-20
Thank you again for your help but this does not work for me.
[https://wiki.debian.org/PowerPC/FAQ#How_do_I_get_graphics_working.3F](https://wiki.debian.org/PowerPC/FAQ#How_do_I_get_graphics_working.3F)
This seems to be promising but importantly it does not work for me. And I am unable to generate an xorg.config without errors.
This approach is effective but Open Firmware does not hand off the display to linux. Or at least I don't know what to do at a static Open Firmware window.
> Several 14" G3 iBook and eMac users have reported blank screens with Radeon/KMS. The only workaround is to disable KMS, load the old Radeon framebuffer, and use the unaccelerated fbdev driver. To first disable KMS and get a semi-working screen, you must boot with the Yaboot parameter Linux nomodeset.
You should arrive at a login screen with psychedelic colors, so it's advisable to switch to a console to further change settings enabling the Radeon framebuffer and fbdev driver. First, remove the radeonfb blacklisting in /etc/modprobe.d/fbdev-blacklist.conf (deleting the radeonfb line or commenting it out), and then add radeonfb to /etc/modules. Finally, disable both KMS and the Open Firmware framebuffer by rebooting with the parameters Linux nomodeset video=[noparse]offb:off[/noparse] (see the yaboot.conf example above for how to make these parameters permanent).

---

### Post by tiwmid on 2019-12-20
[https://lists.ubuntu.com/archives/kernel-team/2012-March/018805.html](https://lists.ubuntu.com/archives/kernel-team/2012-March/018805.html)
This outlines the only an approach that works for some.
I have not been able to pull it off yet but I have been told by others who know that I need an EDID.bin file specific to my monitor
in order to have x display correctly.

---

### Post by tiwmid on 2020-04-08
I am overjoyed that I found this post on Facebook by Jay Hubbard.
All of the credit goes to him for the simple, useful solution to install Ubuntu 16.04 with a working DE, and GUI interfaces on a eMac G4, 1.25.
It is trivial to install linux, OpenBSD, FreeBSD on this device but difficult  to use the CRT display.
[URL="https://m.facebook.com/notes/linux-on-powerpc-macs/this-guide-is-for-emac-users-to-end-up-with-ubuntu-1604-a-custon-44-kernel-due-t/"]https://m.facebook.com/notes/linux-on-powerpc-macs/this-guide-is-for-emac-users-to-end-up-with-ubuntu-1604-a-custon-44-kernel-due-t/

[/URL]I am posting this just so others can find the facebook page, it took me forever to see this . (I don't use facebook.)
Also there are so many posts that dismiss Ubuntu for ppc as a bloated dog that won't run on weak hardware.
That has not been my experience, Ubuntu was the only version of linux that always gave me a GUI. (Problem was it was unusable.)
I have used linux for years on my eMac and when I tried to upgrade to Ubuntu 16.04 on my own I never succeeded.
Jay Hubbard's Facebook post worked for me.

---

### Post by tiwmid on 2020-04-08
[https://imgur.com/a/xIXuUZ1](https://imgur.com/a/xIXuUZ1)

---

### Post by ernsteiswuerfel on 2020-06-21
[INDENT]If you want a much more painfree experience with Linux on G3/G4/G5 hardware just skip this outdated distro and use another one. Also G3/G4/G5 PPC is no longer supported by Ubuntu.

These are (better) alternatives with bootable isos, current software (working browser, etc.) and current kernels:
[https://voidlinux-ppc.org/](https://voidlinux-ppc.org/)
[https://www.adelielinux.org/](https://www.adelielinux.org/)
[https://fienixppc.blogspot.com/p/download.html](https://fienixppc.blogspot.com/p/download.html) (64bit only, USB boot image)

Also no need to fiddle around with yaboot any longer. Void and Adelie use grub just like you know it from Linux on regular x64_64 hardware.[/INDENT]

---

