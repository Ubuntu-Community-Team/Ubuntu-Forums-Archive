---
title: "How do I get my hd specs?"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by ricardisimo on 2007-01-26
I know that I could just restart my comp and read the startup info really fast, but clearly there has to be another way to do it in a terminal or GUI. What command line would give me all of the pertinent specs on my hard drive(s) and removables, etc. As to the GUI option, why does computer:/// list my drives, but doesn't really give any useful info about them? I guess I'm thinking along the lines of "Properties" on "My Computer" in Windows. Does anyone know if that has been discussed as an option for Feisty? Thanks in advance.

---

### Post by taurus on 2007-01-26
```
dmesg | more
```
(Hit the Space bar for the next 24 lines.)

Or

```
sudo fdisk -l
```

---

### Post by jbayone on 2007-01-26
I think hardinfo works too for that

---

### Post by ricardisimo on 2007-01-26
```
hda: max request size: 128KiB
hda: 80293248 sectors (41110 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(133)
hda: cache flushes supported
hda: hda1 hda2 < hda5 >
```
I'm not sure what the first line means, but the second line is telling me that I have a 40G UDMA, correct? UDMA is the type of disk? And if I want to add another disk to my comp, would I be wise to get another like this one? Thanks.
By the way, jb, what is hardinfo? Is that code?

---

### Post by kosmic on 2007-01-26
sudo fdisk -l (it is an L) will give you something like this :

[I][B]Disc /dev/hda: 120.0 GB, 120034123776 bytes
255 cabeças, 63 setores/trilha, 14593 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
[/B][/I]
Dispositivo Boot Início Fim Blocos Id Sistema
/dev/hda1   *           1        3187    25599546    7  HPFS ou NTFS
/dev/hda2            3188       14593    91618695    f  Win95 (LBA) Partição Extendida
/dev/hda5            3188        5992    22531131    7  HPFS ou NTFS
/dev/hda6            5993        7344    10859908+   7  HPFS ou NTFS
/dev/hda7            7345        7375      248976   82  Linux swap / Solaris
/dev/hda8            7376        8652    10257471   83  Linux
/dev/hda9            8653       11602    23695843+  83  Linux
/dev/hda10          11603       14593    24025176    7  HPFS ou NTFS

Disco /dev/hdb: 15.3 GB, 15367790592 bytes
16 cabeças, 63 setores/trilha, 29777 cilindros
Unidades = cilindros de 1008 * 512 = 516096 bytes

---

