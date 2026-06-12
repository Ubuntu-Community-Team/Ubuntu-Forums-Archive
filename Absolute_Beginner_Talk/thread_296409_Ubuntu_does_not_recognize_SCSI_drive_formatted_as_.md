---
title: "Ubuntu does not recognize SCSI drive formatted as NTFS"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by callumm on 2006-11-09
Hi,

I am fairly new to Linux but have some basic computer understanding.  I am currently stuck installing Ubuntu because it seems it does not recognize the SCSI hard drive that is formatted as NTFS.  I installed Vista on the machine, an IBM x-series 200 with a PIII 1266 and 512 MB ram. I also opened it up and vacuumed the dust out of it.  After I tried to boot it up again it gave the following errors: PXE-E61:Media test failure - check cable.  Anyone have any ideas how I can boot from Ubuntu CD (which works) and see the scsi disk so I can reformat it?

Thanks in advance for any help.  Pelase let me know if you need any more details.

Callum

---

### Post by callumm on 2006-11-09
Hi,

I am fairly new to Linux but have some basic computer understanding.  I am currently stuck installing Ubuntu because it seems it does not recognize the SCSI hard drive that is formatted as NTFS.  I installed Vista on the machine, an IBM x-series 200 with a PIII 1266 and 512 MB ram. I also opened it up and vacuumed the dust out of it.  After I tried to boot it up again it gave the following errors: PXE-E61:Media test failure - check cable.  Anyone have any ideas how I can boot from Ubuntu CD (which works) and see the scsi disk so I can reformat it?

Thanks in advance for any help.  Please let me know if you need any more details.

Callum

---

### Post by K.Mandla on 2006-11-09
(Merged duplicate threads. ;) )

---

### Post by ReaderRat on 2006-11-09
To look at your partitions, and do any formatting, I would suggest using [**Gnome PARTition EDitor = gparted**](http://gparted.sourceforge.net/index.php). It is also able to resize partitions, and do other useful things.It is bootable.

---

### Post by callumm on 2006-11-12
Thanks for the response reader rat.  The Gparted utility does not recognize any devices.  I will try again to ensure the cables are secure.

Thanks,
C

---

### Post by callumm on 2006-11-12
After reviewing the cables (there was one cable that only had one end plugged in) and checking part numbers, I realized I had 2 SCSI adapters.  Cant really say why that was but after taking out one of the adapters everything is working fine.  We are installing Ubuntu as I write!

Thanks!

---

