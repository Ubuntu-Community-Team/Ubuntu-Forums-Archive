---
title: "DVD does not mount desperately need help."
date: 2013-05-04
forum: Any Other OS
---

### Post by codingman on 2013-05-04
I have automount enabled, but it does not work for disks. I have tried mounting manually, but then it gives me an error saying: 
mount: /dev/sr0 is write-protected, mounting read only.
mount: /dev/sr0: can't read superblock.

I am trying to burn a .iso file to a blank DVD. I cannot see this disk in any way. 

Thanks in advance,
Codingman

---

### Post by codingman on 2013-05-04
Here is the output of dmesg | tail:
[  242.850541] sr 1:0:0:0: [sr0]  
[  242.850545] Result: hostbyte=0x00 driverbyte=0x08
[  242.850548] sr 1:0:0:0: [sr0]  
[  242.850549] Sense Key : 0x5 [current] 
[  242.850553] Info fld=0x0
[  242.850554] sr 1:0:0:0: [sr0]  
[  242.850556] ASC=0x21 ASCQ=0x0
[  242.850558] sr 1:0:0:0: [sr0] CDB: 
[  242.850559] cdb[0]=0x28: 28 00 00 00 00 00 00 00 01 00
[  242.850601] FAT-fs (sr0): unable to read boot sector

It appears to be that the dvd is oddly sr0...

---

### Post by codingman on 2013-05-04
I used the command:
```
sudo mount -o ro /dev/sr0 /mnt/media
```
and got the error:
```
mount: /dev/sr0: can't read superblock
```
Anybody have the same issue or have a fix for this?

---

### Post by mips on 2013-05-05
do you have gvfs etc installed

---

