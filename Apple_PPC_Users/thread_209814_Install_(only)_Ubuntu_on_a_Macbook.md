---
title: "Install (only) Ubuntu on a Macbook"
date: 2006-07-05
forum: Apple PPC Users
---

### Post by el toro on 2006-07-05
So, I've been scouring the intarwebs, these forums, etc. for the answer to my question...is it currently possible to install ONLY Ubuntu on a Macbook (no hfs/OS X partition)?  Everything I've read seems to indicate that it's not currently possible due to EFI vagaries, but what is unclear to me is exactly *why*.  So, if anyone with some expertise can answer my question, I'd appreciate it.

---

### Post by amitofu on 2006-07-05
The problem is that Apple's EFI implementation only supports hfs+ filesystems, although [not for long]("http://sourceforge.net/mailarchive/forum.php?thread_id=16105978&forum_id=47882").

I have only Ubuntu installed on my MacBook, but I have a small hfs+ filesystem at the beginning of my disk that holds elilo. In order to install or update elilo, however, I have to boot from the Mac OS X restore cd and copy elilo from a usb flash drive and enable it. So you can be OS X free on your hard drive, but you still need an OS X cd to update the boot manager. This will hopefully change with the EFI implementation of ext2. Then all we need is a Linux version of the bless command.

---

### Post by chasisaac on 2006-07-06
[QUOTE=el toro]So, I've been scouring the intarwebs, these forums, etc. for the answer to my question...is it currently possible to install ONLY Ubuntu on a Macbook (no hfs/OS X partition)?  Everything I've read seems to indicate that it's not currently possible due to EFI vagaries, but what is unclear to me is exactly *why*.  So, if anyone with some expertise can answer my question, I'd appreciate it.[/QUOTE]

I know one person suggested to leave a basic Macintosh OSX partition on for updates such as firmware. OF corurse you can that via a firewire drive

---

