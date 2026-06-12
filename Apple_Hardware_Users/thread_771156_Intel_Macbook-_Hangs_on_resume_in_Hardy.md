---
title: "Intel Macbook- Hangs on resume in Hardy"
date: 2008-04-27
forum: Apple Hardware Users
---

### Post by Rog-Mahal on 2008-04-27
My 3rd. Gen Macbook (not the Santa Rosa model) has been having some new issues related to suspend/resume that didn't appear in Gutsy. 

Generally two things happen, and it's about 50-50 in terms of frequency:

Either it just hangs and the keyboard appears dead and I have to hard reboot or I get the following message (which I got from dmesg) and it takes about 15 seconds to get my login prompt:

```
[    2.319388] ata3.01: revalidation failed (errno=-2)

```

That message shows up by itself, the entire dmesg section that seems to be related to resuming is:

```
[    1.740099] sd 2:0:1:0: [sda] Starting disk
[    2.319388] ata3.01: revalidation failed (errno=-2)
[    2.319389] ata3: failed to recover some devices, retrying in 5 secs
[    3.620806] ata3.01: ACPI cmd ef/03:0c:00:00:00:b0 filtered out
[    3.620809] ata3.01: ACPI cmd ef/03:45:00:00:00:b0 filtered out
[    3.623296] ata3.01: configured for UDMA/100
[    3.624177] sd 2:0:1:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    3.624199] sd 2:0:1:0: [sda] Write Protect is off
[    3.624202] sd 2:0:1:0: [sda] Mode Sense: 00 3a 00 00
[    3.624231] sd 2:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.670057] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[    3.671472] PM: Finishing wakeup.

```

Any ideas? It seems like my hdd is failing to be woken up sometimes.

---

### Post by anat on 2008-09-05
hi!

i get the same "revalidation failed" error message everytime i try to wake up my macbook (first generation), but it works everytime. it takes em almost half a minute to wake up, but it works.

maybe someone knows why it is sooo slow/ it doesn't work at all.

---

### Post by cyberdork33 on 2008-09-05
> **anat said:**
> hi!

i get the same "revalidation failed" error message everytime i try to wake up my macbook (first generation), but it works everytime. it takes em almost half a minute to wake up, but it works.

maybe someone knows why it is sooo slow/ it doesn't work at all.
Intrepid will be released soon. If it gives the same errors, I would file a bug.

---

### Post by anat on 2008-09-20
good news here!

i upgraded to 8.10 alpha 6: it works!

---

