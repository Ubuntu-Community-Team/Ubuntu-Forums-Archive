---
title: "Problem with Macbook Pro (7, 1) install"
date: 2011-02-03
forum: Apple Hardware Users
---

### Post by Jabrouwer on 2011-02-03
So, like an idiot, I attempted to install Linux Mint (a variant of Ubuntu for those who don't know, anything that works for ubuntu should work for Mint) on my macbook pro.  The first time I booted to the liveCD and tried to install, when I got to the partition table and started the partition, the installer told me that nfs+ isn't supported.  A quick google search on another computer told me to boot OSX and turn off journaling.  

When I attempted to reboot into OSX to change the setting, my mac instead booted to the cd, and would do so repeatedly.  I also tried to use the  boot menu (grub?) to boot to the local disk, which never did anything.  After a while of this, I decided that maybe I would see what the liveCD could do for me.  I soon found out that gparted comes on the liveCD, and for some reason can re-partition nfs+ partitions when the built in partitioner couldn't.  I then used gparted to resize my OSX partition, and used the unused space to install Mint.  I can now boot into Mint, but choosing either OSX (32 bit) or OSX (64 bit) results i the following :

```
npvhash=4095
Darwin Kernel Version 10.6.0: Wed Nov 10 18:11:58 PST 2010; root:xnu-1504.8.26~3/RELEASE_X86_64
vm_page_bootstrap: 943059 free pages and 31789 wired pages
kext submap [0xffffff7f80600000 - 0xffffff8000000000], kernel text [0xffffff8000200000 - 0xffffff8000600000]
standard timeslicing quantum is 10000 us
mig_table_max_displ = 73
AppleACPICPU: ProcessorId=0 LocalApicId=0 Enabled
AppleACPICPU: ProcessorId=1 LocalApicId=1 Enabled
calling mpo_policy_init for TMSafetyNet
Security policy loaded: Safety net for Time Machine (TMSafety)
calling  mpo_policy_init for Sandbox
Security policy loaded: Seatbelt sandbox policy (Sandbox)
calling mpo_policy_init for Quarantine
Security policy loaded: Quarantine policy (Quarantine)
Copyright (c) 1982, 1986, 1989, 1991, 1993
           Blah blah, all rights reserved
MAC Framework successfully initialized
using 16384 buffer headers and 4096 cluster IO buffer headers
IOAPIC: Version 0c11 Vectors 64:87
ACPI:  System State [S0 S3 S4 S5] (S3)
AppleIntelCPUPowermanagment: initiallization complete
mbinit: done (64 MB memory set for mbuf pool)
From path: "uuid",
Waiting for boot volume with UUID 39324721-BC0C-3A55-999F-FB1CE6A77A97
Waiting on <dict ID="0"><key>IOProviderClass</key><string ID="1">IOResources</string><key>IOResourceMatch</key><string ID="2">boot-uuid-media</string></dict>
com.apple.AppleFSCompressionTypeZlib kmod start
com.apple.AppleFSCompressionTypeZlib load suceesed
AppleIntelCPUPowerManagmentClient: ready
USBMSC Identifier (non-unique): 6D18F1FFFFFF 0x59b 0x47a 0x100
USBMSC Identifier (non-unique): 000000009833 0x5ac 0x8403 0x9833
BICOEXIST off
wl0: Broadcom BCM432b 802.11 Wireless Controller
5.10.131.36
Firewire (OHCI) Lucent ID 5901 built-in now active, GUID d83062fffef97400; max speed s800
Still waiting for root device
```It repeats that last line for a long time.  Also, the 32 bit doesn't say "Still waiting for root device". 

I'm not a total idiot though, I do have a complete back up of my hard drive and the OSX install disk, but when I attempt to reinstall, repair or anything, the installer can't recognize my hard disk.  When I use the disk utility, it claims every partition is FAT, but when I open GParted, it recognized every partition correctly as nfs+, ext4 and swap.

I have no idea what to do now, I don't know how to re-install, or how to fix what I've done, any ideas?

---

