---
title: "Uninstalling Ubuntu"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by JohnLJH on 2007-08-16
I have a main drive with WinXP, and installed Ubuntu 7.04 on my secondary removable hard drive.

First I disabled my main drive in the BIOS, wanting to run Ubuntu independently for evaluation.

To my surprise, the dual boot (GRUB) installed on my main drive, which  won't even kick over unless my removable drive with Ubuntu is running.

How do I get a clean Ubuntu uninstall, so I can physically disconnect my main drive and reinstall Ubuntu as a self-standing program?

Why is there no OS-uninstall command built into Ubuntu?

I have PartitionMagic 8 on my main drive, if this helps.

Thanks in advance for any help.

JohnLJH

---

### Post by Hobo Joe on 2007-08-16
Well, I'm not an expert on GRUB and partitions, but I think you can just have the Ubuntu partitions swallow the Windows one, and then repair grub. But I'm not sure about that, so get a second opinion first. :)

---

### Post by vexorian on 2007-08-16
> 
Why is there no OS-uninstall command built into Ubuntu? mostly because that's not available in any OS.

--
clean uninstall: use some tool to format the partition where ubuntu was installed, then use the windows XP cd:

when it tells something like "press R to enter recovery console" press R

once you get into the console, type: fixmbr

---

