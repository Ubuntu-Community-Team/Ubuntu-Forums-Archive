---
title: "BIOS Question: One 'SCSI' menu entry, but two bootable SATA devices"
date: 2015-07-26
forum: Any Other OS
---

### Post by syntaxerror74 on 2015-07-26
Well, as there is no Hardware forum here which is *independent of any OS*, I thought I might post it here as there are so many tech-savvy people on here *AND* especially those rarely found on Windows forums i. e. users with OLDER PCs. Consider that we Linuxers have excellent performance even with an old Athlon, because our OS is not so resource-hungry.
But now enough of my intro.

Whenever the menu (F8) in the BIOS says 'SCSI', this shouldn't be taken too literally. Even SATA devices might be treated as if they were SCSI ones, sometimes even getting assigned their own LUN.

The gist about my setup as follows:

(*) DVD-ROM, SATA (connected to a *newer* expansion card, one of which that also allows to boot off a DVD (early ones may not))
(*) HDD, SATA, bootable flag set, connected to the onboard SATA port
(*) It is *not* possible to connect the DVD-ROM to the *onboard* SATA port. It won't even show up there.

Again, the BIOS only gives me one 'SCSI' entry, not two. So how does the BIOS decide which of the two devices to choose for booting (supposing **both** of them are **bootable** (DVD inserted))
And, is there any way to take influence in that choice from user's side?

---

### Post by oldfred on 2015-07-27
Normally if motherboard has SATA, then boot order is set within BIOS.
In old days with IDE, you typically had two PATA/IDE connections and master/slave on each. But all those settings were those tiny jumpers (which I really really hate) on the hard drive. I converted to SATA as soon as the drive was only $10 more than PATA because I hated the tiny jumpers as I did not know which way to connect (newer did add label), could not easily see connections once installed and lost connectors. 

Did I mention I really hate the old PATA/IDE drive with jumpers? :)

---

### Post by syntaxerror74 on 2015-08-12
Thanks for your reply. Now, many experiments later, there are some interesting findings...

**Bootable 'SCSI'** **device *may* be changed by physically (!) putting the expansion card in a different PCI slot.**

It's a hit-and-miss, but it works. As my mainboard is mounted sideways, one might say that mine will do things in a 'top-down' fashion, i. e. the slot closest to the VGA will be the first one to be accessed; the one farthest from it will be last.
And this was the main trick, too, i. e. to insert the card with the HDD with the main system into the slot closest to the VGA, and then let follow the DVD-ROM.
However, note that optical devices may be very "dominant" at times nonetheless, that means that even though the expansion card now comes first, it will try to **boot off the media **if a CD or DVD is inserted!
So all you need to do is keep your optical drives "clean" of bootable media, and should you need a rescue CD, put one in and it will override the boot-up sequence and boot off the optical media. Voila!

---

### Post by oldfred on 2015-08-12
One user posted with boot issues, and it turned out to be a non-bootable DVD in DVD drive and system would not go to next device in BIOS boot order.
Not sure if him or another user had system running fsck on DVD which cannot be done so system locked up.
So yes, best not to have a bootable DVD in DVD unless you want to boot from it.

---

