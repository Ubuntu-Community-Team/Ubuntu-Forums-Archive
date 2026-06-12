---
title: "[SOLVED] Gutsy Grub Error 21"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by exile on 2008-01-13
I installed xubuntu on a 4gb flash disk.. Went through the LiveCD install with the flash disk plugged into my laptop. Install went great. I was sure to select the USB partition etc.

Problem: unplugged the usb disk and restarted my laptop. GRUB error 21 - basically a disk that grub is looking for doesn't exist. Plug the USB in and boot into my old system from that GRUB runs fine and I can get to both the disk based install and the USB one.

hd0,2 is the disk that my original grub was operating from.

I've tried:

>sudo grub
>root (hd0,2)
>setup (hd0,2)
>quit

reboot and the same problem. Am I missing a step? Is there a command to tell grub to commit to the MBR?

Thanks in advance!

---

### Post by dcstar on 2008-01-13
> **exile said:**
> I installed xubuntu on a 4gb flash disk.. Went through the LiveCD install with the flash disk plugged into my laptop. Install went great. I was sure to select the USB partition etc.

Problem: unplugged the usb disk and restarted my laptop. GRUB error 21 - basically a disk that grub is looking for doesn't exist. Plug the USB in and boot into my old system from that GRUB runs fine and I can get to both the disk based install and the USB one.

hd0,2 is the disk that my original grub was operating from.

I've tried:

>sudo grub
>root (hd0,2)
**>setup (hd0,2)**
>quit

reboot and the same problem. Am I missing a step? Is there a command to tell grub to commit to the MBR?

Thanks in advance!

```
**setup (hd0)**
```

---

### Post by exile on 2008-01-13
Ahh.. worked a treat. Thanks.

---

