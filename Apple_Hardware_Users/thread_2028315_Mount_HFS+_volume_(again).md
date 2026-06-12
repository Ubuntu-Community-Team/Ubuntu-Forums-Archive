---
title: "Mount HFS+ volume (again)"
date: 2012-07-18
forum: Apple Hardware Users
---

### Post by freget on 2012-07-18
Dear all,

sorry to bother you with another HFS+ thread - I had a good look through old threads and did not see a solution that seemed appropriate to my problem.

Everything I write probably would reduce to rephrasing the terminal outputs while discarding information. Thus, I will just give you the commands I did run:

```

> sudo mount -t hfsplus /dev/sdc2 Home
mount: wrong fs type, bad option, bad superblock on /dev/sdc2,
       missing codepage or helper program, or other error

``````

> dmesg | tail
[37378.162380] mount: sending ioctl 5310 to a partition!
[37378.162382] mount: sending ioctl 5310 to a partition!
[37378.181290] hfs: invalid secondary volume header
[37378.181294] hfs: unable to find HFS+ superblock

``````

> sudo parted -l
[...]
Modell: ATA ST3000DM001-9YN1 (scsi)
Festplatte  /dev/sdc:  3001GB
Sektorgröße (logisch/physisch): 512B/4096B
Partitionstabelle: gpt

Nummer  Anfang  Ende    Größe   Dateisystem  Name                  Flags
 1      20,5kB  210MB   210MB   fat32        EFI System Partition  boot
 2      210MB   3000GB  3000GB  hfs+         Daten
[...]

``````
> sudo fsck -f /dev/sdc2
fsck von util-linux 2.20.1
** /dev/sdc2
[...]
** The volume Home appears to be OK.
```Journaling is enabled on the volume, I'm running the pengolin with all available updates installed. Mounting via the Gui does result in identical problems.

Thanks for your thoughts!

---

