---
title: "dapper hang on boot"
date: 2006-06-27
forum: Apple PPC Users
---

### Post by godard on 2006-06-27
I've been through a major odyssey with the transition from breezy to dapper, mostly on account of the kernel problems i encountered during Dapper's development: 

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508)

Here is the pre-reboot method i ran through to get a working install: Clean install Breezy --> dist-upgrade to Dapper via distribution installer CD --> updated all packages via synaptic --> removed quiet splash options + ybin -v --> removed old Dapper distribution kernel and i set the old Breezy kernel for 'old' as a boot option that works.

Attempting to boot the latest kernel (.43) grinds to a halt at one of two places:

hda: cache flushes supported
hda: [mac] hda1 hda hda3 hda4 hda5 hdb6

OR 

hdb: cache flushes supported
hdb: [mac] hdb1 hdb2 hdb3 hdb4 hdb5 hdb6

Any help as to why the boot cyle would be stopping there would be greatly appreciated. This is my yaboot.conf, just in case this might help.

boot=/dev/hdb2
device=/pci@f2000000/mac-io@17/ata-4@1f000/disk@1:
partition=4
root=/dev/hdb4
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx=/dev/hda9

image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old

**My configuration:**

  Machine Name: Power Mac G4
  Machine Model: PowerMac3,5
  CPU Type: PowerPC G4 (2.1)
  Number Of CPUs: 1
  CPU Speed: 867 MHz
  L2 Cache (per CPU): 256 KB
  L3 Cache (per CPU): 2 MB
  Memory: 640 MB
  Bus Speed: 133 MHz
  Boot ROM Version: 4.2.5f1

GeForce FX 5200:

  Chipset Model: GeForce FX 5200
  Type: Display
  Bus: AGP
  Slot: SLOT-1
  VRAM (Total): 256 MB
  Vendor: nVIDIA (0x10de)
  Device ID: 0x0321
  Revision ID: 0x00b1
  ROM Revision: 2060
  Displays:

Apple Studio Display:
  Display Type: CRT
  Resolution: 1400 x 1050 @ 75 Hz
  Depth: 32-bit Color
  Core Image: Supported
  Main Display: Yes
  Mirror: Off
  Online: Yes
  Quartz Extreme: Supported

---

