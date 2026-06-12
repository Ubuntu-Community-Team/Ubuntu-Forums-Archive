---
title: "[SOLVED] Auto mount swap memory"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by ethoxyethaan on 2008-04-13
whenever i boot ubuntu i cant get m swap memory to be enabled.

the story: i removed my first partition (windows), and merged it with my root partition. after that my swap memory never gets switched on automatically.

**sudo fdisk -l**

Schijf /dev/sda: 80.0 GB, 80026361856 bytes
255 koppen, 63 sectoren/spoor, 9729 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0x00000080

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda2               1        2189    17583111   83  Linux
/dev/sda3            2190        2493     2441880   82  Linux wisselgeheugen
/dev/sda4            2494        9729    58123170   83  Linux

**cat /etc/fstab**

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=20654ec2-c7f2-4353-a53b-02143eb8e10a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda4
UUID=69f9a0b4-1e92-4da9-86f0-d2bbea5395ef /home           ext3    defaults        0       2
# /dev/sda3
UUID=0a4ebd39-4085-4c93-a45d-1fbd60527046 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,[color=red]noauto[/color],exec 0       0
#Added by diskmounter utility
/dev/sda1 /media/sda1 vfat rw,user,fmask=0111,dmask=0000 0 0

**ls -l /dev/disk/by-uuid/**

totaal 0
lrwxrwxrwx 1 root root 10 2008-04-13 13:25 20654ec2-c7f2-4353-a53b-02143eb8e10a -> ../../sda2
lrwxrwxrwx 1 root root 10 2008-04-13 13:25 69f9a0b4-1e92-4da9-86f0-d2bbea5395ef -> ../../sda4
lrwxrwxrwx 1 root root 10 2008-04-13 11:27 b83fedbb-ca08-4504-917e-1d040b13c4d9 -> ../../sda3

-------------------------------------------------------

ok that being said, i hate messing arround with partitions that is why im askign you guys first. 

can i just edit fstab entry "# /dev/sda3" from "noauto" to "auto"

without messing everything up.

thanks in advance.

---

### Post by joshrobinson on 2008-04-13
that noauto is in your cdrom's fstab line.. 
how do u know its not mounting?
can you post the output of
```
free
```

---

### Post by ethoxyethaan on 2008-04-13
> **joshrobinson said:**
> that noauto is in your cdrom's fstab line.. how do u now its not mounting?
can you post the output of
```
free
```

from the system monitor and from gparted (the program).
```
             total       used       free     shared    buffers     cached
Mem:       2074324     491400    1582924          0      14948     253624
-/+ buffers/cache:     222828    1851496
Swap:            0          0          0
```

(i know how to mount it but i don't know how to auto mount it on startup)

the mounted outup:

```
             total       used       free     shared    buffers     cached
Mem:       2074324     489792    1584532          0      15312     253648
-/+ buffers/cache:     220832    1853492
Swap:      2441872          0    2441872
```

---

### Post by joshrobinson on 2008-04-13
weird, theres no way that your swap partition changed names right? as in its not sda3 for some reason?

---

### Post by forestpixie on 2008-04-13
The UUID for sda3 are different they should be the same, try editing fstab to suit

from fstab
0a4ebd39-4085-4c93-a45d-1fbd60527046

from ls -l /dev/disk/by-uuid/
b83fedbb-ca08-4504-917e-1d040b13c4d9

---

### Post by joshrobinson on 2008-04-13
> **forestpixie said:**
> The UUID for sda3 are different they should be the same, try editing fstab to suit

from fstab
0a4ebd39-4085-4c93-a45d-1fbd60527046

from ls -l /dev/disk/by-uuid/
b83fedbb-ca08-4504-917e-1d040b13c4d9



even easier, remove the uuid line, and replace it with this


```
/dev/sda3   none   swap   sw   0   0
```

you should also have backed up your fstab before making changes
```
sudo cp /etc/fstab /etc/fstab.backup
```

---

### Post by ethoxyethaan on 2008-04-13
> **forestpixie said:**
> The UUID for sda3 are different they should be the same, try editing fstab to suit

from fstab
0a4ebd39-4085-4c93-a45d-1fbd60527046

from ls -l /dev/disk/by-uuid/
b83fedbb-ca08-4504-917e-1d040b13c4d9

so i switch the fstab entery on my swap to "b83fedbb-ca08-4504-917e-1d040b13c4d9" amirite?

---

### Post by forestpixie on 2008-04-13
Or follow joshrobinson - using his method will survive any further partition changes I think :) - not sure though - and he's been at it longer than I have.

---

### Post by ethoxyethaan on 2008-04-13
> **forestpixie said:**
> Or follow joshrobinson - using his method will survive any further partition changes I think :) - not sure though - and he's been at it longer than I have.

ok ill test that out, since your method dident do it job :(.

Ok Josh his method worked. 

thanks to you both.

---

