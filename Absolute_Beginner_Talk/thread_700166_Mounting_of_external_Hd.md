---
title: "Mounting of external Hd"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by TURNER on 2008-02-18
I am currently having issues connecting an external scsi disc (5 in totel which are daisy chained) via the firewire port.

I was under the impression that this should be automatically detected and mounted, however I seem to have been incorrect with that assumption...

after hot plugging the device in question I run a sudo fdisk -l command and notice that none of drives are displayed...I believe it should mount as follows

sda
sdb

etc etc...for all 5 daisy chained drives....

the drives are not in the fstab.....I was wondering if they first need to be added there before being able to see the drives??

If indeed they do need to be added, then what is the actual mount point for a device such as this?

thanks in advance for any assistance.

---

### Post by jan quark on 2008-02-18
plug in all your external devices and run these commands and post the output please

```
mount
```

```
sudo fdisk -l
```

```
cat /etc/fstab
```

---

### Post by TURNER on 2008-02-18
hi, thanks for your reply...as this is a linux server which isnt connected to the internet, iam unable to transfer accross the full file...however I can confirm that upon running mount

/dev/sda1 on type ext3
/dev/sda3 on /home type ext3

other stuff listed there is:

none on /dev/pts type devpts

The scsi drives in question are all 100gb in size, 5 in total.

fdisk -l

lists

/dev/sda1
/dev/sda2
/dev/sda3

again, unsure what this is, perhaps a device which is plugged into one of the other machines on the server.....however no other removable drives are plugged into this machine..

fstab doc again lists sda1 2 sda 3 and lists sda 2 as swap.....

aside from this just the normal hda drives lists, and another machine on the network....

If i were to add mount points to the fstab, where would I start?

***EDIT** just checked again, fstab indicats that the sda's listed are actually the machines harddrives, the hda listed there is a cd rom.....seems this machine has scsi hard drives...which are partitioned....

---

