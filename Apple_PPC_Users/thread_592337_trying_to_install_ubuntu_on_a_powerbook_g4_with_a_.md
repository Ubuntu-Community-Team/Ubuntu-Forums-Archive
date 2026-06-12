---
title: "trying to install ubuntu on a powerbook g4 with a broken cdrom"
date: 2007-10-26
forum: Apple PPC Users
---

### Post by emrgncman on 2007-10-26
i am a noob to ubuntu, and am really enjoying it on my pc laptop, I would really like to have it on my powerbook.  any help is appriciated.

I have a Powerbook g4 and it has a cdrom that will only work for about 5 min then it heats up and wont work.  I have an external Firewire/USB cd rom (cant get ubuntu to boot on the external) and i have an IMAC g4 with a good cd rom.  I have read posts and installed to the powerbook with it in target mode,(it fails the yaboot install part just like they said) and followed instructions  to copy yaboot, and yaboot.conf to the bootstrap partition that the installer made.  when i try to copy to that bootstrap patition it says it cannot write to read-only system partition.  I either need to find out how to copy those files to the bootstrap partition, or find out how to boot the ubuntu live cd on my external cd rom drive.  

thanks in advance,

emrgncman

---

### Post by pxwpxw on 2007-10-26
> **emrgncman said:**
> i am a noob to ubuntu, and am really enjoying it on my pc laptop, I would really like to have it on my powerbook.  any help is appriciated.

I have a Powerbook g4 and it has a cdrom that will only work for about 5 min then it heats up and wont work.  I have an external Firewire/USB cd rom (cant get ubuntu to boot on the external) and i have an IMAC g4 with a good cd rom.  I have read posts and installed to the powerbook with it in target mode,(it fails the yaboot install part just like they said) and followed instructions  to copy yaboot, and yaboot.conf to the bootstrap partition that the installer made.  when i try to copy to that bootstrap patition it says it cannot write to read-only system partition.  I either need to find out how to copy those files to the bootstrap partition, or find out how to boot the ubuntu live cd on my external cd rom drive.  

thanks in advance,

emrgncman

You need to know where everything is.
Use your live CD on the imac, with the pbook in target mode,
and from a terminal 
```

 sudo mac-fdisk -l

```
That should produce a listing of all the partitions on both machines.
If you can copy the output and post it, it will be a good start.

You might also see if , from the pbook, you can boot the cd in the imac connected in firewire target mode.
That might be an easier way to install.

[pbook]------firewire----[imac target]----[cdrom]

---

### Post by emrgncman on 2007-10-26
ok, I will get that info for ya, I tried putting the live cd in the imac and booting to target mode, then option booting the powerbook, it sees the osx that is on the imac, but does not see the live cd as a bootable drive.  is there anything i have to do to point the pbook to the cdrom in the imac?

p.s. i can get the pbook to boot to the yaboot menu but when i hit enter, or type live the drive craps out shortly after that.  is there a way i can point yaboot to boot from the external firewire cdrom drive instead of the internal cd rom drive.  i have tried " device=/pci@f4000000/Firewire" but that dont work either.  

thanks

> 
ubuntu@ubuntu:~$ mac-fdisk -l
/dev/sda
        #                    type name                 length   base     ( size )  system
/dev/sda1     Apple_partition_map Apple                    63 @ 1        ( 31.5k)  Partition map
/dev/sda2         Apple_Bootstrap untitled               1954 @ 64       (977.0k)  NewWorld bootblock
/dev/sda3         Apple_UNIX_SVR2 untitled           75119141 @ 2018     ( 35.8G)  Linux native
/dev/sda4         Apple_UNIX_SVR2 swap                3019001 @ 75121159 (  1.4G)  Linux swap

Block size=512, Number of Blocks=78140160
DeviceType=0x0, DeviceId=0x0

mac-fdisk: can't open file '/dev/hda'  (Permission denied)
/dev/hdb
        #                    type name                length   base    ( size )  system
/dev/hdb1     Apple_partition_map Apple                    2 @ 1       (  1.0k)  Partition map
/dev/hdb2               Apple_HFS Ubuntu 7.04 ppc    1407584 @ 16      (687.3M)  HFS

Block size=512, Number of Blocks=1407600
DeviceType=0x1, DeviceId=0x1

ubuntu@ubuntu:~$ sudo mac-fdisk -1



---

### Post by pxwpxw on 2007-10-26
> **emrgncman said:**
> ok, I will get that info for ya, I tried putting the live cd in the imac and booting to target mode, then option booting the powerbook, it sees the osx that is on the imac, but does not see the live cd as a bootable drive.  is there anything i have to do to point the pbook to the cdrom in the imac?

p.s. i can get the pbook to boot to the yaboot menu but when i hit enter, or type live the drive craps out shortly after that.  is there a way i can point yaboot to boot from the external firewire cdrom drive instead of the internal cd rom drive.  i have tried " device=/pci@f4000000/Firewire" but that dont work either.  

thanks

Do you mean that you see 2 icons, Macosx and Linux when you startup, and then you boot the linux icon to get to the yaboot menu, but then no further? That is probably the case.

For the partition info, try again with "sudo" to see the other drive, and please identify what/where they are. The /dev/hdb looks like the iMac CD,  /dev/sda your iMac?
You should be able to see your installation on the pbook.

```

 sudo mac-fdisk -l

```

I will check that out here later, to see what you can do/see in target firewire mode.

---

### Post by ag0g0girl on 2007-10-26
I have an extra superdrive.  I changed mine already and it wasn't hard.  A new one would be $200, but I got this one for $40.

---

### Post by pxwpxw on 2007-10-28
I checked out a couple of options for booting installers from external firewire drives in target mode apple ppc's, or from usb flash stick.

1. Not recommended. Booting a ubuntu install CD in a target G5 power ppc via firewire from an ibookg4, you can indeed boot it from open firmware by booting yaboot on the CD via the  firewire device path - but it will not run the install, just a rescue.
 
for example:
```

0> boot   fw/node/sbp-2@4000/disk:,install\yaboot 

```

The correct sbp-2 address is needed to distinguish the CD from other drives on the target machine. The address is found in open firmware by listing other disks:
```

0> dev fw ls

```

Then in the installer or rescue, the cdrom has to be mounted manually when it cant be found. But then the install fails when the Partitioner starts up and gets lost so can't install that way. 

However you can boot the same way successfully in rescue mode (no partitioner) and edit files on the target ppc or other rescue functions, also needing to manually mount the CD on the way.

2. Much easier - booted from a USB Flash drive (NOT a usb HDD) in the iBookg4, formatted by Macosx as an Apple Macos standard (hfs) with 1 partition, then loaded it with yaboot, yaboot.conf, vmlinux and initrd.img, and optionally a full install iso for hd-media install images.

 Booted from OpenFirmwre for example (may be usb0....usb3.. ):

```

0> boot usb0/disk:2,yaboot

```

It then ran normally for install or rescue to internal drive, or booting an internal drive kernel.

Some usb flash sticks don't work (U3, Security, Easy Vista ready and other fancy stuff).

---

