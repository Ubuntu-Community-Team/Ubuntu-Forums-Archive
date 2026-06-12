---
title: "How to apply custom DSDT??"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by kevdog on 2007-06-11
Ive got a custom DSDT for my Inspiron 5000e that I downloaded from [http://acpi.sourceforge.net/](http://acpi.sourceforge.net/).

Im trying to follow the instructions at [http://gaugusch.at/kernel.shtml](http://gaugusch.at/kernel.shtml) but I dont really understand them.  It doesnt seem I need to patch anything for ubuntu, but Im getting confused by this part of the documentation:

> 
The second step consists in adding the DSDT to the initrd (note that since version 0.8, this step is different than before). The final file has to be of initramfs type and has to contain the DSDT as a file situated at the root and called DSDT.aml. If your mkinitrd or mkinitramfs doesn't support it, you can use this script to add the DSDT file to your initramfs and then use this command:

initrd-add-dsdt initrd.img my-dsdt.aml


I saw one other post in the forum that may have suggested something totally different than this. 

Is there anyone that can give me a hand??

---

### Post by 444 on 2007-06-11
Look in /boot. That's where the initrd's are. Make a backup copy and run that script on it.

---

