---
title: "How to mount other HDD's from Wubi?"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by Gripp on 2007-11-25
i have kubuntu through wubi installed and i can see my c: drive in /media/host
but i can not see any of my HDD's 

listing fdisk gives
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14593   117218241    7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14588   117178078+   7  HPFS/NTFS

Disk /dev/sdc: 180.0 GB, 180045766656 bytes
255 heads, 63 sectors/track, 21889 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes


so they are there
just not mounted...
its been a year or so since i've messed with linux, 
and given that i'm in a virtual drive... i want to get help before jumping 



ps
cat /etc/fstab
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults          0   0
/media/host/wubi/disks/system.virtual.disk      /               ext3        loop,sync         0   1
/media/host/wubi/disks/home.virtual.disk      /home           ext3        loop,sync         0   2
/media/host/wubi/disks/swap.virtual.disk      none            swap        sw                0   0


and 
mount
/media/host/wubi/disks/system.virtual.disk on / type ext3 (rw,sync)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/media/host/wubi/disks/home.virtual.disk on /home type ext3 (rw,sync,loop=/dev/loop1)

---

### Post by Gripp on 2007-11-25
okay
trying to be adventurous got me nowhere

sudo mount -t ntfs /dev/sdc /media/F_Drive/
mount: wrong fs type, bad option, bad superblock on /dev/sdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


so, no
not so easy

---

### Post by Gripp on 2007-11-25
i should add
i dont really want to be able to write to the NTFS drive for fear of curropting my drives
so the Ntfs-3G solution is a last resort

i just simply want to mount a read only ntfs HD...

---

### Post by meierfra on 2007-11-25
> Disk /dev/sdc: 180.0 GB, 180045766656 bytes
255 heads, 63 sectors/track, 21889 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

It seems that sdc is not formated. Otherwise there would be at least one partition (sdc1) on sdc.


> sudo mount -t ntfs /dev/sdc /media/F_Drive/

You cannot mount a hard drive. Only partitions can be mounted.  For example you should be able to mount "sdb1" via

```
sudo mount -t ntfs /dev/sdb1 /media/Some_Drive/
```

But I don't know much about wubi, so I'm not sure it will work,

---

### Post by Gripp on 2007-11-25
i'm not in linux atm - but i do recall some "files" with 1 at the end (it seems like it was like sbc.1 though, but i might be mistaken - i'll let you know when i get back into linux)
but i do know that all of those were showing as 0kb in size (even the partition i'm mounted to) when looking at it through konquerer (sp? lol..)

they are all formatted though - mostly full even
so if the drives aren't partitioned - how to make them appear to be without actually partitioning them? some way of just telling linux to treat it as a partition?

not risking my windows install is the whole reason i went with wubi... i moved and lost track of my winblows disk/key (at least i think that's when it grew legs...) and realllly dont want to have to either pay for it again or deal with the whole genuine crap
my hope is that by the time i would otherwise need to re-install windows *again* i will be comfortable enough with linux that i simply wont... :)

---

