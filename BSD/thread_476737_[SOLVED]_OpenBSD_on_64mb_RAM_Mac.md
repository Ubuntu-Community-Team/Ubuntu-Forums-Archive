---
title: "[SOLVED] OpenBSD on 64mb RAM Mac?"
date: 2007-06-17
forum: BSD
---

### Post by waggygee on 2007-06-17
I have a truely chronologically accomplished Mac it should be about 9years old or something, I lost count. I was looking for a way to get it running again but it has only 64mb RAM and a 20gb hard drive. I thought I could run Linux puppy but I was told it wouldnt work because its a power pc or something and someone suggested I try OpenBSD3.7 I could find minimum system requirements or anything so is there anyone who knows if my computer would handle it? If there anymore specs you would like to know please dont hesitate to ask!

---

### Post by Bachstelze on 2007-06-17
OBSD 3.7 ? The current release is 4.1, dude :)

Anyway, I've successfully ran it on machines much lower than that, so you will have no problem.

---

### Post by mips on 2007-06-18
Install OBSD followed by fluxbox. Should be fine as OBSD basically has no bloat and it's a pretty good performer even on older hardware.

---

### Post by waggygee on 2007-06-30
ok.... I went to softpedia.org to download Open BSD4.1 (macppc version) but I want given simple ISOs to download.... like which things do I have to get? Or is there a simpler "one click" download link to get it?

---

### Post by mips on 2007-07-01
What model Mac do you have ? Reason I ask is that there are some unsupported models, [http://www.openbsd.org/macppc.html#unsup](http://www.openbsd.org/macppc.html#unsup)
Also check to see unsopported hardware.

There is no freely available OBSD cd as you have to pay for it. There is however a mini cd available through which you can do a Net install (dunno what internet connection you have). You could also download all the files and make your own bootable cd. The there are torrents but I'm not to trusting of them as you have no idea about their source.

[ftp://ftp.mirrorservice.org/pub/OpenBSD/4.1/macppc](ftp://ftp.mirrorservice.org/pub/OpenBSD/4.1/macppc)
[http://www.mirrorservice.org/sites/ftp.openbsd.org/pub/OpenBSD/4.1/macppc/](http://www.mirrorservice.org/sites/ftp.openbsd.org/pub/OpenBSD/4.1/macppc/)

Another option could be NetBSD or FreeBSD & maybe Darwin.  You could also try linux distros like mklinux, gentoo etc

---

### Post by waggygee on 2007-07-01
> **mips said:**
> What model Mac do you have ? Reason I ask is that there are some unsupported models, [http://www.openbsd.org/macppc.html#unsup](http://www.openbsd.org/macppc.html#unsup)
Also check to see unsopported hardware.

Another option could be NetBSD or FreeBSD & maybe Darwin.  You could also try linux distros like mklinux, gentoo etc

I think it is supported. My computer is a realy old G4, 32bit, 64mb RAM, PCI graphics, 400MHz microprocessor speed....... What else may be  important? I had a brief look at the other distros metioned, would they work with my tiny amount of RAM? I couldnt find any minimum system requirements

I have tried YellowDog 4.1 Sagitta,  installation goes well and I completes as expected but when I reboot I get a grey screen saying I should type 'mac-boot' or 'shut-down'....... I have tried Open BSD but I find it complicated to install and I can only find instalation instructions/guides for Open BSDs other than Macppc version.........

---

### Post by waggygee on 2007-07-03
ok, I just managed to install OpenBSD4.1. but when I reboot, the Openfirmware comes on. so I type in the command "boot hd :,ofwboot/bsd' (it said this command should work after installing) but it didn't so I tried altering it a bit and wrote "boot i:,ofwboot/bsd", after this I receive this:

can't OPEN:/pci@80000000/pci-bridge@d/pci-ata@1/@0/disk@0:2,\\:tbxi

if I type "i" click return then "boot" it appears to have frozen.

---

### Post by waggygee on 2007-08-02
It apears that yaboot did not install.... Anyway, I installed Ubuntu Feisty Fawn with IceWM... Thanx everyone!

---

