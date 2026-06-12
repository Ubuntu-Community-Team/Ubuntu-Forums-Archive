---
title: "windows root (hd1,1) cant figure out which one"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by uduntu on 2008-03-23
hello.. first I was having trouble booting ubuntu changed root to (hd1,1) and it worked.. now I cant boot windows tried too many roots (hdx,x) that I cant remember what I tried now.. so how can I figure out which (hdx,x) windows is set to 

someone asked me to paste this earler, not sure if it is useful but am pasting it here anyways

[http://paste.ubuntu-nl.org/60577/](http://paste.ubuntu-nl.org/60577/)

[http://paste.ubuntu-nl.org/60728/](http://paste.ubuntu-nl.org/60728/)

[http://paste.ubuntu-nl.org/60726/](http://paste.ubuntu-nl.org/60726/)

please help, 

thanks

---

### Post by njparton on 2008-03-23
Windows wil be on one of the NTFS partitions you listed.  You probably overwrote the MBR when you installed ubuntu - can you boot into windows using grub?

---

### Post by uduntu on 2008-03-23
njparton thanks for replying,
 
I did many things actually reinstalled ubuntu, then used fixmbr in recovery console to get windows to boot, used super grub disk to install grub the good part is I managed to get ubuntu to boot but now windows...  Error: 17 no such partition and other errors when I change (hdx,x) 

Now I just need to figure out which root (hdx,x) windows is set to and hopefully it will work

---

### Post by PmDematagoda on 2008-03-23
Please post the output of:-
```
sudo fdisk -l
```

---

### Post by uduntu on 2008-03-23
PmDematagoda, thanks for replying

might want to check the links I posted in my first post as well for /boot/grub/menu.lst and /etc/fstab


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x641fd029

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14592   117210208+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb647077e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        6528    52428127+   f  W95 Ext'd (LBA)
/dev/sdb2   *        6529       19457   103852192+   7  HPFS/NTFS
/dev/sdb5               2        6528    52428096    7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x80db80db

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         249     2000061   82  Linux swap / Solaris
/dev/sdc2   *         250        1494    10000462+  83  Linux
/dev/sdc3            1495        8982    60147360    b  W95 FAT32

---

### Post by teryowen on 2008-03-23
onto which hard drive is windows installed the 160GB one or the 120GB one?

EDIT: And type this into terminal 
```
cat /boot/grub/device.map
```
paste the output

---

### Post by uduntu on 2008-03-23
hi teryowen, thanks for replying

Windows in 160GB drive

I tried (hd0,1) and it freezes at 
Starting up...

shall I change these as well for Windows?

map		(hd0) (hd1)
map		(hd1) (hd0)

cat /boot/grub/device.map
(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdc

---

### Post by teryowen on 2008-03-23
EDIT: Nevermind leave the map and the hd0,1 is the one you need to use.

if it freeze that means there is something wrong with the windows installation, by the way i see you have NTFS on your 120GB perhaps that has windows on it. If it does and you want to boot of it, remove the map part and use hd0,0

---

### Post by uduntu on 2008-03-23
teryowen: nothing is wrong with the windows installation it used to work perfectly before I used Super Grub Disk to install Grub.. and am not sure why it shows a windows installation on 120GB, this drive was on my old pc I formatted it and using it currenly as storage only.

I would use fixmbr again to boot to windows but am afraid that if I install grub again I'd confront the same issue which impedes windows to boot

what do suggest?

---

### Post by teryowen on 2008-03-23
Does it give any error messages when you go into windows or does it just freeze up? Also do you see the whole windows logo thing and it loading?

---

### Post by uduntu on 2008-03-23
teryowen been five minutes now and all I get it a black screen and

Starting up ...

- blinking

---

### Post by uduntu on 2008-03-23
*** SOLVED ***

I just commented out ## both map lines and it no longer freezes at Starting up ...


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title		Windows NT/2000/XP (loader)
root		(hd0,1)
savedefault
makeactive
#map		(hd0) (hd1)
#map		(hd1) (hd0)
chainloader	+1

thanks everyone

---

