---
title: "RAID1 and ubuntu7.10"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by sloop on 2007-10-24
Hi to all.I have to use ATA133 RAID Controller DM-8401R in RAID - 1mode.With Open SUSE works, but with xubuntu 7.04 and ubuntu 7.10 doesn't work.Does any of you has such problem?Why doesn't work? I expect to run graphical interface but it runs only a kind of command prompt.

---

### Post by overdrank on 2007-10-24
> **sloop said:**
> Hi to all.I have to use ATA133 RAID Controller DM-8401R in RAID - 1mode.With Open SUSE works, but with xubuntu 7.04 and ubuntu 7.10 doesn't work.Does any of you has such problem?Why doesn't work? I expect to run graphical interface but it runs only a kind of command prompt.

HI I see you have many post on this issue( just asking) are you sure you downloaded the desktop version?

---

### Post by sloop on 2007-10-24
Yes, I'm sure.

---

### Post by overdrank on 2007-10-24
> **sloop said:**
> Yes, I'm sure.

Ok are you getting any error messages? And this is just running the live cd correct?

---

### Post by sloop on 2007-10-24
I'll explain.The PC is :Intel(R) Celeron(R) CPU 2.66GHz(133x20),RAM=516MB,I945-chipset
The last instalacion was xubuntu 7.04.After the installacion and restart is givs:
GRUB loading
Starting up
'XUBUNTU'
5minutes waiting
/bin/sh: can't access tty; job control turned off
(initramfs)_

---

### Post by overdrank on 2007-10-24
> **sloop said:**
> I'll explain.The PC is :Intel(R) Celeron(R) CPU 2.66GHz(133x20),RAM=516MB,I945-chipset
The last instalacion was xubuntu 7.04.After the installacion and restart is givs:
GRUB loading
Starting up
'XUBUNTU'
5minutes waiting
/bin/sh: can't access tty; job control turned off
(initramfs)_

Hi, You can try and press esp key at the grub line, this will allow you to edit  the kernel line by pressing e and you can remove the quiet splash and add noapic and then hit enter and then  b to boot. By removing the splash you can see any errors. Hope this helps. Good luck!

---

### Post by sloop on 2007-10-25
All try but I'm negativer.Thank you.

---

