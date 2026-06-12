---
title: "HDD on CD IDE Cable???"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by charles.g.moore on 2006-09-17
I found out that I can get the BIOS only to see my HDD if it is plugged into the IDE cable reserved for the CD-ROMS

Im trying to set up my OLD system as a server, can I leave the HDD on the CD IDE cable and if so should it be the master or slave, and will I be able to still use the CD-ROM to load ubuntu server

---

### Post by orb9220 on 2006-09-17
You should have a primary and secondary ide connector on motherboard.
May also be called ide0 and ide1.

The primary Hd should be master and on first ide port.
The cdrom can be slave on the primary with HD or set as master on secondary.

If you only have one cable then grab another one and then you can set it  on secondary ide as master.

If you put cdrom with HD on same channel then visually verify that cdrom  is set as slave and HD is master.

Which you can verify from the bios and see how the devices are connected without opening the machine.

With standard motherboards you can have two ide devices per channel for a max of 4 devices.

---

### Post by JayTee on 2006-09-17
Do you have two IDE connectors on your motherboard? And if so are you trying to use another cable for the HD on a separate IDE connector? Some hard drives won't work with an older IDE cable i.e. 40-pin 40-wire and require the new IDE cables 40-pin, 80-wire. Especially the ATA-133 drives but some ATA-100 drives won't work with an older cable either. When it comes to jumper settings if I have a computer with a HD and a CDROM on the same IDE channel I set the HD as primary or MASTER and the CDROM as SLAVE. If you want to boot off the CDROM just change the order of the boot devices in your BIOS.

---

