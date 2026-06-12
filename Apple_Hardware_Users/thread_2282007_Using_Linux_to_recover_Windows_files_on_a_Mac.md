---
title: "Using Linux to recover Windows files on a Mac"
date: 2015-06-11
forum: Apple Hardware Users
---

### Post by anlag on 2015-06-11
Lovely title, isn't it?

So, I have in front of me a Macbook Air with a dual installation of OS X and Windows 7, where the latter system has become infected by malware. My objective is to recover, from that Windows system, a directory with user files, without the risk of said malware spreading to a removable media used to copy the files. My go-to method to do this would be to boot the machine to a Linux live CD/USB, which I have managed to do. It took installing rEFInd on the OS X before I could see the Xubuntu USB drive, but so far, so good.

The problem is that once I'm inside the Xubuntu live desktop, I am unable to mount the NTFS partition that Windows resides on. Whether double-clicking the desktop icon or trying to mount it through a command line,

> mount -t ntfs /dev/sda4 /mnt

...I get the same error message, namely: 

> Failed to read last sector (165488639): Invalid argument. 

The desktop shortcut mount uses more mount options, but the error thrown is the same.

I'm wondering if this is to do with the Macbook using a GPT partition table rather than MBR, or possibly, if I might have caused this issue by installing rEFInd. I haven't tried doing this on Mac hardware before, so I'm not quite sure what to expect. However, the Windows system does seem to be intact, at least to the point that I can boot it into safe mode with no networking, log in there with a local account, and verify that the files are still there.

Lastly, I suppose I could skirt the problem by extracting the directory from the OS X installation rather than going the Linux route. I tried, briefly, but most or all files in the directory throw input/output errors when accessed via the OS X terminal, making me think I'm missing some NTFS support there. And either way, I'm rather partial to the Linux route, being also interested in using it for other situations in the future.


Some data:

> (parted) unit s                                                           
(parted) print                                                           
Model: ATA APPLE SSD SM128E (scsi)
Disk /dev/sda: 236978176s
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start      End         Size       File system  Name                  Flags
 1      40s        409639s     409600s    fat32        EFI System Partition  boot
 2      409640s    69952183s   69542544s  hfs+         Mac HD
 3      70214328s  71483863s   1269536s   hfs+         Recovery HD
 4      71485440s  130893823s  59408384s  ntfs         WINDOWS               msftdata


> root@xubuntu:~# gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: hybrid
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with hybrid MBR; using GPT.
Disk /dev/sda: 236978176 sectors, 113.0 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 29FF994C-8F8A-4F19-8223-D65D89951E8B
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 236978142
Partitions will be aligned on 8-sector boundaries
Total free space is 106348045 sectors (50.7 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI System Partition
   2          409640        69952183   33.2 GiB    AF00  Mac HD
   3        70214328        71483863   619.9 MiB   AB00  Recovery HD
   4        71485440       130893823   28.3 GiB    0700  WINDOWS


> root@xubuntu:~# mount -t ntfs-3g /dev/sda4 /mnt
Failed to read last sector (165488639): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sda4': Invalid argument
The device '/dev/sda4' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?


---

### Post by SeijiSensei on 2015-06-11
Can OS X mount the NTFS partition?  Surely that would be the easiest solution.

---

### Post by anlag on 2015-06-12
OS X can mount the NTFS partition, but the directory I want to recover shows as empty in the Finder, and when attempting an ls in the terminal, I can see the subdirectories but they all produce the infamous input/output error. My first thought was the drive hadn't mounted properly, but I can see and open various other files on it, so it's specifically those files, perhaps a matter of ownership or permissions. One natural suspicion would of course be that the drive is broken or the files corrupt, but they work fine in Windows safe mode. 

I'll see if I can get the material accessible by poking around with ownership in Windows, before rebooting into OS X. Failing that I guess I can fall back on copying the files to a pen drive via Windows and simply put it through ClamAV or whatever scans on a live Linux system, before it's allowed in contact with other Windows machines. It feels less secure than recovering the files through another system, but it may have to do.

---

### Post by este.el.paz on 2015-06-12
Can't get into this problem too deeply right now, but I have spent a lot of time using dual-boot apple/linux systems . . . but, from listening to people who use windows, isn't there a "history" feature that lets you re-set windows to a time **before** the malware??  And, then you could copy your files to the pendrive as you suggest as the solution?

rEFInd should not be causing problems, for my experience OSX doesn't seem to mount other systems, linux **might** be able to do what you are trying, but probably easiest is your pendrive idea with the clamav clean, and then nuke the windows install and do a clean re-install of it . . . .

e..

---

