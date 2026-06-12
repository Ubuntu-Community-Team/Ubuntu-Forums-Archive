---
title: "Grub Error 17"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by bldgengineer on 2008-03-19
Tried doing as others had suggested but nothing seems to work. I can load from the live cd and when I do and try to access the ubuntu volume from the home folder I get this:

```
$Logfile indicates unclean shutdown (0,0) Failed to mount '/dev/sda1': Operation not supported Mount is denied because NTFS is marked to be in use. 
Choose one action: 
Choice 1: if you have windows then disconnect external devices by clicking on the safely remove hardware icon in the windows taskbar then shutdown windows cleanly.
 Choice 2: if you don't have windows then you can use the 'force' option for you own responsibility.
 For example  type the command line: Mount -t ntfs-3g /dev/sda1/media/disk -o force Or add the option to the relevant row in the /etc/fstab file: /dev/sda1/media/disk ntfs-3g defaults,force 0 0 
```

here is my device.map - 

```
(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
```

and my fdisk - 

```
Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x78c778c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9120    73256368+   7  HPFS/NTFS
/dev/sda2            9121       11552    19535040   83  Linux
/dev/sda3           11553       11795     1951897+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x79047904

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001    c  W95 FAT32 (LBA)

```

TIA for any help!

---

### Post by bumanie on 2008-03-19
Try 
> sudo grub
> > root (hd0,1)
> > setup (hd0)
> > quit
If that doesn't work, go here [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
Very informative guide on all aspects of grub

---

### Post by bldgengineer on 2008-03-19
I get to "setup (hd0)" and receive:

```
Error 17: Cannot mount selected partition
```

nothing in the troubleshooting section of that website has helped either :(

---

### Post by bumanie on 2008-03-19
Go to the link above and look up grub error 17. Also you could try super grub disc. A link to it is also on that page.

---

### Post by bldgengineer on 2008-03-19
how do you burn SBD if you can;t load windows and the only way to load ubuntu is with the live cd in your only cd rom drive?

---

### Post by bldgengineer on 2008-03-19
I was able to get SBD onto a USB drive and started windows with it but if I try to start ubuntu I get an error 13 halfway through loading.

How can I use SBD to fix my boot from the HDD?

---

### Post by bldgengineer on 2008-03-19
nothing I tried in super grub disk seems to be working....

I forgot to mention that I did check my hdd in bios and it is set to "auto"

---

### Post by bldgengineer on 2008-03-20
As an update, its seems I no longer have grub at all and I'm loading straight to windows now. Anybody know what might be going on?

---

