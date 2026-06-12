---
title: "Can't mount root on encrypted LVM/raid 1"
date: 2010-11-27
forum: Apple Hardware Users
---

### Post by nataraj88 on 2010-11-27
I'm trying to install ubuntu 10.04.1 on an LVM2 LV on top of a LUKS encrypted file system on top of an md RAID1 partition.  This is on a mid 2010 Mac Mini.

Somehow I was led to believe that the alternate installer may not do the right thing with the GPT partition table on the MAC, so I've tried to use the alternate installer to install the desired setup inside a VM and then copy the the root and boot partitions to the mac mini.  Root (/) is on an LVM /boot is a seperate non-raid unencrypted partion.

I'm able to install grub2 and get it to boot the kernel.  The problem that I'm having is with the kernel mounting the root partition.  I'm even pretty sure that I've got the raid part working because initially I was getting thrown into busybox and I could see that the raid partition was setup.

Here's the error I get from the kernel:

No filesystem could mount root, tried: ext3 ext2 ext4 fuseblock
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

When I copy the install from the VM to the macmini I update the following files:

First, unpack the initrd using cpio
1) In initrd image conf/conf.d/cryptroot
change UUID to the UUID of the encrypted volume (cryptsetup luksUUID /dev/md0)

2) In initrd image etc/mdadm/mdadm.conf change UUID to UUID of md0
On root partition /etc/mdadm/mdadm.conf change UUID to UUID of md0
/boot/grub/grub.cfg must have UUID of root partition
ON root partition in /etc/crypttab change UUID to UUID of md0

3) in initrd image, update UUID for root and swap in /conf/conf.d/cryptroot

4) update fstab on the root partition to have the uuid of /boot and dev/mapper/VolGroup00-ubuntu_10.04_root for root


Then repack initrd using cpio.


I've also tried rebuilding the initrd while booted from the live cd
using:
mkinitramfs -v -k -d /mnt/a/etc/initramfs-tools -o ./initrd.img-2.6.32-24-generic

Note, here I did this with .24 kernel because that's what's on the live CD.  I could see that the correct modules were loaded and the cryptroot hook was invoked, but still I could not get the system to mount / on boot.

```
Here's what things look like booted from a live cd:


Filesystem           1K-blocks      Used Available Use% Mounted on
aufs                   1412888    156008   1256880  12% /
none                   1407976       356   1407620   1% /dev
/dev/sr0                702016    702016         0 100% /cdrom
/dev/loop0              673792    673792         0 100% /rofs
none                   1412888       164   1412724   1% /dev/shm
tmpfs                  1412888        40   1412848   1% /tmp
none                   1412888       104   1412784   1% /var/run
none                   1412888         0   1412888   0% /var/lock
none                   1412888         0   1412888   0% /lib/init/rw
/dev/sdc1              1925728     41744   1786160   3% /media/b34aef70-80ca-4d6c-a36b-c3fa4d7b3b43
/dev/mapper/VolGroup00-ubuntu_10.04_root
                      10321208   2791360   7005560  29% /mnt/a
/dev/sda3               283691    119064    149979  45% /mnt/a/boot
/dev/sdb3               283691     77201    191842  29% /mnt/a/boot2


(parted) unit s                                                           
(parted) p                                                                
Model: ATA Hitachi HTS72505 (scsi)
Disk /dev/sda: 976773168s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start      End         Size        File system  Name                  Flags
 1      40s        409639s     409600s     fat32        EFI System Partition  boot
 2      409640s    68769007s   68359368s   hfs+         Macintosh HD2
 3      69031152s  69617087s   585936s     ext2         /boot
 4      69617096s  976510983s  906893888s               ENCRYPTEDLVMRAID      raid



(parted) unit s                                                           
(parted) print                                                            
Model: ATA Hitachi HTS72505 (scsi)
Disk /dev/sdb: 976773168s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start      End         Size        File system  Name                  Flags
 1      40s        409639s     409600s     fat32        EFI System Partition  boot
 2      409640s    68769007s   68359368s   hfs+         Customer
 3      69031936s  69617871s   585936s     ext2         /boot
 4      69617880s  976510983s  906893104s               ENCRYPTEDLVMRAID      raid
root@ubuntu:/home/ubuntu# cat /proc/mdstat
Personalities : [raid1] 
md0 : active raid1 sda4[0] sdb4[1]
      453446464 blocks [2/2] [UU]
      bitmap: 0/217 pages [0KB], 1024KB chunk

root@ubuntu:/home/ubuntu# pvdisplay 
  --- Physical volume ---
  PV Name               /dev/mapper/md0_crypt
  VG Name               VolGroup00
  PV Size               432.44 GiB / not usable 1.81 MiB
  Allocatable           yes 
  PE Size               4.00 MiB
  Total PE              110704
  Free PE               104560
  Allocated PE          6144
  PV UUID               ZGfcjc-E23g-xppm-a9ps-v4le-O02t-BXHf1F


root@ubuntu:/home/ubuntu# lvdisplay
  --- Logical volume ---
  LV Name                /dev/VolGroup00/ubuntu_10.04_root_OLD
  VG Name                VolGroup00
  LV UUID                rhxdKV-9VJg-qJho-86Eh-bDSP-0zTP-EAJEW3
  LV Write Access        read/write
  LV Status              NOT available
  LV Size                10.00 GiB
  Current LE             2560
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
   
  --- Logical volume ---
  LV Name                /dev/VolGroup00/ubuntu_10.04_swap
  VG Name                VolGroup00
  LV UUID                12vvec-uaDf-Mhbi-gASH-st6d-PJ0I-d1ghpc
  LV Write Access        read/write
  LV Status              NOT available
  LV Size                4.00 GiB
  Current LE             1024
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
   
  --- Logical volume ---
  LV Name                /dev/VolGroup00/ubuntu_10.04_root
  VG Name                VolGroup00
  LV UUID                3KaHfQ-3dE2-WIXe-wxSp-1zAW-KHHh-NTRHPI
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                10.00 GiB
  Current LE             2560
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1


```
I would appreciate any suggestions here.  Is it possible to to do an install from the alternate installer without having it rewrite the GPT partition table or disturb other existing LVM's.  I couldn't seem to get it to do that.

Also, I'm not sure how to run update-grub when booted from the live CD, so I edited /boot/grub/grub.cfg to try to accomplish the initial boot.

Thanks,
Nataraj

---

