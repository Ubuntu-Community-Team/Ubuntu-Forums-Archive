---
title: "Bootloaders besides GRUB"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by cypherzero on 2007-05-03
Why is my internal disk now called 'sda1' instead of 'hda1' as in the past, and sInce GRUB refuses to install to my internal disk displaying [I]/dev/sda does not have any corresponding BIOS drive.
[/I], are there any other bootloaders out there capable of loading Linux and Windows?

LILO seems very Linux-only and I don't want to end up with a damaged MBR.

---

### Post by Sef on 2007-05-03
> Why is my internal disk now called 'sda1' instead of 'hda1' as in the past,

It was a decision that was decided on when Feisty was being made.

---

### Post by ubnewbie2 on 2007-05-03
Is this a SATA disk?  SATA disks are more correctly/often called /dev/sd*.  IDE (PATA disks) are /dev/hd*.

I'm fairly sure Lilo can boot Windows btw - try googling it.

---

### Post by starcraft.man on 2007-05-03
I'm not really trying to say you shouldn't use GRUB, I like it. But if you really want something that supports almost any OS, try [GAG.]("http://gag.sourceforge.net/")  Its decent, and it detects and lets you boot almost any OS you can load on it.

---

### Post by gn2 on 2007-05-03
> **ubnewbie2 said:**
> 
I'm fairly sure Lilo can boot Windows 
.
It certainly can.
.
There's even instructions on Microsoft's website for how to remove it. The swines.

---

### Post by starcraft.man on 2007-05-03
> **gn2 said:**
> .
It certainly can.
.
There's even instructions on Microsoft's website for how to remove it. The swines.

LOL, I can't believe that sweet innocent Microsoft would want to provide instructions for removal of a competitors bootloader :p

---

### Post by gn2 on 2007-05-03
> **starcraft.man said:**
> LOL, I can't believe that sweet innocent Microsoft would want to provide instructions for removal of a competitors bootloader :p

Just to show I'm not making it up: [http://support.microsoft.com/kb/q171611/](http://support.microsoft.com/kb/q171611/)

---

### Post by starcraft.man on 2007-05-03
LOL again, I know I was being sarcastic... I'm surprised I didn't find a topic specifically for GRUB :p

---

### Post by louieb on 2007-05-03
got this one from the psychocat [How to Remove Linux and Install Windows on Your Computer]("http://support.microsoft.com/kb/247804")

---

