---
title: "Can you mount a physical hard drive in qemu?"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by Angus77 on 2008-01-30
I wanted to try and remaster Knoppix without stopping my torrents, so I thought I'd run Knoppix using qemu.  I can't figure out how to mount any of my physical drive partitions from Knoppix inside qemu, though.  Is it not allowed?

---

### Post by aeiah on 2008-01-30
im not sure about qemu specifically, but usually with virtual machines, physical drives and partitions on the host are mounted as network drives on the guest, using a virtual network which was probably set up my qemu automatically to allow internet access as well as what you're after

---

### Post by emarkd on 2008-01-30
Not sure about qemu; I've never used it for this.  But VMWare will boot a physical partition or drive.

---

