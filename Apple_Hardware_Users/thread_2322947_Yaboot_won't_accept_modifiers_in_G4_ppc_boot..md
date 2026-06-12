---
title: "Yaboot won't accept modifiers in G4 ppc boot."
date: 2016-05-01
forum: Apple Hardware Users
---

### Post by lukon on 2016-05-01
I've got a yaboot problem that I can't find in the search engines. So any help from yaboot experts would be much appreciated.

After installing Lubuntu 14.04.4 for PPC using the alternate install CD (the one labeled &#8220;Mac (PowerPC) and IBM-PPC (POWER5) alternate install image&#8221; at this page: [http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/)), I attempted my first boot. But I got a blank screen after the &#8220;Libuntu 14.04&#8221; & 4 dots screen. I therefore wanted to try giving yaboot some modifiers. But yaboot won't accept ANY input other than the enter key, which merely gets it to boot the Lubuntu system with the same old blank screen routine.

Here's what I mean:

After entering &#8220;l&#8221; at the stage 1 boot prompt, I get this:

*********************************************************************

Welcome to yaboot version 1.3.16
Enter &#8220;help&#8221; to get some basic usage information
boot:

[So here I enter something]

boot: XXX

[where XXX is something other than the enter key. Something like &#8220;l&#8221; or &#8220;linux&#8221; or those with modifiers. But whatever I enter there ends up replacing the XXX in the following response:]

Please wait, loading kernel...
/pci@f2000000/mac-10@17/ata-4@1f000/00:4,XXX No such file or directory
boot:

*********************************************************************

The linux system is in the 4th partition of this multi-boot setup. So the path makes sense and works great. But my problem remains: I can't send modifiers to yaboot.

Computer info:

Power Mac G4 (PowerMac3.5) Quicksilver 876-M8493
CPU = Power PC G4 2.0, 733mhz
RAM = 1.25 GB
Boot ROM = 4.2.5f1

PCI video card = nVIDIA GeForce2 MX (hence I wanted to send &#8220;nouveau.modset=0&#8221; to yaboot)

111.79 GB hard drive with about 13 partitions (some of them free space buffer zones)

Partition 01: Apple
Partition 02: Apple Bootstrap
Partition 03: Linux swap
Partition 04: Lubuntu 14.04 on EXT4
Partition 05: OSX 10.2
Partition 06: free space buffer zone
Partition 07: OSX 10.4
Partition 08: free space buffer zone
Partition 09: some future OS
Partition 10: free space buffer zone
Partition 11: another future OS
Partition 12: free space buffer zone
Partition 13: data files

---

### Post by gsahli on 2016-05-03
When you want to enter some switches/commands, use this format - Linux "nouveau.modeset=-1" (note the capital L and modeset spelling)

---

### Post by lukon on 2016-05-05
Thank you, gsahli. Your advice worked. But I did discover that I don't need to type in the quote marks.

---

### Post by gsahli on 2016-05-07
You're welcome. Thanks for clarifying on the quotes. It's been a while since I actually did that (have it in my yaboot.conf now).

---

