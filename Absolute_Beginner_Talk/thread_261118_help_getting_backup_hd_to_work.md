---
title: "help getting backup hd to work"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by jinxjinx on 2006-09-19
i just put in another unformatted hard disk. and it is detected by the bios. but now id like to format it and make it part of my linux system. how can i do this? 

Thanks

---

### Post by kidders on 2006-09-19
Hi there,

This is fairly easy to do:

[LIST=1]
[*]Make sure your Ubuntu box recognises it, by looking for its device identifier in **/dev**.
[*]Once you've found the right device name, use **cfdisk** or another device partitioner to make a few disk partitions.
[*]Use the **mkfs** tools to create filesystems on your new partitions.
[*]If you like, update your **/etc/fstab** to have your filesystems mounted automagically by the system.
[*]Mount your filesystems manually, to avoid having to reboot.
[/LIST]

Post back if you have any trouble!

---

### Post by jinxjinx on 2006-09-20
well i can see a bunch of stuff in dev. how can i tell which one to pass to cfdisk? if i got into /dev/disk/by-id/ i can see that it sees it. 
thanks for the reply.

---

### Post by b_martinez on 2006-09-20
The command 
sudo fdisk -l
will list all mounted drives. If the new one is listed it will be listed as /dev/hdX or /dev/sdX where X= a or b or.....
hth
Bill

---

### Post by kidders on 2006-09-20
**Edit:** Oops... bill got in before me, with a much more straightforward answer!

The names follow a sort of convention, depending on what kind of devices they are ...

/dev/hd* - IDE disk drives

/dev/hda - Primary master IDE device
/dev/hdb - Primary slave IDE device
/dev/hdc - Secondary master IDE device
...
...

/dev/hda1 - Primary master IDE device, partition 1
/dev/hda2 - Primary master IDE device, partition 2
/dev/hda3 - Primary master IDE device, partition 3
...
...

Similar naming schemes are used for /dev/sd* (ie serial devices). You'll also find references to your hard drives in your **dmesg**. Look near the top for things like this ...

```

[17179578.200000] SCSI device sdb: 390721968 512-byte hdwr sectors (200050 MB)
[17179578.200000] SCSI device sdb: drive cache: write back
[17179578.200000]  sdb: sdb1

```

This tells me that, on my PC, SATA disk #2 is called /dev/sdb, is 200GB in size, and contains one partition. Often, your system will name devices for you ...

```

[17179580.224000] hdb: ATAPI 52X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)

```

This tells me my optical drive is at /dev/hdb. This way, if I install something new, I can check where it went ... or more importantly, if Linux doesn't like it.

---

### Post by jinxjinx on 2006-09-21
ok found it but i get this

$ sudo mkfs /dev/hdb
mke2fs 1.38 (30-Jun-2005)
/dev/hdb is entire device, not just one partition!
Proceed anyway? (y,n) y
/dev/hdb is apparently in use by the system; will not make a filesystem here!

---

### Post by maigo on 2006-09-21
I get exactly the same message...

---

### Post by David Corrales on 2006-09-21
You could always install GParted and do it graphically :)

---

### Post by kidders on 2006-09-21
> 
$ sudo mkfs /dev/hdb


Omg I have no clue what doing *that* would do!!

You can't format an entire disk ... you have to partition it first!

Incidentally, you should really consider **not** using the Ext2 filesystem, unless of course there's a specific reason you want to.

---

### Post by jinxjinx on 2006-09-21
its already partitioned. it just cant figure out how to mount it.

also im using ext3...i assume thats ok.

thanks for the help.

---

### Post by kidders on 2006-09-21
If you did **sudo mkfs /dev/hdb** it's probably not partitioned any more!!

You can mount a filesystem with the "mount" command or by adding a line to your /etc/fstab to have it done automatically.

Try **mount /dev/hdb1 /mnt/wherever**

---

### Post by jinxjinx on 2006-09-22
ok thanks.
so once i mount it how do i find it using nautuilus?

---

### Post by kidders on 2006-09-22
Just navigate to its mount point, and voila :-)

---

### Post by jinxjinx on 2006-09-22
opps, ok i figured out i did not do mkfs correctly.

i still dont understand why i cant just do mkfs /dev/hdb ??

thanks for the replys

---

### Post by kidders on 2006-09-23
Same deal on every OS... a filesystem must be contained within a partition.

---

