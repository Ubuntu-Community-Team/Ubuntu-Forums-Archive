---
title: "e2fsck with alternative superblock"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by dstew on 2008-04-03
Please post the error message for us. Thanks.

---

### Post by prshah on 2008-04-03
> **Auston said:**
> Hello. Am trying to boot linux and it says the superblock could not be read or does not describe the correct ext2 filesystem. It suggests running e2fsck with an alternative superblock. Please somebody help me out here. Am stuck.

You cannot (should not) run e2fsck on a MOUNTED file system. Unmount it first.

--OR--

You are tryingto run fsck on a DEVICE rather than a partition, eg., /dev/hda, instead of /dev/hda1.

--OR-- (unlikely) 

you have a GENUINELY (slightly) corrupted file system, in which case we need the output of ```
mke2fs -n /dev/xda9
``` where /dev/xda9 is your actual partition which needs to be checked. NOTE: The partition MUST be unmounted, and [color=red]if you FORGET the "-n" you will RUIN your system.[/color]

---

### Post by Gut Feeling on 2008-06-08
Hi,

I think I've got a 'genuinely (slightly) corrupted file system' :-(

(After booting from the 8.04 Live CD)

**'sudo fdisk -l' gives me:**
/dev/sda1 (marked as boot): Id=83, Linux
/dev/sda2: Id=5, Extended
/dev/sda5: Id=82, Linux swap / Solaris

**'sudo -fsck -a /dev/sda1' gives me:**
"fsck.ext2: Bad magic number in super-block while trying to open /dev/sda1
/dev/sda1:
The superblock could not be read or does not describe a correct ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running s2fsck with an alternate superblock:
e2fsck -b 8193 <device>"

**'sudo mke2fs -n /dev/sda1' then gives me:**
warning: 12 blocks unused
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
1759936 inodes, 7012352 blocks
350618 blocks (5.00%) reserved for the super user
First data block=0
Maximum file system blocks=0
214 block groups
32768 blocks per group, 32768 fragments per group
8224 inodes per group
Superblock backups stored on blocks:
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 4096000

I also followed some instructions at 'http://www.bellevuelinux.org/superblock':
**sudo e2fsck -f -b 8193 /dev/sda1**
which gets:
"Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?"


Thanks for any help.

---

### Post by Herman on 2008-06-08
```
Superblock backups stored on blocks:
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 4096000
```Boot a Live CD and try 'sudo e2fsck -b 32768 /dev/sda1' then.
```
sudo e2fsck -b 32768 /dev/sda1
```The reason why it's best to do this from a Live CD is so that your file system won't be mounted. 
You can do it from a different partition if you have another partition or hard disk with Linux installed, as long as you unmount the file system you want to work on first.

This command will replace your superblock with the backup copy which is located at sector 32768. If that doesn't work try the same command again but replace '32768' with '98304'.

---

### Post by Gut Feeling on 2008-06-10
Thanks for the reply Herman.

I tried that command for all the superblock backups but got the same message for all:
"e2fsck: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?"

I also tried unmounting /dev/sda1 ('sudo umount /dev/sda1' (which seemed to work correctly as it came back with 'umount: /dev/sda1: not mounted')), in case that was stopping it from working, but got the same message.

---

### Post by prshah on 2008-06-10
> **Gut Feeling said:**
> 
I tried that command for all the superblock backups but got the same message for all:
"e2fsck: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?"


Boot off the live CD, retry the above commands, and if it again doesn't work, post the results of```
dmesg | tail
sudo tune2fs -l /dev/sda1
```

I'm suspecting an incorrect block size, which means that the backup superblock entries are also wrong.

---

### Post by Gut Feeling on 2008-06-11
> **prshah said:**
> Boot off the live CD, retry the above commands, and if it again doesn't work, post the results of```
dmesg | tail
sudo tune2fs -l /dev/sda1
```

I'm suspecting an incorrect block size, which means that the backup superblock entries are also wrong.

Hi PRShah,

Same results with retrying the 'sudo e2fsck -b xxxxxxx /dev/sda1' commands.

**Results of 'dmesg | tail' :**
Bluetooth: RFCOMM ver 1.8
[drm] Initialized drm 1.1.0 20060810
ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
PCI: Setting latency timer of device 0000:00:02.0 to 64
[drm] Initialized i915 1.6.0 20060119 on minor 0
PCI: Setting latency timer of device 0000:00:02.1 to 64
[drm] Initialized i915 1.6.0 20060119 on minor 1
NET: Registered protocol family 10
lo: Disabled Privacy Extensions
ADDRCONF(NETDEV_UP): eth0: link is not ready

**Results of 'sudo tune2fs -l /dev/sda1':**
tune2fs 1.40.8 (13-Mar-2008 )
tune2fs: Bad magic number in super-block while trying to open /dev/sda1
Couldn't find valid filesystem superblock.

Thanks

---

