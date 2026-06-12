---
title: "Kam nje problem!!!!"
date: 2010-03-10
forum: Albania Team
---

### Post by artinet on 2010-03-10
Pershendetje te gjithve
Me vjen mire qe ka nje forum i ketill ne gjuhen shqipe,edhe pse pak antar ka prapse prap eshte mire,nje fillim i mire.
Problemi i im eshte ne ndamjen e particioneve,kam HDD 250giga e kam nda ne 3 pjes:2giga swap,40 giga sitem-ubuntu dhe 50 giga te shprazet,kur mar te shfrytzoj edhe 150 giga te tjera qe i kam te lire nuk mund as te krijoj particionin,me qet eror
Rezultati i fdisk -l eshte kjo
arti@arti-desktop:~$ sudo fdisk -l
[sudo] password for arti: 
Ignoring extra extended partition 3

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004fedd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4863    39062016   83  Linux
/dev/sda2            4864        5106     1951897+   f  W95 Ext'd (LBA)
/dev/sda3           11186       23343    97659135    f  W95 Ext'd (LBA)
/dev/sda4            5107       11185    48829567+   c  W95 FAT32 (LBA)
/dev/sda5            4864        5106     1951866   82  Linux swap / Solaris

Partition table entries are not in disk order

Mundsisht si te ka dikush ndonje ide se si te beje tew mundshem krijimin e particionit do ishte mire.
Me respekt Arti

---

### Post by alket on 2010-03-10
Provo GParted

Shko tek Applications/Ubuntu Software Center edhe shkruaje gparted dhe instaloje.

Programin do ta kesh tek System/Administrator.

---

### Post by ermali86 on 2010-03-10
> **artinet said:**
> Pershendetje te gjithve
Me vjen mire qe ka nje forum i ketill ne gjuhen shqipe,edhe pse pak antar ka prapse prap eshte mire,nje fillim i mire.
Problemi i im eshte ne ndamjen e particioneve,kam HDD 250giga e kam nda ne 3 pjes:2giga swap,40 giga sitem-ubuntu dhe 50 giga te shprazet,kur mar te shfrytzoj edhe 150 giga te tjera qe i kam te lire nuk mund as te krijoj particionin,me qet eror
Rezultati i fdisk -l eshte kjo
arti@arti-desktop:~$ sudo fdisk -l
[sudo] password for arti: 
Ignoring extra extended partition 3

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004fedd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4863    39062016   83  Linux
/dev/sda2            4864        5106     1951897+   f  W95 Ext'd (LBA)
/dev/sda3           11186       23343    97659135    f  W95 Ext'd (LBA)
/dev/sda4            5107       11185    48829567+   c  W95 FAT32 (LBA)
/dev/sda5            4864        5106     1951866   82  Linux swap / Solaris

Partition table entries are not in disk order

Mundsisht si te ka dikush ndonje ide se si te beje tew mundshem krijimin e particionit do ishte mire.
Me respekt Arti

Pershendetje Arti. perdor programin e sugjeruar nga babaroga dhe do ta kesh shume te thjeshte, vetem mos harro te besh nje backup te gjerave qe mund te te duhen para se te nisesh zgjerimin e particionit.

Realisht kjo qe te ka ndodhur nuk eshte problem. fdisk thjesht po te thote qe particionet nuk kane renditjen e duhur, keshtu qe mund ti lesh edhe ashtu sic jane. Megjithate nese do te rregullosh renditjen mund te perdoresh "Expert Mode" te fdisk. 

fdisk -x eshte expert mode, me pas duhet te besh fdisk -f qe eshte opsioni fix dhe ne fund shkruaj ndryshimet qe ke bere me fdisk -w. KIJ KUJDES qe mbas ketyre ndryshimeve te kontrollosh fstab dhe boot menu sepse mund te kesh kernel panic heres tjeter qe do te besh restart pc.

---

### Post by artinet on 2010-03-18
Flm ermali86,problemin tem e zgjidha,eshte interesant se si me tregojke Gdarter edhe Disk Utility krejtsisht ne kundershtim me njeri tjetrin vinin,por me fdsik e zgjidha problemin,Screnshotat ende i kam te ruajtuna te cilat do ti dergoj ketu te shifni.Babaroga flm edhe prej teje.kete problem edhe ne irc ubuntu e paraqita por sme dhan asnje zgjidhje se si te ndreqi.Pike se pari me vjen mire qe ka edhe shqiptar qe perdorin Ubuntun e qe ka me kend te komunikoj ne lidhje me linuxin.Do ju dergoj screnshotat qe kam bere masi paska opcion per ti dergu...
Me respekt Artinet

---

