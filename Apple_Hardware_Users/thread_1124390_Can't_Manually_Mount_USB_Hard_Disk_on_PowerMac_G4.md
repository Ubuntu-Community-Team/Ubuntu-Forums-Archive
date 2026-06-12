---
title: "Can't Manually Mount USB Hard Disk on PowerMac G4"
date: 2009-04-13
forum: Apple Hardware Users
---

### Post by jevchance on 2009-04-13
Hello everyone.

I'm running a PowerMac G4 (PPC) and I can't mount a USB hard disk. I suspect it might be the lack of support for an EFI partition map, but I'm not sure.

The USB controller recognizes the drive fine, but when I try to mount the partition I get a message "mount: special device /dev/sdc2 does not exist".

Here are some commands/output:

```
:~$ sudo parted /dev/sdc
GNU Parted 1.7.1
Using /dev/sdc
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) p 

Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number Start End Size File system Name Flags
1 20.5kB 210MB 210MB fat32 EFI System Partition boot 
2 210MB 1000GB 1000GB hfs+ Untitled 

(parted) q 
Information: Don't forget to update /etc/fstab, if necessary. 

:~$ sudo mount -t hfsplus /dev/sdc2 /mnt/backup
mount: special device /dev/sdc2 does not exist

:~$ sudo dmesg | tail
[292820.382482] sd 3:0:0:0: [sdc] Mode Sense: 23 00 00 00
[292820.382492] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[292820.385199] sd 3:0:0:0: [sdc] 1953525168 512-byte hardware sectors (1000205 MB)
[292820.386575] sd 3:0:0:0: [sdc] Write Protect is off
[292820.386593] sd 3:0:0:0: [sdc] Mode Sense: 23 00 00 00
[292820.386603] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[292820.386620] sdc: sdc1
[292820.401091] sd 3:0:0:0: [sdc] Attached SCSI disk
[292820.401244] sd 3:0:0:0: Attached scsi generic sg2 type 0
[293954.798423] hfs: unable to find HFS+ superblock
```

Its this last line in the dmesg that concerns me. I'm thinking that Linux can't read the partition table. Can anyone confirm?

---

### Post by cyberdork33 on 2009-04-13
Are you sure this disk has an EFI partition map? nvm I see.

What does 'sudo fdisk -l /dev/sdc' show? This might be an issue with the MBR partition map not being in sync with the GPT (though it shouldn't have to be).

---

