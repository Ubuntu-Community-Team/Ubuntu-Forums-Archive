---
title: "ghostbsd cannot dual boot with ubuntu"
date: 2021-01-04
forum: BSD
---

### Post by VMC on 2021-01-04
I've tried every possible combination of grub menu commands:
```
menuentry "GhostBSD Loader" {       insmod part_gpt
        insmod chain
        set root='(hd3,gpt1)'
        chainloader /EFI/ghostbsd/BOOTX64-GHOSTBSD.EFI
}
```
That is the one everyone list when trying to dual boot with ubuntu.
It doesn't work. Grub output is:
```
error: image has invalid negative size
```

Tried other menu commands as I stated. Will not boot.
ghostbsd will boot using it own boot manager, but cannot get it to dusl-boot.

Has anyone dual booted ubuntu and ghostbsd?

This link shows same error I got:
[https://forums.freebsd.org/threads/grub-error-image-has-invalid-negative-size.70974/](https://forums.freebsd.org/threads/grub-error-image-has-invalid-negative-size.70974/)

---

