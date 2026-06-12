---
title: "Mounting hfs partition at boot"
date: 2010-05-16
forum: Apple Hardware Users
---

### Post by davideotape on 2010-05-16
I'm currently trying to mount a hfs partition at boot as part of my quest to have a shared music folder across ubuntu and OSX. Here's the output of fdisk -l

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc8ffc8ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  GPT
/dev/sda2              26       10224    81919460   af  HFS / HFS+
/dev/sda3           10225       12151    15474648   af  HFS / HFS+
/dev/sda4   *       12167       15299    25159180   83  Linux

```

I'm trying to mount /dev/sda3 at boot, and here's what my /etc/fstab looks like:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system>                           <mount point>   <type>       <options>                                <dump>  <pass>

proc                                      /proc           proc         defaults                                 0       0

# / was on /dev/sda3 during installation
UUID=0930a768-d3be-4580-85e2-a0598063e769 /               ext4         errors=remount-ro                        0       1

/dev/scd0                                 /media/cdrom0   udf,iso9660  user,noauto,exec,utf8                    0       0

/dev/sda3                                 /mnt/data       hfs          user,auto,file_umask=0111,dir_umask=0000  0       0
```

When I boot I get the following message:

```
mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mountall: mount /mnt/data [576] terminated with status 32
mountall: Filesystem could not be mounted: /mnt/data
Skipping /mnt/data at user request
```

Anyone know what I'm doing wrong and how I can make this work?

Regards,
David

---

### Post by propagation_of_sound on 2010-05-16
/dev/sda3 should be mounted as hfsplus in /etc/fstab, not hfs

-j

---

### Post by linuxopjemac on 2010-05-16
what happens if you do it manually?

```
sudo mount -t hfs /dev/sda3 /mnt/data
```

---

### Post by linuxopjemac on 2010-05-16
If you can't do it manually you need the following programs probably:

hfsplus - Tools to access HFS+ formatted volumes
hfsutils - Tools for reading and writing Macintosh volumes

---

### Post by davideotape on 2010-05-16
Got both hfsutils and hfsplus installed.

```
$ sudo mount -t hfs /dev/sda3 /mnt/data
[sudo] password for david: 
mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

But ```
$ sudo mount -t hfsplus /dev/sda3 /mnt/data
``` works fine. I'll try changing it in /etc/fstab. Don't quite understand that though, cause I formatted it to hfs using OSX yesterday, not hfs+

---

### Post by davideotape on 2010-05-16
Changed to hfsplus in /etc/fstab, but I'm still getting the same errors. Here are the relavent entries in /var/log/syslog :

```
May 16 11:51:08 david-macbook os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sda3
May 16 11:51:08 david-macbook 10freedos: debug: /dev/sda3 is not a FAT partition: exiting
May 16 11:51:08 david-macbook os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sda3
May 16 11:51:08 david-macbook 10qnx: debug: /dev/sda3 is not a QNX4 partition: exiting
May 16 11:51:08 david-macbook os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sda3
May 16 11:51:08 david-macbook macosx-prober: debug: /dev/sda3 is an HFS+ partition
May 16 11:51:08 david-macbook os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sda3
May 16 11:51:08 david-macbook 20microsoft: debug: /dev/sda3 is not a MS partition: exiting
May 16 11:51:08 david-macbook os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sda3
May 16 11:51:08 david-macbook 30utility: debug: /dev/sda3 is not a FAT partition: exiting
May 16 11:51:08 david-macbook os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sda3
May 16 11:51:08 david-macbook os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sda3
May 16 11:51:08 david-macbook os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sda3
May 16 11:51:08 david-macbook os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sda3
May 16 11:51:08 david-macbook os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sda3g
```

---

### Post by srs5694 on 2010-05-16
First, try trimming your mount options in /etc/fstab. You've got a fair number of options there, and I'm not even sure they're all useful for HFS+ (file_umask and dir_umask, in particular). It's conceivable they're causing problems. I'd just use "defaults" as the mount option for the moment. If you want to add more in the future, you can do so once you get the basics working.

Second, although I don't think this is the issue, you should be aware that Linux understands GPT perfectly well. Your MBR partitions (revealed by "fdisk -l") are irrelevant, and their numbering may not be the same as the numbering for the GPT partitions that Linux is probably using. You should be able to use parted ("sudo parted /dev/sda print") or gdisk ("sudo gdisk -l /dev/sda") to view your GPT partitions in Linux. (The gdisk program probably isn't installed by default. If you're using 10.04, you can install it by typing "sudo apt-get install gdisk"; otherwise, or if you want the latest version, download the .deb file for your architecture from [its Sourceforge downloads page.](http://sourceforge.net/projects/gptfdisk/files/)) Use the number for the GPT partition, rather than your MBR partition number, to identify the shared-data partition. I say this isn't likely to be the problem, though, because you report that a manual mount command using the /dev/sda3 identifier worked. Still, it's worth double-checking. In fact, unless the way you're booting Linux requires the hybrid MBR, you might want to consider converting it to a standards-conformant protective MBR. Hybrid MBR configurations [are flaky and dangerous.](http://www.rodsbooks.com/gdisk/hybrid.html) That said, I'm not an expert on booting Linux on Intel-based Macs; it's conceivable that it's required for some boot methods on that hardware, so proceed with caution.

Third, you may find it informative to type "sudo blkid". This will reveal some basic information, including filesystem types and UUID values, for all your partitions. You might be able to specify the partition using its UUID value rather than its device filename.

---

### Post by Zookalicious on 2010-05-16
Adding 
```
/dev/sda2                     /media/sda2  hfsplus  defaults                  0  0
```
At the bottom of my /etc/fstab worked for me. My drive mounts automatically at login.

Try 
```
/dev/sda3                     /media/sda3  hfsplus  defaults                  0  0
```?

---

### Post by davideotape on 2010-05-17
> **Zookalicious said:**
> 
Try 
```
/dev/sda3                     /media/sda3  hfsplus  defaults                  0  0
```?

Cheers, that got it working for me :)

---

