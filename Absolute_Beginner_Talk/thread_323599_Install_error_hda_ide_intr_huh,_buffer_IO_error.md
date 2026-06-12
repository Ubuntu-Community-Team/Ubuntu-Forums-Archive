---
title: "Install error: hda ide_intr: huh?, buffer I/O error"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by trosdquoniam on 2006-12-22
Hey there!

I hope somebody can help. I'm new to Linux and I'm totally lost. I recently built a new system from scratch (Intel Core 2 Duo E6600, asus p5b mobo, 2 GB RAM, 3 SATA HDD drives, nvidia grpahics card).

I downloaded and burned the .iso of Ubuntu 6.10 edgy on a CD.

I boot the machine with the CD in it, and I try to start the installation procedure. After hitting "Install ubuntu" I get a long string with the following error messages:

hda: ide_intr: huh? expected NULL handler on exit
Buffer I/O error on device hda, logical block 35764

This keeps repeating endlessly, though the logical block changes.

Any ideas as to what this is pointing to? What is device hda? What can I do?

Thanks!

---

### Post by okipatrick on 2006-12-22
> **trosdquoniam said:**
> Hey there!

I hope somebody can help. I'm new to Linux and I'm totally lost. I recently built a new system from scratch (Intel Core 2 Duo E6600, asus p5b mobo, 2 GB RAM, 3 SATA HDD drives, nvidia grpahics card).

I downloaded and burned the .iso of Ubuntu 6.10 edgy on a CD.

I boot the machine with the CD in it, and I try to start the installation procedure. After hitting "Install ubuntu" I get a long string with the following error messages:

hda: ide_intr: huh? expected NULL handler on exit
Buffer I/O error on device hda, logical block 35764

This keeps repeating endlessly, though the logical block changes.

Any ideas as to what this is pointing to? What is device hda? What can I do?

Thanks!

When you get to the boot menu with the edgy CD in, try pushing F6 to specify boot options.  Add "irqpoll" w/out the quote as a new argument to the line and see if that helps.  You may also want to put "acpi=ht" as well (helps some people)

---

### Post by trosdquoniam on 2006-12-28
Thanks!

I forgot to get back to the forums just to say that I got past the error messages by simply waiting. I still don't know what caused them, but after a couple of minutes the Ubuntu boot processs went further, I could boot with the Live CD and install from there.

After a couple of hours struggling I even managed to install NVIDIA latest drivers and use Beryl - WOW!

I still feel quite lost with the use of terminals, but I hope to progress slowly.

---

### Post by amniarix on 2007-01-07
I got exactly the same problem, trying to install 6.10 (2.6.17-10 kernel) via CD. The Ubuntu splash screen appears to hang, and after pressing alt-F1 to view the logs, I see:

PCI: JMB36x: Enabling dual function on 0000:03:00.0
PCI: Cannot allocate resource region 0 of device 0000:03:00.0
PCI: Cannot allocate resource region 1 of device 0000:03:00.0
PCI: Cannot allocate resource region 2 of device 0000:03:00.0
PCI: Cannot allocate resource region 3 of device 0000:03:00.0
PCI: Error while updating region 0000:03:00:00.0/0 (0000c000 != 00000000)
PCI: Error while updating region 0000:03:00:00.0/2 (0000c008 != 00000000)
ata6 failed to respond (30 secs)
ata6 failed to respond (30 secs)
hda: ide_intr: huh? expected NULL handler on exit
hda: ide_intr: huh? expected NULL handler on exit
Buffer I/O error on device hda, logical block 357566
hda: ide_intr: huh? expected NULL handler on exit
hda: ide_intr: huh? expected NULL handler on exit 
Buffer I/O error on device hda, logical block 357566
[.. last 3 lines repeat ..]

This happened for ~11 minutes after which, as you say, the installer proceeds. For subsequent reboots after the installation, it only hangs for 1 minute, printing:

PCI: JMB36x: Enabling dual function on 0000:03:00.0
PCI: Cannot allocate resource region 0 of device 0000:03:00.0
PCI: Cannot allocate resource region 1 of device 0000:03:00.0
PCI: Cannot allocate resource region 2 of device 0000:03:00.0
PCI: Cannot allocate resource region 3 of device 0000:03:00.0
PCI: Error while updating region 0000:03:00:00.0/0 (0000c000 != 00000000)
PCI: Error while updating region 0000:03:00:00.0/2 (0000c008 != 00000000)
ata6 failed to respond (30 secs)
ata6 failed to respond (30 secs)

hda is the CD drive. On my motherboard (MSI P965) and yours it's plugged into the only IDE channel available, and is handled by an infamous JMicron controller. If you google for this you'll find [bug 57502]("https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/57502"), which appears to be what you've hit.

Two other bits of info:
[LIST]
[*]I can get rid of the "Cannot allocate resource" and "Error while updating region" errors by loading the BIOS (hit del on startup) and going to Integrated Peripherals -> Onboard RAID Controller (options: Disabled, RAID, IDE), and switching this to "RAID".
[*]When installing the alpha of 7.04 (feisty fawn) with 2.6.20 kernel, I didn't have that 10 minute hang, and regular boots don't print the "ata6 failed to respond (30 secs)" error, so these problems may be a thing of the past when 7.04 is released.
[/LIST]

---

### Post by ninjagore on 2007-02-25
I am also having this same error. I am trying to install 6.10 Edgy on my new computer. I downloaded it onto cd just fine, and checked the cd for defects before trying to install it. I continue to get the same error,  though. If it helps, I have an MSI k9n6gm v series motherboard with pata optical drives. I also have an ide drive, converted to a sata drive. I also have socker AM2 with Athlon XP X2 3800+.

I just want the CD to load into a desktop so I can install 6.10.
I can get to the original screen where you can start or install, do mem test, etc. All I want is to install 6.10 Is there a way to just install ubuntu from that screen?

Any help on this would be appreciated.

---

### Post by Quickdood on 2007-03-02
I had this same problem, it turns out it was my CD drive, which is kind of weird because my cd drive is brand new.  Anyway I have two cd drives so I popped the cd into my second cd drive and no problem.  I hope this can help!

---

### Post by Skull Kid on 2007-03-02
I had this same problem when I first installed Ubuntu. I waited a bit like the OP did and it just conintued, so I assume everything's fine, and a month later, it looks like it is. Is it anything to worry about?

---

