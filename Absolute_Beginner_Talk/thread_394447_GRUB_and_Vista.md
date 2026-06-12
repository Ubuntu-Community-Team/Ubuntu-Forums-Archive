---
title: "GRUB and Vista"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by nudnik on 2007-03-26
I assume there are plans in the works in order to make GRUB recognize Vista and add it to the boot menu; perhaps there is a version already available which does this.

Is there a GRUB version which is capable of recognising Redmond's latest, and if so, when will it be added to Ubuntu? Is there a version already available for download somewhere?

---

### Post by 1/0 on 2007-03-27
Correct me if I'm wrong but isn't GRUB just the boot loader that starts any partition? I thought all you had to do is:

```
title         "whatever"
root         (hd0,0)
chainloader      +1
```

Or sd0,0 if you got scsi or sata drives. As for recognizing, the boot loader don't recognize anything that's not in the config file (/boot/grub/menu.lst). On the other hand, I haven't run Microsoft OSs in 7 years so maybe I'm wrong...

---

### Post by Doug11 on 2007-03-27
> **nudnik said:**
> I assume there are plans in the works in order to make GRUB recognize Vista and add it to the boot menu; perhaps there is a version already available which does this.

Is there a GRUB version which is capable of recognising Redmond's latest, and if so, when will it be added to Ubuntu? Is there a version already available for download somewhere?


Grub already recognizes vista. I dual boot Edgy and Vista and grub gives me the option to boot my Linux kernel or Vista.

---

