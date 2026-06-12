---
title: "Cd-rom not recognised"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by baysl on 2007-09-27
In my PC I have DVD-ROM and CD-ROM unit.

I install Ubuntu with DVD-ROM.
Ubuntu only sees DVD-ROM and doesnt see CD-ROM.
When I put cd in CD-ROM nothing happens.

How do I make my CD-ROM work?

---

### Post by dca on 2007-09-27
Is this the first you're noticing it, because normally if it's on the same IDE channel I'd re-verify that the jumpers are set to 'cable select'...  Also after checking, look in the BIOS (press delete or [F*] key on start-up) and make sure the they're both recognized...  Also, post contents of /etc/fstab file...

---

### Post by baysl on 2007-10-02
When I insert cd in cd-rom I get this error:

[B]Cannot mount volume:
Invalid mount option when attempting to mount the volume.[/B]

Contents of my /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=142b5f16-7e1a-4cb9-90f4-95d88fb96c13 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=e0319cb4-ee0d-44d9-8805-500d411ccb39 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1     /media/Windows     ntfs-3g     defaults,locale=en_US.utf8   0    0
/dev/sdd1     /media/sdd1     ntfs-3g     defaults,force 0 0


Any sugestions?

---

### Post by baysl on 2007-10-03
Can you help?

Please

---

### Post by LowSky on 2007-10-03
fstab seems to only see the one drive... can you answer these questions for me

did the drive work under a different OS like windows?

can you see the drive in BIOS?

Is either drive new? do the drives use the same cable or are they on different cables?

Is the cbale pluged in all the way in the CDROM and motherboard?

Is the Jumper set to Cable select?

---

### Post by baysl on 2007-10-03
Yes, it worked in windows.
I can see it in BIOS.
No its not new. They use the same cables.
Yes.
Yes.

---

