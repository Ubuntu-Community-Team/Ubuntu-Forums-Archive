---
title: "Lost Automatic Mount / Unmount CDROMs"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by andrew.46 on 2007-01-04
Hi,

 I am running Xubuntu 6.06 and seem to have lost the ability to automatically mount CDROMs. By this I mean the ability to put a CD in the drive and have it available for immediate use as an icon on the desktop.

 How can I change this back?

         Thanks for any help!

                      Andrew

---

### Post by kane77 on 2007-01-04
did you modify your /etc/fstab ?
if so post your exact content of fstab you have now.

---

### Post by andrew.46 on 2007-01-04
Hi,

 Thanks for your prompt reply:

> **kane77 said:**
> did you modify your /etc/fstab ?
if so post your exact content of fstab you have now.

Hmmm... not knowingly. But I smell a rat in the file you asked about:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

 Is the last line the culprit? What should I alter it to?

               Andrew

---

### Post by andrew.46 on 2007-01-05
Hi again,

 Hmmm..... very odd...... the cds now automount again. Possibly my computer is possessed?

                        Andrew

---

### Post by macogw on 2007-01-05
Yeah, my computer does that sometimes too.  The cd drive just refuses to open (even pressing the button on the cd drive won't open it...I was chalking it up having a Gateway).  I don't know why.  I reboot.

---

### Post by bcom on 2007-01-05
andrew.46

The noauto option on the /cdrom tells mount that this filesystem should not be mounted at boot time.  Apparently, one reason for this is that, because there is no guarantee that a CD-ROM will be available when the system boots, the noauto option prevents mount from wasting time trying to mound a drive that isn't there.

I think the command: sudo mount -a will mount all available devices.

---

### Post by bcom on 2007-01-08
Correction:

sudo mount -a will not mount a filesystem listed in /etc/fstab that is marked with the noauto option

---

