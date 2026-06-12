---
title: "netinstall on Cube using usb"
date: 2011-11-08
forum: Apple Hardware Users
---

### Post by henrythemouse on 2011-11-08
I've downloaded the oneiric boot.img.gz and transferred it to a usb stick. It boots fine on my Cube via the firmware boot command. However, when it finally gets to the partition faze of the install the partitioner doesn't recognize the hard disk. It only sees the usb stick. I've rebooted several times and rerun the disk detection several times with no luck. I modprobed hfsplus, and then retried the detection with no luck.

I've done a lucid install using this method in the past without any trouble. So, I'm wondering if this is a known issue, if anyone else has experienced this, and if there is a work-around?

TIA

---

### Post by rsavage on 2011-11-08
The ata controllers have been changed in 11.10.  On some machines they are not recognised.  For example, those using a powermac or emac may have to type
 
modprobe pata_macio
 
I wrote some instructions about installing from the mini cd here [http://ubuntuforums.org/showpost.php?p=11020435&postcount=1](http://ubuntuforums.org/showpost.php?p=11020435&postcount=1) .  If you get the 11.10 mini cd working then I'd be grateful on the feedback and I can update the post better.

---

### Post by henrythemouse on 2011-11-08
Well the mini.iso does seem to boot, but it locks up with this screen message:

Calling quiesce ...

Unfortunately, the pata_macio module is not available in the netboot img. Maybe I'll go back one version and then upgrade. 

Thanks for your help.

---

