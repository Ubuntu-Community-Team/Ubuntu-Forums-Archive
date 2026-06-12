---
title: "Install won't detect harddrives."
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by deezer4u on 2007-06-09
I'm doing a dual boot I have XP on my computer right now and I've been following all the guides linked from here but it's not working.  When I click text install I get a few error messages along the lines of 'ATA 1.00:Failed to set xfermode (err_mask=0x4)' and 'ATA2.00:failed to set xfermode (err_mask=0x40)' and once I get to the part where it tries to detect my disks so I can change the partitions it doesn't detect them and asks me to choose the driver from a list (none of them work).  My drives are a 250gb hitachi and a 500gb maxtor sata2 on an onboard promise card.  Any help will be greatly appreciated.

---

### Post by ghost_ryder35 on 2007-06-09
check the bios out, on some bios's there is an option for making the hard drives faster or (forget what its called native something)  deselect that.  save changes and reboot.  should work this time around.

---

### Post by deezer4u on 2007-06-09
> **ghost_ryder35 said:**
> check the bios out, on some bios's there is an option for making the hard drives faster or (forget what its called native something)  deselect that.  save changes and reboot.  should work this time around.

No option like that in my bios, it's something else causing the problem.

---

### Post by deezer4u on 2007-06-09
Still can't get it to detect the drives.  Has no one else had this particular problem before?

---

### Post by deezer4u on 2007-06-09
Tried previous versions of Ubuntu as well now and always the same error messages then it's unable to detect my hdds.

---

### Post by deezer4u on 2007-06-10
Same general thing with debian as well.  Anyone out there know anything that will help me?

---

### Post by logos34 on 2007-06-10
> My drives are a 250gb hitachi and a 500gb maxtor sata2 on an onboard promise card

So the drives are connected to the board via a pci sata controller card

---

### Post by deezer4u on 2007-06-10
> **logos34 said:**
> So the drives are connected to the board via a pci sata controller card

Nope.  Onboard as in part of the MB.

---

### Post by deezer4u on 2007-06-10
The MB is an Asus A8AE-LE.  Evidentially it's an HP proprietary board so it's hard to find info about it.

---

