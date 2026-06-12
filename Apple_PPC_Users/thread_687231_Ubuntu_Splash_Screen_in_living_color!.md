---
title: "Ubuntu Splash Screen in living color!"
date: 2008-02-04
forum: Apple PPC Users
---

### Post by stream303 on 2008-02-04
Never thought I'd live to see this:  A** full-color, non-distorted startup and shutdown splash screen** on PPC. :)

I just applied the techniques by Eric Work from the following bug report on my 20" G5 iMac running an Nvidia card and lo and behold - it works!

[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/21478](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/21478)

Video seems a tad slower, although I did get a very small boost by adding my own kernel parameter in addition to the ones they discuss:  **fb=false**

Since this is a general-purpose desktop machine, I'm not so concerned about absolute video speed, and think I'll just enjoy the splash for awhile.

We're dealing with yaboot and other critical files, so be careful when editing!

---

### Post by BladeMelbourne on 2008-02-04
I haven't seen that before on PPC - methinks urban legend!

I tell myself that real men append "nosplash video=ofonly" so I don't ever need to see the splash screen ;-)

---

### Post by stream303 on 2008-02-04
That's what I thought until I did this:

```

1. Edited /etc/yaboot.conf
changed append to, "video=offb:off video=nvidiafb quiet splash"
2. Ran 'sudo ybin -v'
3. Edited /etc/initramfs-tools/modules
added the new line, "nvidiafb noaccel=1"
4. Edited /etc/modprobe.d/blacklist-framebuffer
commented out, "blacklist nvidiafb"
5. Ran 'sudo dpkg-reconfigure linux-image-`uname -r`'
6. Rebooted

This is for a 1.33 GHz 12" Powerbook G4 with an Nvidia GeForce Go5200. With these changes I can now also use the framebuffer for mac-on-linux and still have brightness controls. Of course uplash is also now shown correctly which is what brought me to this bug initially. The key changes were adding noaccel when loading the nvidiafb module and putting the nvidiafb module into initramfs.
```

Works great on my 20" G5 iMac after a brief white screen flash.

It also fixed a very slight problem that when I used to get into the first virtual terminal aka CTRL-ALT-F1, I would see the last few lines of the startup stanza and had to hit return once to get to the login prompt.

On my 12" G4 late 2004 iBook, removing video=ofonly cured my lack of virtual terminals altogether, and got brightness working.  Sold the iBook recently so I can't test this.  Picked up an HP tx1400us Tablet pc which has it's own unique kernel parameters to get stable. :)

**Update:**
As per the powerpc faq I tried something that I thought only applied to ATI cards, but I seem to have my original video speed back.  Now with the above completed, I added this option to the device section in my /etc/X11/xorg.conf file:

```
Option   "UseFBDev" "false"
```

wow.

Here are the relevant portions of my yaboot.conf and xorg.conf for reference:
**yaboot.conf:**

```
image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
        append="video=offb:off video=nvidiafb quiet splash fb=false"

```

and **xorg.conf** device section:

```
Section "Device"
	Identifier	"nVidia Corporation NV34M [GeForce FX Go5200]"
	Driver		"nv"
	BusID		"PCI:240:16:0"
	Option		"FPDither" "true"
	Option		"UseFBDev" "false"
EndSection
```

---

### Post by casbahdk on 2008-02-15
Will this work with a G5 single, an nVIDIA GeForce FX 5200 and a Samsung SyncMaster 930BF flatscreen monitor? I don't want to screw anything up just to get a splash screen.

---

### Post by stream303 on 2008-02-15
While it was pretty while it lasted, I'd say that unless you absolutely need to have a nice splash, maybe forget about it. :)

You just caught me after a two hour ordeal of getting my original yaboot working again after I lost it carelessly doing a server install onto a firewire drive.  The good news is that both are working now.  Btw, the ubuntu forums as seen in text-based elinks browser leaves something to be desired. :)

---

### Post by casbahdk on 2008-02-15
I feel your pain. I don't think I could have recovered from that . Thanks for the info.

---

