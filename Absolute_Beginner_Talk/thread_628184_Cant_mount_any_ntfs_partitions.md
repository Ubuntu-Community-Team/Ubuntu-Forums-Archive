---
title: "Cant mount any ntfs partitions"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by Jormanks on 2007-12-01
Wll, hi... I have 3 HD where 2 of them are SATA, and they have 6 altogether... the problem is that when i loaded the live cd all the partitions were mounted and now, after installing, Ubuntu only mounts one drive...

whata can i do?

---

### Post by joku_muko on 2007-12-01
Look for Storage Device Manager in the repository.

---

### Post by FuturePilot on 2007-12-01
Try installing the ntfs-config package. Then you can configure access to the drives.
```
sudo apt-get install ntfs-config
```

---

### Post by Jormanks on 2007-12-01
did it already and no luck

here, i dont understand very well this, hope anyone can help me:

[PHP]sudo fdisk -l

Disco /dev/sda: 320.0 GB, 320072933376 bytes
255 cabezas, 63 sectores/pistas, 38913 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Disk identifier: 0xfc920b67

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1               1        6375    51207156    7  HPFS/NTFS
/dev/sda2            6376       38913   261361485    f  W95 Ext'd (LBA)
/dev/sda5            6376       16819    83891398+   7  HPFS/NTFS
/dev/sda6           16820       27263    83891398+   7  HPFS/NTFS
/dev/sda7           27264       38913    93578593+   7  HPFS/NTFS

Disco /dev/sdb: 163.9 GB, 163928604672 bytes
255 cabezas, 63 sectores/pistas, 19929 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Disk identifier: 0xf976edb9

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   *           1       19929   160079661   42  SFS

Disco /dev/hda: 20.0 GB, 20020396032 bytes
255 cabezas, 63 sectores/pistas, 2434 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Disk identifier: 0x1fb01faf

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/hda1   *           1        1127     9052596    c  W95 FAT32 (LBA)
/dev/hda2            1128        1370     1951897+  82  Linux swap / Solaris
/dev/hda3            1371        2434     8546580   83  Linux
[/PHP]

---

### Post by monte48lowes on 2007-12-01
If you have NTFS drives due to dual booting with windows, boot into windows and perform a normal shut down. Then restart into ubuntu. Check if the problem is still there.

Mike

---

### Post by Jormanks on 2007-12-01
No, nothing happens.

As i understand Ubuntu detects the HDs, but does not mount them.

...



Help!

---

