---
title: "Linux identification of devices"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by Seanchen on 2007-02-04
I am trying to install Ubuntu to my usb hd, but I am not postive of something.

I am asked to pick a installation device, and I picked my usb hd which is listed as ( 0,0,0 ) my main sata hd is ( 0,1,0 ).

My first question is what do those numbers mean?

My second question if my BIOS lists the hds in ( sata hd, then usb hd ) which device would be hd0 because Grub whats to install there.

I am a complete newbie, any advice how to identify each device, so I don't screw up my main hd?

Clearly I want to install the Grub to the usb hd, and NOT to my main sata device.  I have tread that hd0 is the first device seen by bios, does that mean the "boot order" of the hds?

Would making a boot cd be easier at this point?

I could also try to make the usb hd be seen first, I just to need to make sure which device is hd0 before I go pressing that big red button...

---

### Post by jpkotta on 2007-02-06
Install to USB drive:
[http://ubuntuforums.org/showthread.php?t=308027](http://ubuntuforums.org/showthread.php?t=308027)

Grub information (including how to know which device is which):
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

I am guessing that because USB uses some of the SCSI framework (this is why USB drives come up as /dev/sd*) (SATA also uses the SCSI framework, but not for long), that the triple you have is (bus,target,lun).  But I'm not sure.  Whether I'm right or not, I'm guessing that it could change.

If you're worried about overwriting your HD, then just unplug it while you install.  Grub will not ruin your HD.  It will just write to the MBR.  You can always rewrite the MBR using a Live CD or a Windows install CD.  Grub should never mess with the data on the drive.

---

### Post by Seanchen on 2007-02-08
> * Grub by default installs to the first hard drive detected by the BIOS. The simplest way to ensure that it installs correctly is to make sure that the only hard drive available is the install target drive.

Does this mean the order of the drives within the BIOS?

If so can I just change said order, and be able to install the os and grub to the drive, I would then of course modify grub to be able to boot to my main hd when I wanted.

:guitar:

---

