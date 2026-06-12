---
title: "Boot loader overwritten"
date: 2007-03-04
forum: Apple PPC Users
---

### Post by robert-s on 2007-03-04
Hello. I had Edgy and Panther installed on my iBook G4, and yesterday I upgraded to Tiger. However it seems that the Tiger installation has overwritten the boot loader, so I don't get the choice of booting into Linux any more, it just boots OSX right away. Is there any way to reinstall the boot loader without completely reinstalling Edgy?

Thanks.

---

### Post by machead5 on 2007-03-04
Try this... 
Resetting PRAM and NVRAM

   1. Shut down the computer.
   2. Locate the following keys on the keyboard: Command, Option, P, and R. You will need to hold these keys down simultaneously in step 4.
   3. Turn on the computer.
   4. Press and hold the Command-Option-P-R keys. You must press this key combination before the gray screen appears.
   5. Hold the keys down until the computer restarts and you hear the startup sound for the second time.
   6. Release the keys.

Your computer's PRAM and the NVRAM are reset to the default values. The clock settings may be reset to a default date on some models.

---

### Post by calum on 2007-03-04
> **robert-s said:**
> Hello. I had Edgy and Panther installed on my iBook G4, and yesterday I upgraded to Tiger. However it seems that the Tiger installation has overwritten the boot loader, so I don't get the choice of booting into Linux any more, it just boots OSX right away. Is there any way to reinstall the boot loader without completely reinstalling Edgy?

Thanks.

Probably, assuming you didn't resize any partitions to make room for Tiger:

1. Hold down option key while booting, this will show you a list of bootable partitions.  Choose the Linux partition.
2.  Once booted into Linux, run "/usr/sbin/ybin" as root.  This should restore your boot menu.

As always, you might want to back up anything vital first.

---

