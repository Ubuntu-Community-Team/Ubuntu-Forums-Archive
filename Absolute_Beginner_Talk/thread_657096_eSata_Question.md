---
title: "eSata Question"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by bobbocanfly on 2008-01-03
I am about to get a Western Digital 750gb USB2/Firewire400/eSata external hard drive. Seeing as eSata is meant to be super-fast and i have totally run out of USB/ Firewire ports im thinking of getting an eSata card. The hard drives at the moment are all connected with IDE/PATA and my mobo has no SATA connections. If i got a PCI eSata card would this let me connect to my eSata drive?

---

### Post by bone2006 on 2008-01-03
I have a PCI card in one of my machines that in the back gives me a ESATA connection.  I have a SATA HD inside a case enclosure that I use often with Ubuntu...........no problems.

---

### Post by tech9 on 2008-01-03
> **bone2006 said:**
> I have a PCI card in one of my machines that in the back gives me a ESATA connection.  I have a SATA HD inside a case enclosure that I use often with Ubuntu...........no problems.

If bone2006 did it, it looks like a PCI sata card will work.

---

### Post by bobbocanfly on 2008-01-03
> **tech9 said:**
> If bone2006 did it, it looks like a PCI sata card will work.

So i install a PCI Sata controller with an external connector, add the drive into my fstab and i should be fine?

---

### Post by tech9 on 2008-01-03
> **bobbocanfly said:**
> So i install a PCI Sata controller with an external connector, add the drive into my fstab and i should be fine?

Depending upon what type of Hard Drive it is, Ubuntu may even have the drivers built-in to where you will not need to edit your fstab file...

Hook it up and see if this is the case - let me know how it goes.

---

