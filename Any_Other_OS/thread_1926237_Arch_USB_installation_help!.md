---
title: "Arch USB installation help!"
date: 2012-02-15
forum: Any Other OS
---

### Post by drawkcab on 2012-02-15
I would like to install Arch on one of my netbooks but I'm having a difficult time creating a bootable USB for installation.  I've tried following the easier options on the Arch wiki, some howtos, etc. but I can't ever seem to get it right.  

Am I missing something obvious or what?  I haven't had this frustration with any other distro.

Can anyone point me in the right direction?

---

### Post by drawkcab on 2012-02-15
Or Archbang for that matter!

---

### Post by mips on 2012-02-16
dd if=/path/to/archlinux.iso of=/dev/sd[x] 

Where [x] is the letter of the USB device, this you can get from **sudo fdisk -l**. Do NOT specify a number after the letter as you are then specifying a partition and not the entire device.

On my PC I would do
```
sudo dd if=/media/160GB_WD/Linux/archlinux-2011.06.10-netinstall-dual.iso of=/dev/sdi
```

---

### Post by drawkcab on 2012-02-16
Dang.  I was hoping for something easier.  I'll give it another shot though.  I must have screwed something up last time.

Thanks!

---

### Post by mips on 2012-02-16
> **drawkcab said:**
> Dang.  I was hoping for something easier.

I don't think you can get any easier than that.

---

