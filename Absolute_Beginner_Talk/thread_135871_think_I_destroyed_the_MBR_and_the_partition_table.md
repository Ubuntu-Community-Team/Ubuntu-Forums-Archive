---
title: "think I destroyed the MBR and the partition table"
date: 2006-02-24
forum: Absolute Beginner Talk
---

### Post by ninjasmith on 2006-02-24
ok my computer is very ill at the moment.  for a while it would let my boot into two flavours of windows and ubuntu.  however when messing around with a spare partition of space I ended up trying to delete this partiton from inside windows.  now grub won't load.

I have tried rescuing GRUB but cant mount a hard drive when in rescue mode.

more worryingly when I put in ubuntu cd try and reinstall and manuallly edit partition table it whos no partitions on my second harddrive where there should be about 5.???  if i boot into the rescude disk of norton ghost it still shows my two windows partitions?  so it seems to me that I may have remove the MBR and partiton table.

can anyone help?  reallly dont want to reformat this drive and install three os's again

---

### Post by ninjasmith on 2006-02-24
ok norton ghost has the ability to view and edit the partition table.  it can also restore the master boot record.

when i view the partition taable there is all kind of crap in there and also the partitions that I recogonise.  there are also errors which are a bt comliacted to type in but seems t refer to the start and end point of partitions....

if I restore MBR on the drive will it just allow me to boot back into windows(via boot.ini) and then I can try and fix the partitions from there?

or should I try and manually edit the partiiion tbale from inside norton?

---

### Post by az on 2006-02-24
Screw those windows aps.  Boot the installer and use parted from the command line (CTRL-ALt-F2)

parted /dev/hdb
rescue
(enter the locations of where you think the partitions were.  It will promtp to add them to the partition table.)

Stage 1.5 and 2 of grub are not on the MBR, but on the partition you deleted.  If the data is no longer therem, you will have to reinstall grub with a grub menu.list somewhere.

---

### Post by abhaysahai on 2006-02-24
Thanks azz, nice trick.
Could you make a Howto/List of grub boot error and the easy repair options!

---

### Post by az on 2006-02-24
[QUOTE=abhaysahai]Thanks azz, nice trick.
Could you make a Howto/List of grub boot error and the easy repair options![/QUOTE]
There are easy repair options?

If you recover your partition and the data is still there, you probably don't have to reinstall grub, unless you fooled around with the mbr in the meantime.  To reinstall grub:

Let's say we are talking about hdd5

mkdir /hdd5 
mount /dev/hdd5 /hdd5
chroot /hdd5
grub-install /dev/hda

That is also assuming you installed grub to the first hard drive you have.  That is also assuming you are working from the shell from theinstaller cd (you are root)  That is also assuming that you recovered all your partitions,  If you skipped one, then the naming will be different and you will have to rename your partition in /etc/fstab and /boot/grub/menu.list.


See?  Easy,

---

### Post by ninjasmith on 2006-02-25
[QUOTE=azz]Screw those windows aps.  Boot the installer and use parted from the command line (CTRL-ALt-F2)

parted /dev/hdb
rescue
(enter the locations of where you think the partitions were.  It will promtp to add them to the partition table.)

Stage 1.5 and 2 of grub are not on the MBR, but on the partition you deleted.  If the data is no longer therem, you will have to reinstall grub with a grub menu.list somewhere.[/QUOTE]


i get parted is unkown command when I run from the rescue mode from the ubuntu disk installer?

---

### Post by az on 2006-02-25
[QUOTE=ninjasmith]i get parted is unkown command when I run from the rescue mode from the ubuntu disk installer?[/QUOTE]


Doh!

I keep forgetting to mention that you have to let the installer load the components from the disk.  This happens before the partitioner screen.  Just boot and make your way there, then CTRL-ALT-F2.   Sorry.

---

### Post by ninjasmith on 2006-02-25
ok getting somewhere now, however rescue gives the following error

Error: Can't have partition outside the disk

as do the following commands that I have tried

print
check


this is similar to the info showed in norton ghost partition table where there was a spurious partition beyond the end of the disk....

any ideas?

maybe I will try and delete this partition in the norton ghost editor as parted doesnt seem to be ale to hadnle the partition table

---

### Post by ninjasmith on 2006-02-25
ok well fdisk works and shows the following partitions

device          boot  start    end     block            id   system
/dev/sdb1               1       2550    20482843+    7    ntfs
      /sdb2       *     2551   3768      9783585     83   linux
      /sdb3              3769   14588   86911650     f     w95 ext'd (lba)
     /sdb5        ?     18391  65645   379573761   81   Minix / old linux
      /sdb6              3826   6375    20482843      7    ntfs


sdb1,2 and 5 are my linux and two windows partitions.  other than that there should be a 60 gig partition which when I ws trying to edit cause the problem.

I think sdb6 is the problem as it is larger than the drive.  shall I just delete this and then run parted?

---

