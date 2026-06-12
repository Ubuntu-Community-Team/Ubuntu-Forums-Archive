---
title: "problem with ntfs partition"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by pecoronas on 2007-05-15
suddenly, after a reboot, i have "lost" my settings on a ntfs partition.
it was correctly configured in fstab and used to work perfectly, now it appears to be "read only".

this is my sudo fdisk -l:

```
okapi@okapi-desktop:~$ sudo fdisk -l

Disk /dev/hda: 10.1 GB, 10110320640 bytes
255 heads, 63 sectors/track, 1229 cylinders
Units = cilindri of 16065 * 512 = 8225280 bytes

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1171     9406026   83  Linux
/dev/hda2            1172        1229      465885    5  Esteso
/dev/hda5            1172        1229      465853+  82  Linux swap / Solaris

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cilindri of 16065 * 512 = 8225280 bytes

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            1913       14946   104695605    f  W95 Ext'd (LBA)
/dev/sda5            1913       14946   104695573+   7  HPFS/NTFS
```

ntfs-config can't see the partition unless i comment the line about it in fstab. but even then, i get this error in ntfs-config:

```
okapi@okapi-desktop:~$ sudo gedit /etc/fstab
okapi@okapi-desktop:~$ sudo ntfs-config

(ntfs-config:6359): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Errore alla riga 3 carattere 13: È stato chiuso l'elemento "markup", ma l'elemento correntemente aperto è "b"

** (ntfs-config:6359): WARNING **: Failed to create /media/DATI.


** (ntfs-config:6359): WARNING **: Errore: E' occorso un errore durante il tentativo di configurazione di
 /media/DATI. Ritenta, grazie.


(ntfs-config:6359): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Errore alla riga 3 carattere 13: È stato chiuso l'elemento "markup", ma l'elemento correntemente aperto è "b"

(ntfs-config:6359): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Errore alla riga 3 carattere 13: È stato chiuso l'elemento "markup", ma l'elemento correntemente aperto è "b"

(ntfs-config:6359): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Errore alla riga 3 carattere 13: È stato chiuso l'elemento "markup", ma l'elemento correntemente aperto è "b"
```

this is my fstab (last line, sda5, here not commented, is the partition i have "lost"):

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=ae48e046-6485-4a0d-8eb4-d83841dd2f8b /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=13868999-bddc-4c09-ad72-4454965e79f8 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

#/dev/sda5
/dev/sda5       /media/DATI     ntfs-3g silent,umask=0,locale=it_IT.utf8 0 0
```

please help me, that's the partition with ALL OF MY DATA!!!

---

### Post by nightskywind83 on 2007-05-15
I could be wrong because I'm *somewhat* of a Linux noob myself, but in reviewing your fstab file, I believe the umask option on your ntfs line should have a 4-digit value assigned.

I mount my NTFS partition readonly, and this is the line I use in my fstab:

/dev/hda1 /media/windows ntfs ro,nls=utf8,umask=0222 0 0

See this page for more information, it may prove helpful:

[https://help.ubuntu.com/community/MountNtfsOnBoot](https://help.ubuntu.com/community/MountNtfsOnBoot)

---

### Post by Bakerman on 2007-05-16
Have you checked that the mountpoint folder /media/DATI has read/write access enabled? By default only root would have write access to this folder. You may need to modify the permissions to allow for normal user write access.

I believe the code you could use to set the user permissions would be:

sudo chmod -R a+rwx /media/DATI
 
This would give the mountpoint folder recursive read/write/executable access for all users again.

---

