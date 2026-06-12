---
title: "Grub2 booting problems with GPT"
date: 2011-12-29
forum: Any Other OS
---

### Post by zuku on 2011-12-29
Hi,
I've installed debian 6.0.3 od adaptec raid5, but after installation my grub2 won't start giving me error: not found and blinking cursor in rescue mode. Here is print from live cd with my partitions:

```
sing /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) p                                                                
Model: Adaptec RAID 5 (scsi)
Disk /dev/sda: 8987GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      17.4kB  1018kB  1000kB                        bios_grub
 2      1018kB  8979GB  8979GB  ext3                  boot
 3      8979GB  8987GB  8105MB  linux-swap(v1)


```

---

### Post by Elfy on 2011-12-29
Thread moved to Other OS/Distro Talk.

---

### Post by jjex22 on 2011-12-29
As you are using hardware RAID 5, I doubt this is causing the problem, I'd imagine the gpt is at fault - did you use the guided partitioning with squeeze?  anyway looks as though your mbr partition is set up okay, so I'd recommend using a live cd such as [Super Grub Disk]("http://www.supergrubdisk.org/") or the debian live cd and chroot into your install just like ubuntu and use 
```

grub-install /dev/sda

```

and of course update-grub if you're using the debian live cd.

Hope it helps!

---

### Post by zuku on 2011-12-30
Thanks for your reply!
So now I can boot to my new system but only using Super Grub2 Disk which decects my boot entries:

(hd1,gpt2)/boot/vmlinuz-2.6.32-5-amd64
(hd1,gpt2)/boot/vmlinuz-2.6.32-5-amd64 (single)

So after login I've reinstalled grub:

grub-install /dev/sda
Installation finished. No error reported.

but after restart still the same.
Grub loading
Welcome to GRUB!
error:file not found
grub rescue >

here you are my all partitions:
```
GPT fdisk (gdisk) version 0.5.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): p
Disk /dev/sda: 17553141760 sectors, 8.2 TiB
Disk identifier (GUID): 64
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 17553141726
Total free space is 0 sectors (0 bytes)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34            1987   977.0 KiB   EF02
   2            1988     17537312534   8.2 TiB     EF00
   3     17537312535     17553141726   7.5 GiB     8200

Command (? for help): i
Partition number (1-3): 1
Partition GUID code: 49 (BIOS boot partition)
Partition unique GUID: FE
First sector: 34 (at 17.0 KiB)
Last sector: 1987 (at 993.5 KiB)
Partition size: 1954 sectors (977.0 KiB)
Attribute flags: 0000000000000000
Partition name:

Command (? for help): i
Partition number (1-3): 2
Partition GUID code: 3B (EFI System)
Partition unique GUID: 6D
First sector: 1988 (at 994.0 KiB)
Last sector: 17537312534 (at 8.2 TiB)
Partition size: 17537310547 sectors (8.2 TiB)
Attribute flags: 0000000000000000
Partition name:

Command (? for help): i
Partition number (1-3): 3
Partition GUID code: 4F (Linux swap)
Partition unique GUID: C9
First sector: 17537312535 (at 8.2 TiB)
Last sector: 17553141726 (at 8.2 TiB)
Partition size: 15829192 sectors (7.5 GiB)
Attribute flags: 0000000000000000
Partition name:

Command (? for help):

```

---

