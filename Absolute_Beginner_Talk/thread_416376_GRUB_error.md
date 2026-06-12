---
title: "GRUB error"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by sla004 on 2007-04-21
Hi,

I just installed system 7.04 and it said that reboot and remove installation cd. When it reboots it gives following error message:

GRUB Loading, please wait ...

Error 18

I only have one harddrive and only this ubuntu installed. When I used installation cd to go back to system I saw that it think my harddrive is scsi, but it is actually ata.

Can that be a reason?

Br,

Simo

---

### Post by kiran_aryan on 2007-04-21
> **sla004 said:**
> Hi,

I just installed system 7.04 and it said that reboot and remove installation cd. When it reboots it gives following error message:

GRUB Loading, please wait ...

Error 18

I only have one harddrive and only this ubuntu installed. When I used installation cd to go back to system I saw that it think my harddrive is scsi, but it is actually ata.

Can that be a reason?

Br,

Simo
I had a similar problem. But, my pc has both SATA and IDE hard drives. I had to change IDE settings from "Compatible" mode to "Enhanced" mode in the BIOS settings to get linux installed.

---

### Post by sla004 on 2007-04-21
I checked bios and ide setting is enhanced. Is there anything else I could check?

---

### Post by sla004 on 2007-04-21
Problem was with the bios. It is not supporting as big drive as I have now.

---

