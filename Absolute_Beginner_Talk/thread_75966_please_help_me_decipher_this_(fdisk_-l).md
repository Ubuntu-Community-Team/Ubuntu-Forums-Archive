---
title: "please help me decipher this (fdisk -l)"
date: 2005-10-14
forum: Absolute Beginner Talk
---

### Post by onesojourner on 2005-10-14
I am trying to find a harddrive that is formatted with ntfs. it is a 160g with about 12g free.  when I do the fdisk -l command in terminal this is what i get
----------------------------------------------------------
peter@peterLinux:~$ fdisk -l

Disk /dev/sda: 524 MB, 524025856 bytes
17 heads, 59 sectors/track, 1020 cylinders
Units = cylinders of 1003 * 512 = 513536 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?      775809     1913904   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(775808, 8, 13)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(1913903, 14, 4)
Partition 1 does not end on cylinder boundary.
/dev/sda2   ?      168185     2098423   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(168184, 16, 27)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(2098422, 8, 24)
Partition 2 does not end on cylinder boundary.
/dev/sda3   ?     1864289     3794527   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(1864288, 10, 12)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(3794526, 1, 20)
Partition 3 does not end on cylinder boundary.
/dev/sda4   ?           1     3626348  1818613248    d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(0, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(3626347, 7, 42)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
peter@peterLinux:~$
----------------------------------------------------------------------------------------
I dont really understand this. I followed the directions here 
[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows) and that mounted my windows partition. I still have others I would like to mount. to mount the windows partition I typed exactly what it said

sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

I'm not sure what I needed to change so this is what I did

sudo mkdir /media/[COLOR="Red"]otherdirve[/COLOR]
sudo mount /dev/[COLOR="Red"](and I changed this to lots of different things like sda3 because of what the fdisk -l said, I also tried hda2 hda3 ect..) [/COLOR]/media/[COLOR="Red"]otherdrive[/COLOR]/ -t ntfs -o nls=utf8,umask=0222

mount: special device /dev/hda4 does not exist

or 

mount: wrong fs type, bad option, bad superblock on /dev/hda2,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I typed dmesg and I still dont see a list of the drives I want to mount. Is there a write up on mounting mutiple drives? If I could just find my 160 gig I would be happy for now.

---

### Post by towsonu2003 on 2005-11-24
sorry, I can't help, but:[QUOTE=onesojourner]This doesn't look like a partition table
Probably you selected the wrong device.[/QUOTE]I agree... + so many partitions in 524MB doesn't look right... try ```
fdisk -l /dev/hda
```

---

