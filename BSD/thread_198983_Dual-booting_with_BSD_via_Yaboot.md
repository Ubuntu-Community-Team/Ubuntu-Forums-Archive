---
title: "Dual-booting with BSD via Yaboot"
date: 2006-06-18
forum: BSD
---

### Post by BoneKracker on 2006-06-18
How to dual-boot with BSD via Yaboot.

Yaboot doesn't dual-boot with BSD as advertised due to what I think is a simple path concatenation bug in the ybin shell script.  If you want to dual-boot with BSD but don't want to have to boot into OpenFirmware and type a bootline every time, you can do the following.  

I realize there might be like two people who care, but it's still worth documenting where it can be searched for and reused.  I've tested this on OpenBSD and am pretty sure it applies to NetBSD (not sure about FreeBSD).

Edit a line in the OpenFirmware bootloader script that ybin creates in the bootstrap partition.  The script is named "ofboot.b" and the offending line is near the top.  Basically, it erroneously tacks a kernel path (in red) onto the end of the line.

**Before (this is a single line):**
> : bootybsd " Booting BSD..." .printf 100 ms load-base release-load-area " /pci@f2000000/pci-bridge@d/mac-io@7/ata-4@1f000/disk@0:2,\\ofwboot [COLOR="Red"]:,/bsd[/COLOR]" $boot ;

**After:** (shows additional optional changes)
> : bootybsd " Booting BSD..." .printf 100 ms load-base release-load-area " hd:2,ofwboot" $boot ;

The bottom line is that you should replace the text between that second set of quotes with whatever command you can successfully boot with at the OpenFirmware prompt.  For me this was simply "hd:2,ofwboot".

Also, there is a second bug that is only binding if you have "defaultos=bsd" in yaboot.conf.  Toward the bottom of ofboot.b, after the line "drop" is the command referring to whichever bootline is your default (either "bootyaboot" or "bootbsd").  It should read "bootybsd", not "bootbsd".  

Note: Running ybin over-writes any changes, so you may want to make a copy of the fixed ofboot.b in your home directory for reference.

---

### Post by SigmaNunki on 2007-03-14
Well, it looks like I'm one of the two people that care.  I gotta say, you're a life saver!

Thanks :)

---

### Post by BoneKracker on 2007-03-15
I'm pleased someone else was able to make use of it.

One of the Gentoo developers created a patch for ybin that should fix this, but I haven't had the chance to test it.

Until someone patches ybin, you'll have to fix that file any time you run ybin.

---

### Post by kong74 on 2008-04-24
Also thanks for the tip, It works for FreeBSD also, but I had to do some more things, here it is:
First you'll need a copy of the loader (FreeBSDs loader) on the bootstrap-slice, because open firmware can't read ufs. I used finnix live-disto to do that, and some ftp-server because my version of finnix wasn't able to read ufs2; that means i boot to FreeBSD with the bootline in openfirmware, then copy /boot/loader to the ftp-server, then boot to finnix and copy the loader to the boot-partition which already contains yaboot.
BoneKracker replaced "hd:2,ofwboot", hd2 seems to be the boot-partition, and OpenBSDs ofwboot seems already to exist on that partition (either put there somehow during install or afterwards). For me FreeBSD-booting worked with replacing "hd:2,loader hd:4" istead of what BoneKracker replaced, hd:2 is also my boot-partition, FreeBSD and the original loader are in hd:4, change to your needs. The loader on the boot-partition can read ufs2 and therfore load something from hd:4.
If i try to load FreeBSD directly through just copying the loader to the hfs-boot-partition and customizing the boot-command in openfirmware, my FreeBSD boots but I get no vga-console - i don't know why. But this second method can't dual-boot with linux unless you learn how to use loader for that and solve the problem with the vga-console (if it occurs in your mac).

---

### Post by mips on 2008-04-24
[GAG]("http://gag.sourceforge.net/")?

---

### Post by cardinals_fan on 2008-04-24
Ah, thank you for this.

---

