---
title: "HowTo read EFI Firmware version from Ubuntu"
date: 2010-05-20
forum: Apple Hardware Users
---

### Post by captwiggum on 2010-05-20
How do you view the macbook pro EFI Firmware version from Ubuntu? 
I do not have osx installed, only Ubuntu 10.04 x86_64 on a macbook pro 5,5.
Actually everything is working great with Lucid Lynx, I just want to know firmware ver.

dmidecode give me the below system info, but I do not clearly see the firmware ver is given.

Also I mounted the efi partition, but only one file on whole partition and its a binary:
/mnt/efi/EFI/APPLE/EXTENSIONS/Firmware.scap

```
$ dmidecode
...<snip>...
Handle 0x000E, DMI type 0, 24 bytes
BIOS Information
        Vendor: Apple Inc.
        Version:    MBP55.88Z.00AC.B03.0906151708
        Release Date: 06/15/09
        ROM Size: 4096 kB
        Characteristics:
                PCI is supported
                BIOS is upgradeable
                BIOS shadowing is allowed
                Boot from CD is supported
                Selectable boot is supported
                ACPI is supported
                IEEE 1394 boot is supported
                Smart battery is supported
                Function key-initiated network boot is supported
        BIOS Revision: 0.1

Handle 0x000F, DMI type 1, 27 bytes
System Information
        Manufacturer: Apple Inc.
        Product Name: MacBookPro5,5
        Version: 1.0
        Serial Number: W89463W366E
        UUID: 2C7A2E5D-968A-C64D-A1E4-92CD72BB3256
        Wake-up Type: Power Switch
        SKU Number: System SKU#
        Family: MacBook
...<snip>...

```

---

### Post by alexmurray on 2010-05-21
Try looking under /sys/firmware/efi/vars (you may need to load the efivars module first - note you may also have to have booted via efi for this to work as well...)

---

### Post by captwiggum on 2010-05-21
Thank you for the suggestions, but they did not hold the solution.

I am running Ubuntu 10.04 on a 13" macbook pro 5,5 booted from grub.efi. In fact there is no osx partition at all; no refit or bootcamp, just Ubuntu. So I am definitely running on an efi boot. 

There is no kernel module for efi. This find turns up no efi modules:
# find /lib/modules/2.6.32-22-generic/ -iname '*efi*'

There are no efi directories:
# dir /sys/firmware/efi
ls: cannot access /sys/firmware/efi: No such file or directory
# dir /proc/efi
ls: cannot access /proc/efi: No such file or directory

I was hoping someone would look at the dmidecode in the first post, and tell me that one of those fields holds the firmware information in some encoded or none obvious way. Here's to hoping...

---

