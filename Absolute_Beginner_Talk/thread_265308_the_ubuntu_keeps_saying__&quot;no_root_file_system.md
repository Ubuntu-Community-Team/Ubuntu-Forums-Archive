---
title: "the ubuntu keeps saying : &quot;no root file system&quot; at installation"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by itisgood on 2006-09-25
hi everyone, nice to meet to you all.

i have just started to install ubuntu to my pc, while i also have winxp installed.

i have used  <Acronis Disk Director Suit> to patition my harddisk, and in that program i see 5 disks perfected partitioned and formatted, 
C:  NTFS primary active
D:  FAT32 logical
E:  FAT32 logical     
Ex3 linux ex3 primary    2.6 GB
Linux swap               564 MB

but in ubuntu when i boot from the disk and start the installation, it shows that i have only one partition of 37 GB (thats the right number for the size of my whole hardisk) **unallocated**

then if i click 'proceed', it will bring me to 5/6 showing me that it choose to assign "/" to 'Ex3', and "swap" to 'linux swap'.
that is quite the thing i wanted.
but then i press install, it will pop out an error message sayint " no root file system ", then stop the installation.

i have been spending a whole night working on this problem but i cant solve it. 
does anyone know what is actually going wrong and how should i fix it. 
any ideas would be appreciated
thx a lot

---

### Post by xpod on 2006-09-25
Mabey just deleting the 2 linux partitions and leaving them as one unallocated space then just running the installer and pointing it to that empty space and letting it do it all itself would work better??

Seems like one lot of the common advice.

Goodnight and good luck:D

EDIT: not sure about the rest..hope you fix it

---

