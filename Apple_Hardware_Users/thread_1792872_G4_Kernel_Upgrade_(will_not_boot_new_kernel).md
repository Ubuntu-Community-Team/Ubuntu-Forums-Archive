---
title: "G4 Kernel Upgrade (will not boot new kernel)"
date: 2011-06-28
forum: Apple Hardware Users
---

### Post by svtguy88 on 2011-06-28
Alright,
I'm trying to get my G4 off of OS X for its primary OS.  I have a working Debian install on a 40 GB IDE drive (kernel is custom 2.6.26).  I am trying to update the kernel to 2.6.39.1, but I cannot get the new kernel to boot.

I'm sure I should post this elsewhere, but I've had good luck here with fellow PPC Mac users before.

Anyway, when I point yaboot to my new kernel, it prints out about two lines (the usual "Elf32...." blah blah blah), then flashes to a white screen that looks like open firmware.  The only thing this screen says is:

```

done
found display     : /pci@f000000/NVDA,Parent@10/NVDA,Display-A@0, opening... 
```

And that's it.  System hangs from there...

I'm not sure what to make of it.  I feel like the nvidiafb should take over, and I've got it compiled in the kernel as a module (just like the working 2.6.26 kernel on this machine), but nothing happens.  I've never seen the white open firmware screen outside of..well, open firmware.

I can post any files necessary...until then I'll just keep fiddling with the kernel configuration, rebuilding and trying it out.

---

### Post by linuxopjemac on 2011-06-29
chroot into your sytem and check the symbolic links in /boot
and check them against yaboot.conf. Also don't forget to issue a ybin -v whenever you change the yaboot.conf file. Make sure your open firmware path to your device is correct as well.

[http://mac.linux.be/content/yaboot](http://mac.linux.be/content/yaboot)

---

### Post by svtguy88 on 2011-06-29
I issued ybin -v when I first built the kernel and put it in /boot.  Each time I rebuild though, I've been renaming it to the same thing, so yaboot doesn't really need to be updated, right?

As for the open firmware path, the hard drive will boot using the old (2.6.26) kernel, so I assume everything is fine with the OF path.

What do you mean by checking the sym links?

---

### Post by linuxopjemac on 2011-06-29
the entries you have should link to the right kernel, so vmlinux should be linked to your new kernel image if that is the default one for example, I hope you understand what I mean.

---

### Post by svtguy88 on 2011-06-29
I used the method described [here]("http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html") for compiling/installing the kernel.  I've never gotten the "make install" command to work for me, so I just copied vmlinux and initrd (appended with version info to differentiate from the other vmlinux/initrd) over to /boot and then I added an entry in yaboot.conf that points to them.

Is there more I have to do?  I don't remember doing anything with links last time around (this is the first time booting this machine to linux in over a year...I'm a bit rusty).

---

### Post by linuxopjemac on 2011-06-30
It looks like you did the right thing.

---

### Post by svtguy88 on 2011-07-11
Hmm...new problem.

I downloaded the latest mainline (3.0-rc6) kernel, and tried building form that.  I compiled with only the VESA framebuffer, and am now able to get further than the odd openfirmware-ish screen that I had before.

However, the system still does not boot.  Everything is kosher on bootup until the system tries to start loading modules.  I start seeing errors like this:  

```
FATAL:  Could not open /lib/modules/3.0.0-rc6/modules.dep:  No shuch file or directory
```

Before these errors appear (there are several - the system appears to continue to attempt to load while this error just reoccurs), I can see /dev/hda3 recognized as my boot partition (which is correct).  It then says:

```
Begin:  Waiting for root files system
```

However, after this appears, the system throws some USB messages, and then the "fatal" error described above is shown a few times after it says "Gave up waiting for root device."

Finally, I'm left with:

```
ALERT! /dev/hda3 does not exist.  Dropping to a shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty: job control turned off
(initramfs)_
```


The final underscore blinks, and the system halts right there.  I'm lost.  If I boot the kernel that has been working the whole time (a custom 2.6.26-2 build), everything is fine, but trying to boot this kernel (custom 3.0-rc6) causes havoc.  I don't get it:  /dev/hda3 is recognized by the new kernel (or appears to be when I try to boot it), but I get those crazy FATAL errors saying that it can't load the modules.  

For what it's worth, the modules for the Mac-IO (Powermac/Powerbook IDE bus) are compiled into the kernel, and the general PATA drivers are modularized.  I believe the working (2.6.26-2) kernel is setup the same way...

---

### Post by linuxopjemac on 2011-07-12
I would ask help here:
[http://forums.debian.net/viewforum.php?f=5&sid=f9d4d311f4d710e1d9c7759281006888](http://forums.debian.net/viewforum.php?f=5&sid=f9d4d311f4d710e1d9c7759281006888)

---

### Post by rsavage on 2011-07-12
I would run the ybin command.  There is something magical/mystical about it, so it may just work.  Whenever I've played around with kernels (not much, I was trying to get KMS to work) I've always added a new stanza and run ybin.
 
If it not your kernel setup, then it could easily be your yaboot.conf.  When I installed lubuntu maverick my debian partition stopped working (it dumped me into busybox with errors indicating that it couldn't find root), but the ubuntu ones were fine.  The only thing that had changed was the yaboot.conf and I still haven't figured out why (it is on my list of things to look into).  The only major difference was how the bootstrap was addressed in the path, athough they pointed to the same partition.  Have got it working now using an old yaboot.conf as the basis and adding new stanzas for debian and my recent lubuntus.
 
What I would do is find a more recent non-custom kernel and see if that boots.  You can then have a look at its setup.  Out of curiosity, why do you need a custom kernel?  Is it for speed and if so, what improvements are you getting?

---

### Post by rsavage on 2011-07-12
Ignore what I was saying about the boostrap/device path. That was a red herring like I thought. I've found the offending bit of the yaboot.conf.
 
For me I needed to change the append line:
 
```
image=/pci@f4000000/ata-6@d/disk@0:5,/boot/vmlinux
    label=hda5-Linux
    root=/pci@f4000000/ata-6@d/disk@0:5
    append="root=UUID ro"
    initrd=/pci@f4000000/ata-6@d/disk@0:5,/boot/initrd.img

```to 
 
```
image=/pci@f4000000/ata-6@d/disk@0:5,/boot/vmlinux
    label=hda5-Linux
    root=/pci@f4000000/ata-6@d/disk@0:5
    append="root=/dev/hda5 ro"
    initrd=/pci@f4000000/ata-6@d/disk@0:5,/boot/initrd.img

```It also works if you do something like this (and is how I'm set up at the moment):
 
```
image=/pci@f4000000/ata-6@d/disk@0:5,/boot/vmlinux
    label=Debian-Linux
    root="UUID=b1g-10ng-number-1000"
    append=" ro"
    initrd=/pci@f4000000/ata-6@d/disk@0:5,/boot/initrd.img

```It maybe worth checking it is not something like this.
 
EDIT: Looking at this a few months later that middle suggestion probably could be simplified to:
 
```
image=/pci@f4000000/ata-6@d/disk@0:5,/boot/vmlinux
    label=hda5-Linux
    root=/dev/hda5
    append=" ro"
    initrd=/pci@f4000000/ata-6@d/disk@0:5,/boot/initrd.img

```It would be interesting to know if this works too:
 
```
image=/pci@f4000000/ata-6@d/disk@0:5,/boot/vmlinux
     label=hda5-Linux
     root=/pci@f4000000/ata-6@d/disk@0:5
     append=" ro"
     initrd=/pci@f4000000/ata-6@d/disk@0:5,/boot/initrd.img
 
```
 
Or this
 
```
image=hd:5,/boot/vmlinux
label=hda5-Linux
root=hd:5
append=" ro"
initrd=hd:5,/boot/initrd.img

```
 
So many ways!

---

### Post by svtguy88 on 2011-07-12
I'll try reorganizing my yaboot.conf a bit tomorrow, but I don't think it's that, as I get the same results if I manually boot my kernel image from either Open Firmware or the yaboot prompt (the whole device path, not just the yaboot label).

As for why I'm using a custom kernel...my final goal is to be able to boot linux off of the SATA drive inside my Powermac G4.  However, this SATA drive runs off of an Acard PCI SATA controller, which your run of the mill kernel has problems with.

---

### Post by svtguy88 on 2011-07-27
I changed the status to solved, as I think my errors a result of simply not choosing appropriate options for my kernel.

I downloaded a newer Debain netinstall disc, and it was able to install and boot my SATA drive.  I did have to trick yaboot a little though - the install disc sees my drive as /dev/sdb, but the actual install recognizes my drive as /dev/hdi.  This just means I had to play with the "boot=" and "root=" parts of yaboot.conf a little, but I've got it mostly sorted out.

Unfortunately, multiple processors are disable by default, so I"m back to trying to build a new kernel - but at least I have the SATA drive booting...I can finally ditch the old IDE.

---

