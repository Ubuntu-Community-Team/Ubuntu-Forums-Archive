---
title: "Install ubuntu on PowerPc 8500/120"
date: 2011-01-28
forum: Apple Hardware Users
---

### Post by Isilion on 2011-01-28
Hi all.

A friend of mine give me a old Mac as a present. I want to install ubuntu, or any other linux distro, but i lack completely of experience with Mac's.

The computer boots ok and runs Mac OS X 8. I have a copy already burnt for PPC, but i dunno how to make it boot from CD. I mean, no POST, no "Press F2 to enter setup..." message, etc.

Can someone lend a hand on me?

Thanks in advance.

---

### Post by teh603 on 2011-01-28
I'd suggest looking for one of the guides on installing Linux on a NuBus PowerMac or 68k Mac, although I'd suggest finding a newer computer. One that old won't be much good except as a dedicated server.

First off, the vintage Mac ROM doesn't have a traditional EFI or BIOS, at least as we know it. Thus, a standard bootloader is completely useless. You'll have to compile something from scratch. Second, those computers can only take so much memory if you can even obtain it, and lack the video hardware for most modern graphic frontends like Gnome or KDE. A modern graphics card has more processing power than an 8500. From what I gather, there's also no driver for the SWIM (Super Wozniak Integrated Machine) floppy controller and other device support is spotty at best.

Hate to pop your bubble, because I've got a Performa 5400 that I'd love to find a use for, but them's the breaks.

---

### Post by Isilion on 2011-01-28
Precissely i want to use it as a dedicated server :). I found an ubuntu guide that says that pressing 'C' or 'D', and a debian one that says ''combination of Command, Option, Shift, and Delete keys'' but none works :7


Computer still booting from harddrive. I checked its compatibility and its supported (Power Macintosh 8500/PPC 120). CDROM drive works while Mac OS is loaded.

Is there any kind of Wubi for Mac or anything?

---

### Post by linuxopjemac on 2011-01-29
You have to boot from MacOS and then go into BootX to boot Linux on OldWorld Macs:
[http://mac.linux.be/content/ubuntu-oldworld-macs](http://mac.linux.be/content/ubuntu-oldworld-macs)
[http://mac.linux.be/content/apple-oldworld-computers](http://mac.linux.be/content/apple-oldworld-computers)
[http://mac.linux.be/content/karmic-koala-oldworld-mac-installer-0](http://mac.linux.be/content/karmic-koala-oldworld-mac-installer-0)

I would go for MintPPC on these machines.

---

