---
title: "AGP aperture size"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by papuaoshi on 2006-09-04
My newly compiled kernel 2.6.17.x prints the following message during the boot process. This is an advise... huh... I dont get it :)

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Aug 23 13:59:35 localhost kernel: [   20.374578] agpgart: Detected AGP bridge 0
Aug 23 13:59:35 localhost kernel: [   20.375068] agpgart: Aperture conflicts with PCI mapping.
Aug 23 13:59:35 localhost kernel: [   20.375075] agpgart: Aperture from AGP @ f8000000 size 4096 MB
Aug 23 13:59:35 localhost kernel: [   20.375077] agpgart: Aperture too small (0 MB)
Aug 23 13:59:35 localhost kernel: [   20.375079] agpgart: No usable aperture found.
Aug 23 13:59:35 localhost kernel: [   20.375081] agpgart: Consider rebooting with iommu=memaper=2 to get a good aperture.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

So how can I set AGP aperture?

---

### Post by coolclassic on 2006-09-04
Try looking in bios to adjust aperture size

---

### Post by szf on 2006-09-04
> **coolclassic said:**
> Try looking in bios to adjust aperture size
I agree, try the BIOS... this [site]("http://www.techpowerup.com/articles/overclocking/vidcard/43") appears to recommend an aperture of 128MB, for all video cards from 64-256MB.

---

### Post by papuaoshi on 2006-09-04
I entirely forgot this... 

10x a lot

---

