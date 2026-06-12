---
title: "CD ROM Emulation Program?"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by DSn0wMan on 2006-05-21
Is there a CD ROM Emulation Program for ubuntu?

For windows I use Daemon tools, or Alcohol. What would the linux equivelent be?

---

### Post by aysiu on 2006-05-21
Qemu?

---

### Post by DSn0wMan on 2006-05-21
I am not sure if qemu is what I want? I just want to mount iso, mds, bin/cue files from my hard drive, as if they where mounted in a CD ROM drive.

---

### Post by mlind on 2006-05-21
I've used cdemu. You need to compile a kernel module for it (but not the whole
kernel).

You can mount atleast .iso and .mdf (Alcohol?) files using loopback device
```

sudo mkdir -p /mnt/image
sudo mount -o loop /path/to/image /mnt/image

```

then there's conversion utils like bchunk and mdf2iso, which allow you to convert
other images to .iso images.


to compile module for cdemu, you need atleast build-essential, gcc3.3, linux-kernel, and linux-kernel-headers
(or was it kernel-headers..) packages.

---

### Post by DSn0wMan on 2006-05-21
mlind,

The loopback did the trick for now. I'll try cdemu after I have had some sleep.

Thanks for the tip!

---

### Post by aysiu on 2006-05-21
If you use Qemu with an ISO... ```
qemu -cdrom nameofdistro.iso
```

---

### Post by DSn0wMan on 2006-05-22
[QUOTE=aysiu]If you use Qemu with an ISO... ```
qemu -cdrom nameofdistro.iso
```[/QUOTE]

Cool, thanks again aysiu!

---

