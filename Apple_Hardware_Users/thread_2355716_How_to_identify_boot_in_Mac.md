---
title: "How to identify boot in Mac?"
date: 2017-03-15
forum: Apple Hardware Users
---

### Post by Music_Guy on 2017-03-15
I have a 2010 MacPro Intel running only Ubuntu Studio 16.04. I installed from a USB stick. When I looked on the drive where the OS is installed, under a partition labeled "unknown" was listed boot/grub (or grub/boot, I can't remember the order. I'm not on the machine now.) Does this mean that the MacPro boots using grub and not efi or uefi? Also, when I entered 'grub' on the terminal, it returned a message stating the grub was not installed with how to install it. Is this machine booting using grub, or is there some way to tell what the boot manager is? Would reFind help anything? I'm planning to set up a dual boot system, and want to know what I may have to change.

Thanks. :confused:

---

### Post by Dennis N on 2017-03-15
Run in Ubuntu's terminal
```
sudo parted -l
```
and post the output. It should shed some light on the partition table type and if any EFI system partitions are present.

grub is the package name of the old grub that is no longer used, so what you got is to be expected. Not on my system either:
```
dmn@Sydney:~$ apt-cache policy grub
grub:
  Installed: (none)
  Candidate: 0.97-29ubuntu66
```

Also, an indicator for a UEFI install - UEFI installs will have (among others) **grub-efi-amd64** installed, so you can look for that:

```
dmn@Zotac:~$ apt-cache policy grub-efi-amd64
grub-efi-amd64:
  Installed: 2.02~beta2-9ubuntu1.11
  Candidate: 2.02~beta2-9ubuntu1.12
```

version will vary with your release.

---

### Post by Music_Guy on 2017-03-16
Here is the output from sudo parted:
[COLOR=#0000ff]Model: ATA WDC WD1003FZEX-0 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: [/COLOR]

[COLOR=#0000ff]Number  Start   End     Size    File system     Name  Flags
 1      1049kB  2097kB  1049kB                        bios_grub
 2      2097kB  992GB   992GB   ext4
 3      992GB   1000GB  8575MB  linux-swap(v1)


Model: ATA Hitachi HDS72101 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  ntfs


Model: ATA WDC WD10EAVS-00D (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                  Flags
 1      20.5kB  210MB   210MB   fat32        EFI System Partition  boot, esp
 2      211MB   1000GB  1000GB  fat32        WD 1T DISK            msftdata

[/COLOR]

Note: the OS is in sda; sdb is a backup drive; sdc has data files - this was the original drive from the mac, which is probably why there is an EFI partition, since I did not add it.

Here is the apt-cache policy grub output:
[COLOR=#0000ff]grub:
  Installed: (none)
  Candidate: 0.97-29ubuntu68
  Version table:
     0.97-29ubuntu68 500
        500 [/COLOR][[COLOR=#0000ff]http://us.archive.ubuntu.com/ubuntu[/COLOR]]("http://us.archive.ubuntu.com/ubuntu")[COLOR=#0000ff] xenial/main amd64 Packages
[/COLOR]
Here is the apt-cache policy grub-efi-amd64 output:

[COLOR=#0000ff]grub-efi-amd64:
  Installed: (none)
  Candidate: 2.02~beta2-36ubuntu3.8
  Version table:
     2.02~beta2-36ubuntu3.8 500
        500 [/COLOR][[COLOR=#0000ff]http://us.archive.ubuntu.com/ubuntu[/COLOR]]("http://us.archive.ubuntu.com/ubuntu")[COLOR=#0000ff] xenial-updates/main amd64 Packages
     2.02~beta2-36ubuntu3 500
        500 [/COLOR][[COLOR=#0000ff]http://us.archive.ubuntu.com/ubuntu[/COLOR]]("http://us.archive.ubuntu.com/ubuntu")[COLOR=#0000ff] xenial/main amd64 Packages[/COLOR]

Does this help? Thanks.

---

### Post by Dennis N on 2017-03-16
Yes, very helpful. It tells us that Ubuntu definitely is installed in bios mode, because:
1) grub-efi-amd64 is not installed.
2) ubuntu is on sda, which has a gpt partition table and a bios_grub partition. The latter is used with a bios install on a gpt disk.

If you are going to dual boot, then you will have to also install the 2nd system in bios mode (not UEFI), or you won't be able to boot it from Ubuntu's grub. That means the installer must be booted in bios mode.
-------------------------------------
I hope this helps. Good luck with your dual boot project.

---

### Post by Music_Guy on 2017-03-17
Thanks @Dennis. I'm going to dual boot with Fedora, which does allow BIOS installs. I'll just have to work out the process.

Two more questions, if you don't mind.
- Would it be worthwhile to reinstall Ubuntu in efi mode?
- If so, how would I go about doing that? I installed from a usb stick that was created on a mac for the current install. There must be something else I have to do for an efi install.

Thanks again   :D

---

### Post by Dennis N on 2017-03-17
I'm glad to hear you are making progress. I don't know much about Macs, but you did get Ubuntu installed in BIOS mode, so I wonder why not Fedora?

Information here on installation:

[https://fedoraproject.org/wiki/Unified_Extensible_Firmware_Interface#UEFI-native_and_BIOS-native_installations](https://fedoraproject.org/wiki/Unified_Extensible_Firmware_Interface#UEFI-native_and_BIOS-native_installations)

Looks like most of what you need to know is in there. It does say "Pretty much any Fedora medium of any kind should always be BIOS-bootable."

On the other hand, I do see this comment right at the top.

> If you have an Intel-based Apple system, it has a UEFI firmware, though there are special considerations involved in installing and booting Fedora on Apple systems due to the special Apple boot interface built on top of UEFI. It is best to refer to Apple-specific instructions rather than follow this generic UEFI guide, for Apple installations. 

So I leave it to you to sort that out.

If you use UEFI and dual boot, you would have to reinstall Ubuntu in UEFI mode. With that mode, you need to have an EFI system partition for your OSes on sda (see "partitioning for UEFI" in the guide). Both Fedora and Ubuntu can use the same EFI system partition and store their files in folders on it.

---

### Post by Music_Guy on 2017-03-17
Thanks again @Dennis. I guess the first Ubuntu install was via BIOS because I installed on a new hard drive that I did not partition for EFI, so Ubuntu picked BIOS. I think I'll install the Fedora as BIOS-bootable as a first go. If it does not work, I'll start over, setting up a partition for EFI. 

Just one more thing (I hope). It looks like I'll have to add install grub using the source suggested above. Then I should be able to set up grub so that it will pause for some time on startup to allow me to choose the OS. Do I have that correct?

---

### Post by Dennis N on 2017-03-17
> Just one more thing (I hope). It looks like I'll have to add install grub using the source suggested above. Then I should be able to set up grub so that it will pause for some time on startup to allow me to choose the OS. Do I have that correct?

grub install will be taken care of during installation. You may have to specify where to install it during installation, which for BIOS installs would be sda, the disk your computer is booting to on startup. The grub menu is also initially created during your installation. Nothing to do on that. The default for the menu gives 10 seconds (10 in Ubuntu, Fedora's is shorter - I think 5 seconds) to choose between OSes, but once you move the selector, it will wait forever for you to actually select one.
 
I hope that answers the question.

---

