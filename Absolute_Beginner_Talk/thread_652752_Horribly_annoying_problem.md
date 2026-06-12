---
title: "Horribly annoying problem"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by BackBack on 2007-12-29
I know that you get this question a lot because I've read quit a few of them in hopes of finding an answer, but nothing has worked so far. I'm trying to open the external HDD, and of course it doesn't, and says unable to mount.  Here's the information I've seen others ask for:

lsusb -
```

Bus 002 Device 002: ID 062a:0201 Creative Labs 
Bus 002 Device 003: ID 058f:9360 Alcor Micro Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 4971:ce03  
Bus 001 Device 004: ID 058f:6387 Alcor Micro Corp. 
Bus 001 Device 003: ID 13b1:000e Linksys 
Bus 001 Device 001: ID 0000:0000  

```

fdisk -l -
```

  Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1       60801   488384001    7  HPFS/NTFS

```

Please help me out :/

---

### Post by PmDematagoda on 2007-12-29
Did you try mounting it manually? What is the mounting error you get?

---

### Post by BackBack on 2007-12-29
"Unable to mount the volume 'SimpleDrivePS'." when I try to right-click mount.  Not too sure how I'd do it manually :/

---

### Post by PmDematagoda on 2007-12-29
Here is how you can manually mount a drive:-

1) Make a directory in /media by executing(You may replace "disc" with any other word you may want):-
```
sudo mkdir /media/disc
```

2) Mount the drive using:-
```
sudo mount -t ntfs-3g /dev/sdg1 /media/disc
```

If you get any error, please post it completely.

---

### Post by BackBack on 2007-12-29
```

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdg1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdg1 /media/HDD -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdg1 /media/HDD ntfs-3g defaults,force 0 0

```

---

### Post by PmDematagoda on 2007-12-29
Ok, now execute this command(As suggested by the error):-
```
sudo mount -t ntfs-3g /dev/sdg1 /media/disc -o force
```

That should fix your problem.

---

### Post by BackBack on 2007-12-29
Holy hell, thanks a lot. I've tried the same command, but with a different directory name as on other threads, but it didn't work. Anywho, thanks a lot!

---

### Post by hums07 on 2007-12-29
You may have used the harddisk before with Windows (or other OS), then you put Windows in hibernate mode which left the harddisk "in use".

While using the "-o force" option may be ok, it is not recommended if you have a chance to make your previous system properly shut down. I mean, attach your harddisk to your Windows, remove it properly or shut it down. Then you should get an automount harddisk when rebooting to Ubuntu.

---

### Post by BackBack on 2008-01-25
Hate to be annoying, but I installed Ubuntu on another machine, and the commands don't work now. When I try to to mount with either of the two commands, I get a message saying, "Failed to access '/dev/sdg1': No such file or directory." Any help?

---

### Post by PmDematagoda on 2008-01-25
Please post the output of:-
```
sudo fdisk -l
```

---

### Post by smurphy_it on 2008-01-25
Do as PmDematagoda recommended and type fdisk -l

It might not be sdg1 on the other machine, it's probably called by a different name... Just substitute that name in your mount command.

---

### Post by BackBack on 2008-01-25
```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17347   139339746    7  HPFS/NTFS
/dev/sda2           17348       29967   101370150    5  Extended
/dev/sda5           17348       29905   100872103+  83  Linux
/dev/sda6           29906       29967      497983+  82  Linux swap / Solaris

Disk /dev/sdb: 524 MB, 524286976 bytes
17 heads, 59 sectors/track, 1020 cylinders
Units = cylinders of 1003 * 512 = 513536 bytes
Disk identifier: 0x73696420

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?     1914209     2457017   272218546+  20  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(356, 97, 46) logical=(1914208, 5, 40)
Partition 1 has different physical/logical endings:
     phys=(357, 116, 40) logical=(2457016, 16, 59)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?     1326206     1863570   269488144   6b  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 110, 57) logical=(1326205, 9, 57)
Partition 2 has different physical/logical endings:
     phys=(269, 101, 57) logical=(1863569, 13, 16)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?      537378     1931558   699181456   53  OnTrack DM6 Aux3
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(345, 32, 19) logical=(537377, 4, 25)
Partition 3 has different physical/logical endings:
     phys=(324, 77, 19) logical=(1931557, 10, 42)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   *     1390457     1390478       10668+  49  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(87, 1, 0) logical=(1390456, 5, 1)
Partition 4 has different physical/logical endings:
     phys=(335, 78, 2) logical=(1390477, 9, 38)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

```
That would be the message I get with the suggested command.

---

### Post by PmDematagoda on 2008-01-25
Can you do a scandisk check on the hard drive and post the results of fdisk -l again.

---

### Post by BackBack on 2008-01-25
To be honest with you, I have no idea how I would go about doing that, and I can't seem to find a place that explains :/

---

### Post by BackBack on 2008-01-26
By the way, could this have been caused because I have Windows as my second partition? Though it was working for a day or two, then just stopped recognizing all together, though even WinXP on VMware had no problem with it.

---

