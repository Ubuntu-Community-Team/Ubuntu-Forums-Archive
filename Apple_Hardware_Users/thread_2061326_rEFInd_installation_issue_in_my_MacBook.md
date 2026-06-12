---
title: "rEFInd installation issue in my MacBook"
date: 2012-09-22
forum: Apple Hardware Users
---

### Post by MacWeb on 2012-09-22
Hi 

I use this guide to install Ubuntu on my MacBook Pro.

[http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html)

1-	I complete the "Fixing the Installation" correctly

Disk size is 1465149168 sectors (698.6 GiB)
MBR disk identifier: 0x00000000
MBR partitions:
Number  Boot  Start Sector   End Sector   Status      Code
   1                     1   1465149167   primary     0xEE

2-	I get rEFInd installed and booting when I use

**sudo bless --mount /efi --setBoot --file /efi/efi/refind/refind_ia32.efi**

I´ve use refind_ia32.efi because
[B] ioreg -l -p IODeviceTree | grep firmware-abi
 | |   "firmware-abi" = <"EFI32">
[/B]
Note: Ubuntu doesn´t boot anymore.

3-	After that I just can boot with Super GRUB 2 Disk witch I think it´s normal because rEFInd is not ready to book Ubuntu.

4-	Super GRUB 2  can find Ubuntu Grub on my disk boot partition, and I can boot Ubuntu from there.

5- 	I am stuck to complete the following step.

[B]sudo mkdir /boot/efi  		OK
sudo mount /dev/sda1 /boot/efi 	OK
ls /boot/efi 					OK[/B]
note: I get the list of /EFI files in EFI partition

sudo apt-get install grub-efi

**Here I have one problem.**

 [B]ioreg -l -p IODeviceTree | grep firmware-abi
 | |   "firmware-abi" = <"EFI32">[/B]

I am using a MacBookPro2,2 and I think I am running a Ubuntu 64bit

So I use sudo apt-get install grub-efi because it seams that it will install the package that's appropriate for your system.
Is this correct ?
This command seams that runs fine.

**sudo mkdir /boot/efi/efi/ubuntu/      OK**
note: I check my EFI partition and I did see the new directory  efi/efi/ubuntu/

sudo grub-install 

PROBLEM: command doesn´t give any output just list the command help

So I tried :
sudo grub-install --root-directory=/boot/efi/efi/ubuntu /dev/sda5

I get this warnings:
warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
error: if you really want blocklists, use --force.

I am stuck here I can´t run the grub-install.

I will appreciate some tip to complete this installation.

Thanks in advance,

Anthony

**Extra Information:**

GPT fdisk (gdisk) version 0.8.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Disk /dev/disk0: 1465149168 sectors, 698.6 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): D5C2FE4C-3589-4083-93C8-8DA012B095D4
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1465149134
Partitions will be aligned on 8-sector boundaries
Total free space is 526749 sectors (257.2 MiB)

I would like to install other OS so I have the following partitions:
  SHA is a Shared partition.

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI System Partition
   2          409640      1016034639   484.3 GiB   AF00  MacOS_SL
   3      1016296784      1153927783   65.6 GiB    AF00  MacOS_TIGER
   4      1154189928      1158096183   1.9 GiB     AF00  SHA
   5      1158359040      1158748159   190.0 MiB   0700  Boot
   6      1158748160      1275934719   55.9 GiB    0700  Ubuntu
   7      1275934720      1283747839   3.7 GiB     8200  Swap
   8      1283747840      1400934399   55.9 GiB    0700  Kubuntu
   9      1400934400      1465147391   30.6 GiB    0700  BT5
  99      1158096184      1158358327   128.0 MiB   EF02  BIOS boot partition

---

