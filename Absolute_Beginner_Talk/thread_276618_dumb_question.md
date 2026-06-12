---
title: "dumb question"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by kgls13349 on 2006-10-13
Hello people,
i have just re-setup my home server, i originally setup ubuntu 6 server edition while i only had a single hdd connected, now ive connected an additional hard drive which i want to share between several users but i have no idea how to even get to it fromt he directory listing let along the path needed to share it with samba.

i originally thought that seeing as how all devices are mounted the mnt folder might have details of drives but obviously that was a waste of time ](*,) 

i know this is a stupid question but how do you navigate from one hdd to another from the command line?!?

Thank you for any help!

---

### Post by Kateikyoushi on 2006-10-13
Depends on where are your hard drives are mounted, use the cd command.

Like this
```
cd /media/hda1
```

To see where your drives are mounted check the /etc/fstab file

```
cat /etc/fstab
```

To list your partitions use.

```
sudo fdisk -l
```

---

### Post by Ben Sprinkle on 2006-10-13
In other linux distro's it's in:
/dev/mnt
or
/mnt
:)

---

### Post by kgls13349 on 2006-10-13
Thanks for the replys,

im not sure if ubuntu has actually installed my other hdd :confused:  if i look at fstab this is all it shows

/dev/hda1
/dev/hda5
/dev/hdb
/dev/fd0

the two partitions on my boot drive, my cd drive, and a floppy drive i dont have :confused: 
how come it doesnt have my second hdd there when if i boot from cd into the installer if shows both drives?

---

### Post by celeste on 2006-10-13
It's not in your fstab for one simple reason:  fstab is a list of drives which are configured to be easily mountable, and the new hard drive isn't automatically inserted into fstab for security reasons.

You need the physical address of the drive.  'less dmesg' will give you this information, just look for where the kernel looks for drives.  (yes, your system knows it's there!)

Just let us know which device it is (/dev/hd?) that's the new one, where you want it, and what you want to use it for.  We'll show you how it works :)

---

### Post by kgls13349 on 2006-10-13
Thanks, i did that and this is what ive managed to find, it lists the boot drive and DVD drive perfectly (both are IDE)

[42949377.540000] hda: ST3120022A, ATA DISK drive
[42949378.030000] hdb: TSSTcorpCDW/DVD SN-M242C, ATAPI CD/DVD-ROM drive

but the most i could find that indicated that it might know my second hdd is there is this:

[42949377.160000] sd 1:0:0:0: Attached scsi disk sda

and obviously my second hdd is sata, i dunno if that makes a difference at all??

im using ssh so i could have copied the whole thing but i thought that would be too much info ;)

Thank you

---

### Post by kgls13349 on 2006-10-13
ive been looking about and i think my second hdd is under
/dev/sda
i just need to work out how to get it mounted and then how to actually access it,

ok ive managed to enter it into fstab and such, but when trying to mount i get this

chris@xen:/media$ sudo mount sda
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

chris@xen:/media$

if its the wrong filesystem (im pretty sure its formatted to FAT32) how do i go about reformatting it so it will work?

---

### Post by kgls13349 on 2006-10-13
Ahh its ok,
ive managed to sort it out, partitioned, formatted and mounted my second hdd

and im now sharing it :mrgreen: 

Thanks for your help guys :D

---

