---
title: "ubuntu won't automount usb flash drive"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by wana10 on 2007-07-19
this is the first time that i have had this problem. when i plug my usb flash-drive into a usb slot its led flashes to show it is being used but ubuntu doesn't mount it automatically like it used to. how can i fix this so that ubuntu will mount my flash drive automatically?

edit* found my problem. when i plug in my flash drive without my external hdd connected the flash drive is seen as /dev/sdb1. in fstab my sdb1 is set for my external hdd which i have to mount automatically. so all i had to do was 'sudo mount /dev/sdb1' and then use nautilus to go to /media/external. of course if i forgot the 'sudo umount' things might get annoying... oh well

---

### Post by asmoore82 on 2007-07-19
unplug it and plug it back in, then open a term and run
```
$ dmesg | tail
```
and post the results.

---

### Post by ubanchaos on 2007-07-19
take it out first and put it back in and use the code: $ dmesg | tail

---

### Post by wana10 on 2007-07-19
here's my dmsg | tail
```
~$ dmesg | tail
[483248.640000] sdb: Write Protect is off
[483248.640000] sdb: Mode Sense: 23 00 00 00
[483248.640000] sdb: assuming drive cache: write through
[483248.652000] SCSI device sdb: 2015232 512-byte hdwr sectors (1032 MB)
[483248.656000] sdb: Write Protect is off
[483248.656000] sdb: Mode Sense: 23 00 00 00
[483248.656000] sdb: assuming drive cache: write through
[483248.656000]  sdb: sdb1
[483248.656000] sd 7:0:0:0: Attached scsi removable disk sdb
[483248.656000] sd 7:0:0:0: Attached scsi generic sg1 type 0
```

if there's a way to automount /dev/sdb1 on plug-in that would be awesome

---

### Post by bodhi.zazen on 2007-07-19
In fstab mount your usb hd by LABEL or UUID rather then device ...

So, replace the first part of the line :

/dev/sdb1

With either 

LABEL=<instert label here>

OR

UUID=xxx (where xxx = UUID)

To see the uuid, plug in the drive, then enter this command :

```
blkid
```

Your flash card should then auto mount again.

---

### Post by wana10 on 2007-07-19
when i replace /dev/sdb1 with either uuid or label and try to mount hdd it says it cannot find it.

```
/dev/sdb1: LABEL="SEA_DISK" UUID="0000-0F12" TYPE="vfat"
:~$ sudo mount SEA_DISK
mount: can't find SEA_DISK in /etc/fstab or /etc/mtab
:~$ sudo mount LABEL="SEA_DISK"
mount: can't find LABEL=SEA_DISK in /etc/fstab or /etc/mtab
~$ sudo mount -a
mount: special device /dev/disk/by-label/SEA_DISK does not exist
```
and after changing fstab to uuid
```
~$ sudo mount -a
mount: special device /dev/disk/by-uuid/0000-0F12 does not exist
```

---

### Post by bodhi.zazen on 2007-07-19
What lines are you using in fstab ?

Can you mount with either :

sudo mount LABEL=SEA_DISK <mount_point>

OR

sudo mount UUID=0000-0F12 <mount_point>

changing "<mount_point>" to your actual desired mount point ?

---

### Post by alex_anthony on 2007-07-19
I fixed an automounting problem by installing the new backported verison of hal (hardware abstraction layer I think)
In System>Administration>Software sources, on the updates tab,
 tick 'Unsupported Updates (feisty backports)' and close 
and then in update manager update hal and anything which mentions hal.

Now it automounts any external drive perfectly

---

### Post by zorkerz on 2008-02-02
In hardy I authorized my ntfs partition to automount on every start up. I no longer want it to do this. Is there a way to unauthorize the automount? The ntfs partition is not in fstab.

---

