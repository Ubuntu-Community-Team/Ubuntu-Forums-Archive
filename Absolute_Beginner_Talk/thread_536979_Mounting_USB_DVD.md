---
title: "Mounting USB DVD"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by owenb@theofficenet.com on 2007-08-28
My Tecra 8000 desktop shows the icon recognizing the external USB  DVD drive. It even shows the title of the disc within.
But when I go to access the contents of the disc. I get these error messages:
     "Error -Konqueror
  Could not mount device."
The reported error was:
   Mount: cant find /dev/scd0 in etc/fstab or etc/mtab

Or I get:
     "Error KsCD
CD-ROM read or access error (or no audio disc in drive)
Please make sure you have access permissions to /dev/cdrom.

Can anyone please tell me step by step how to rectify this?
Thanks, 
             Owen

---

### Post by Marat Galiev on 2007-08-28
You must edit you /etc/fstab.

read ```
man fstab
```.

---

