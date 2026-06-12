---
title: "External CD burner not detected"
date: 2005-11-08
forum: Absolute Beginner Talk
---

### Post by editrix on 2005-11-08
I have a Backpack external CD re-writer, connected to the printer port, which isn't showing up in Konqueror under/media, or anyplace else I can think to look for it (e.g. Partitions in KInfocentre).

So, naturally, I can't back up anything in K3B,

According to the manufacturer's wesite:
[http://www.micro-solutions.com/downloads/linux/index.asp](http://www.micro-solutions.com/downloads/linux/index.asp)
> 
The backpack parallel port driver has been included into the Linux Kernel 2.4.4 and higher. No special software downloads should be needed from this page. We recommend that you use the newest kernel version.

If you are looking for boot disks to work for installing your particular Linux distribution from a backpack, please consult the maker of said distribution.

Please note that there are 2 backpack drivers in the Linux kernel:

bpck6.o - works with all current backpack CD-ROM, cd-rewriter, and hard drive models, which typically have a "Series 6 driver" notation on the Serial Number label on the bottom of the backpack drive.

bpck.o - works with earlier models of backpack CD-ROM (Models 163xxx, 164xxx, 165xxx), hard drives (850MB to 6.4GB), and original 2x cd-rewriters (Models 190100 and 190120).

I'm sure the above is very informative to those who understand it, but I don't.

Please help!

---

### Post by mlomker on 2005-11-10
You can try loading the driver from a prompt:

```

sudo modprobe bpck6

```

**dmesg | tail** should provide some information about the driver being loaded.

---

### Post by editrix on 2005-11-11
[QUOTE=mlomker]You can try loading the driver from a prompt:

```

sudo modprobe bpck6

```

**dmesg | tail** should provide some information about the driver being loaded.[/QUOTE]

Thanks for this. What I got was:

```

Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
CSLIP: code copyright 1989 Regents of the University of California
PPP generic driver version 2.4.2
PPP BSD Compression module registered
PPP Deflate Compression module registered
PPP: VJ decompression error
bpck6: BACKPACK Protocol Driver V2.0.2
bpck6: Copyright 2001 by Micro Solutions, Inc., DeKalb IL. USA
paride: bpck6 registered as protocol 0
```

So it looks like it's there, but I put a CD in the burner, I didn't see anything in Konqueror. What I do have is:

/media
cdrom  cdrom0  floppy0  windows

cdrom is a link to cdrom0, my internal CD reader.

---

### Post by mlomker on 2005-11-11
Perhaps you could ask the author of [this thread.]("http://ubuntuforums.org/showthread.php?t=77900")

---

