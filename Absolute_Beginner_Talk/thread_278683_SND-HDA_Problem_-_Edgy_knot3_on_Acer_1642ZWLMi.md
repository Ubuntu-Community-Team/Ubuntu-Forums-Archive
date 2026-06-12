---
title: "SND-HDA Problem - Edgy knot3 on Acer 1642ZWLMi"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by unlokia on 2006-10-16
Hi all!

I have an ACER ASPIRE 1642ZWLMi, and have run the livecd for:

(A) Ubuntu EDGY EFT KNOT 3 i386
(B) Kubuntu EDGY EFT KNOT 3 i386

Weird thing is this - *U*buntu has all sounds working

BUT

*K*ubuntu doesn't :(

```
root@ubuntu:~# dmesg | grep hda
[17179572.212000]     ide0: BM-DMA at 0x1810-0x1817, BIOS settings: hda:DMA, hdb:DMA
[17179572.500000] hda: HTS541080G9AT00, ATA DISK drive
[17179573.684000] hda: max request size: 512KiB
[17179573.688000] hda: 156301488 sectors (80026 MB) w/7539KiB Cache, CHS=16383/255/63, UDMA(100)
[17179573.688000] hda: cache flushes supported
[17179573.688000]  hda: hda1 hda2 < hda5 hda6 > hda3 hda4
[17179632.488000] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...

```

I hate to say this, but Mandriva 2007 managed to get it right.... what gives?!

---

