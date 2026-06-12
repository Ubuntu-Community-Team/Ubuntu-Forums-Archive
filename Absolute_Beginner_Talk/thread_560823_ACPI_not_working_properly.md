---
title: "ACPI not working properly?"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by Yes on 2007-09-26
When I try to find my CPU temperature via the terminal command acpi -V, I get the error

```
No support for device type: thermal
```

Is there anything else I need to install to find my CPU temp?  Or is there an alternative to ACPI that I could use?

Thanks.

---

### Post by nonewmsgs on 2007-09-26
is acpi enabled in BIOS?

---

### Post by raseel on 2007-09-26
Its working fine for me on compaq Presario F572US Laptop with ubuntu Feisty Fawn.
Do you have acpi drivers ?

When I lsmod, I get the following :

$ lsmod | grep acpi
dev_acpi               12292  0 
sony_acpi               6284  0 
pcc_acpi               13184  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi

---

### Post by Yes on 2007-09-27
I'm not sure if it's enabled in the BIOS, I'll have to check next time I reboot.  I'm also not sure if I have the drivers installed, how would I chech for that?  When I ran 'lsmod | grep acpi', I got the same output as you.

Thanks.

---

