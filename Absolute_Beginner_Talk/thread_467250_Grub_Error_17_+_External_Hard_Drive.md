---
title: "Grub Error 17 + External Hard Drive"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by flowheat on 2007-06-07
I'm running a dual booted HP DV9030US with Vista and Fiesty. I did a full format on the second hard drive and installed Fiesty there.  While I was doing this I had a 500GB Western Digital MyBook connected.  Now whenever Grub loads up it gives me "Grub Error 17: Cannot mount selected partition" if the external hard drive is plugged in.  If I disconnect the external and reboot everything works fine(both vista and fiesty).  Both also access the external hard drive fine once into the respective operating systems.  Not a huge problem, but a minor annoyance.

Any Ideas?

Thanks in advance.

---

### Post by confused57 on 2007-06-07
> **flowheat said:**
> I'm running a dual booted HP DV9030US with Vista and Fiesty. I did a full format on the second hard drive and installed Fiesty there.  While I was doing this I had a 500GB Western Digital MyBook connected.  Now whenever Grub loads up it gives me "Grub Error 17: Cannot mount selected partition" if the external hard drive is plugged in.  If I disconnect the external and reboot everything works fine(both vista and fiesty).  Both also access the external hard drive fine once into the respective operating systems.  Not a huge problem, but a minor annoyance.

Any Ideas?

Thanks in advance.

You could boot into Ubuntu & check the output of:
```
sudo fdisk -l
gedit /boot/grub/device.map
gedit /boot/grub/menu.lst
```
it's possible that your external hard drive is (hd1) and your Ubuntu drive is (hd2), but when you disconnect your external hard drive, your Ubuntu drive could possibly be (hd1)...menu.lst and device.map may show this?

Then disconnect your external hard drive, boot up the Ubuntu live cd, and run "sudo fdisk -l" from the live cd...You probably don't need to do this, since Feisty uses UUID's to identify partition filesystems.

---

