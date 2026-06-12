---
title: "VERY unique problem with my partitions"
date: 2009-06-03
forum: Apple Hardware Users
---

### Post by fitzydog on 2009-06-03
So, it all stated with me wanting to have Ubuntu on my mac. I'm a linux noob, but have leaned quickly. Installed it, been running that and Windows ONLY for a couple of months now. I erased the mac part for other reasons that I won't go into. I had three major partitions, one ubuntu's file system, one for my "other home", and the last one was windows. Recently, I wanted more room on the file system, so I booted up the live cd, and adjusted the sizes of the "other home" and Ubuntu. I thought, "Hey, I've done this before, it'll be just the same." well, I restarted it, and it something like, "No boot device found" WOW. WTF was that? so, I calmly restarted it and held down ALT, and nothing. it was blank. huh? I inserted the cd, and that pops up on the bootcamp screen, with no other partitions there. I use the cd, and choose "boot from first hard disk", and there is no more GRUB. I booted with the live cd, and the partitions themselves are perectly fine. nothing happened with them. What do I do?

---

### Post by utnubuuser on 2009-06-03
reinstall grub.

google "reinstall grub from live cd ubuntu".

[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")
but I'm not sure that this method will include being able to access your Windows OS.

Before you reinstall you might want to find your /boot/grub/menu.lst file and make a backup of it before it's over-written, because you might only have to change the block-id info in fstab to be able to re-use the original fstab file once you're up and running again.

You can get updated block-id info with> sudo blkidin terminal
and you can edit fstab with > sudo nano /etc/fstab

---

### Post by fitzydog on 2009-06-21
Sorry it took so long to respond. Yes, it was GRUB that got deleated(although I have NO idea how). I backed up all my files onto an external and reinstalled. I'm thinking about switching to rEFIt so I can get my Windows functionality back. I installed it from synaptic, but what do I do with it now? Should I start a new thread on this?

---

### Post by Richardcavell on 2009-06-21
Hi,

GRUB often has to be reinstalled after you resize your partitions.  It's temperamental like that.  Don't panic.

rEFIt will not alleviate your need to use GRUB to load Ubuntu.  What it does is present operating system choices to you and invite you to select one.  It transfers control to GRUB when you select Ubuntu.

Richard

---

### Post by fitzydog on 2009-06-21
Right.... I got GRUB back already, but I was wondering if rEFIt would fix the problem of none of my partitions showing on the Bootcamp screen.

---

### Post by Richardcavell on 2009-06-22
No, rEFIt will not solve that.  Boot Camp only fully cooperates with partitions that it has created.  It shouldn't be an issue, though.  Absence of Boot Camp does not affect your ability to use Linux.

Richard

---

### Post by fitzydog on 2009-06-23
Okay, good. I read somewhere that XP has to be somewhere 'special' on the MBR for it to boot correctly. Is that why it's not booting? It gives me a message saying such-and-such a file is missing or corrupt.

---

