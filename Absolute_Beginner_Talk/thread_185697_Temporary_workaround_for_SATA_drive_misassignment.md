---
title: "Temporary workaround for SATA drive misassignment"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by therunnyman on 2006-06-01
The devs don't appear to want to fix this, so I'll do my best here to help.

A lot of servers, RAIDs and whatnot have two SATA hard disk ports on the mainboard, then a card (PCI, PCI-X, or PCI-express) for additional SATA drives.  For instance, I have three disks on the machine I'm writing this from, two plugged into the mainboard, and one plugged into a PCI card.  Many prefab machines come this way: Dell's servers do, I believe, and I think, well, hell, a lot of servers have that setup.  Four SATA drives, two plugged into the mainboard and two plugged into a card.

You'll notice when you install Dapper to, say, SATA 0 (first mainboard port), everything will appear to be operating as normal, but it ain't.  What will likely happen on reboot is a spiteful message and a drop to a shell.  True bummer.

What's happened is your PCI devices are loaded first, so sda will be whatever drive you've got plugged in to your card (and sdb will be whatever drive you've got hooked to port 2 of the card).

The main problem is in udev, and I'm working on that solution.  Meantime, all we RAID/more-than-two-SATA-drives people can do is physically rewire the hard disks according to this schema:

Card Port 1 = sda
Card Port 2 (if present) = sdb
Mainboard 0 =sdb (if there's only one drive rigged to the card) or sdc.
Mainboard 1= sdc (if there's only one drive hooked into the card) or sdd.

Striping gets really hairy here.  Pre-install, the mainboard ports will be sda and sdb, even during the partition phase.  Here, you should proceed as if sda, sdb, sdc and so on will be properly identified.  Once finished, physically rewire your drives as described above.

As soon as I have this udev file figured out, I'll post it.

runny

---

### Post by Roscoe62 on 2006-06-05
Hi therunnyman,

Just letting you know there's at least ONE person who's very keen to see your solution to this problem! :) 

Good luck!

---

### Post by thor918 on 2006-11-12
what's irritating about sata is that a new disk screwes up the existing mounting in fstab.
I got a promise pci 4 porter sata card and 2 sata onboard.
if I put a disk on the pci card. all my previuos mounting would be screwed becase the disks gets different /dev/sd names

---

### Post by Zotty2 on 2006-11-19
My god, finally someone with the same problem. Was starting to think I was the only one :D Got Promise SATAII150 TX4 card and 4 onboard SATA ports.

Here's my situation and how the disks are connected;

Onboard VIA chipset SATA
SATA1 = Linux boot
SATA2 = nc
SATA3 = data disk
SATA4 = nc

Promise SATAII150 TX4
channel 1 = data disk
channel 2 = data disk
channel 3 = data disk 
channel 4 = data disk

Standard IDE
IDE1 primary = WinXP
IDE1 slave = nc
IDE2 primary = DVD drive
IDE2 slave = nc

This is what happens. I work with the BIOS bootmenu, since winxp refused to install on a sata drive months ago...

Linux with Promise harddisk(s) turned off:
Press F8 during BIOS boot, get a BIOS bootmenu and select the Linux boot drive. All boots fine.

Linux with Promise harddisk(s) turned on:
Press F8 during BIOS boot, get a BIOS bootmenu and select the Linux boot drive. Kernel extracts and loads, but ends up with a sandbox becuase there is no valid boot device.

Boot output shows that the Promise card's channels are found as SCSI0 to SCSI3, while the onboard channels are SCSI4 to SCSI7. This is where I think the problem lies and it fits your description of the problem.
When a harddisk connected to the Promise card is turned on, the kernel thinks it whould boot from that disk and never reaches the real bootdisk which is detected at SCSI4.

So did you book any progress? This thing is driving me insane, but I'd more than happy to help out with testing if needed.

A small tip which works fine for me, in fstab, use UUID's instead of /dev/sdxx

---

### Post by CatKiller on 2006-11-19
> **Zotty2 said:**
> A small tip which works fine for me, in fstab, use UUID's instead of /dev/sdxx

I think Edgy does this by default. I'd wondered why.

---

### Post by emdeem on 2006-11-19
FWIW, I had a similar experience when installing using a USB boot memeory stick on a notebook with SATA.  The USB stick was sda, so grub was set up to boot from /dev/sdb.  After the install, I had to boot from the stick again, enter rescue mode, and fix menu.lst and device.map.

---

### Post by kiyometane on 2006-11-19
that's the same problem i have.
My serverboard have 2 onboard sata ports and 2 sataII ports on a pci card.
2 hardrives are conected to the onboard ports
May be you could help me with my edgy loading problem.
I move the hardrive with edgy to the pci card and now i cant boot in edgy. it freezes at logo screen.

---

