---
title: "Problem mounting second drive - 'promise_fasttrack_raid_member'"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by Chadwick on 2007-07-14
Hello,

I have added a second drive to my Ubuntu only desktop. It's been picked up by BIOS and its logical name is /dev/sdb. I formatted it to ext3 and then tries to mount it, but got the error below:

laracroft@laracroft-desktop:/mnt$ sudo mount /dev/sdb /mnt/sdb1
mount: unknown filesystem type 'promise_fasttrack_raid_member'

The disk is not new so may have been part of a raid in the past, however, I don't want to mount it as a raid now. Does anyone know how I can solve this issue?

Many thanks in advance.

  *-disk:1
       description: SCSI Disk
       product: ST380011A
       vendor: ATA
       physical id: 1
       bus info: scsi@0:0.1.0
       logical name: /dev/sdb
       version: 8.01
       serial: 5JVK19CD
       size: 74GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
     *-volume
          description: Linux filesystem partition
          physical id: 1
          bus info: scsi@0:0.1.0,1
          logical name: /dev/sdb1
          capacity: 74GB
          capabilities: primary

laracroft@laracroft-desktop:/mnt$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9636    77401138+  83  Linux
/dev/sda2            9637        9729      747022+   5  Extended
/dev/sda5            9637        9729      746991   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161   83  Linux

---

### Post by jfinkels on 2007-07-14
> **Chadwick said:**
> Hello,

I have added a second drive to my Ubuntu only desktop. It's been picked up by BIOS and its logical name is /dev/sdb. I formatted it to ext3 and then tries to mount it, but got the error below:

laracroft@laracroft-desktop:/mnt$ sudo mount /dev/sdb /mnt/sdb1
mount: unknown filesystem type 'promise_fasttrack_raid_member'

The disk is not new so may have been part of a raid in the past, however, I don't want to mount it as a raid now. Does anyone know how I can solve this issue?

Many thanks in advance.

  *-disk:1
       description: SCSI Disk
       product: ST380011A
       vendor: ATA
       physical id: 1
       bus info: scsi@0:0.1.0
       logical name: /dev/sdb
       version: 8.01
       serial: 5JVK19CD
       size: 74GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
     *-volume
          description: Linux filesystem partition
          physical id: 1
          bus info: scsi@0:0.1.0,1
          logical name: /dev/sdb1
          capacity: 74GB
          capabilities: primary

laracroft@laracroft-desktop:/mnt$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9636    77401138+  83  Linux
/dev/sda2            9637        9729      747022+   5  Extended
/dev/sda5            9637        9729      746991   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161   83  Linux

When you use mount, you need to mount a partition, NOT a drive. So instead of this:```
sudo mount /dev/sdb /mnt/sdb1[code] do this:[code]sudo mount /dev/sdb**1** /mnt/sdb1
```

/dev/sdb is the location of the entire physical disk, /dev/sdb1 is the location of the partition.

---

### Post by Chadwick on 2007-07-25
Many thanks jfinkels, that did the trick! :)

---

