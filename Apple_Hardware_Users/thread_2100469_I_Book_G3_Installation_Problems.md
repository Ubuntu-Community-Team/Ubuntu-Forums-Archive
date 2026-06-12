---
title: "I Book G3 Installation Problems"
date: 2013-01-01
forum: Apple Hardware Users
---

### Post by 122jdh on 2013-01-01
Trying to install Ubuntu 12.04 LTS PPC, but I run into all types of errors.
My IBook22 G3 specs are:
OS: MAC OS X 10.3.9
600 MHz PPC 750FX (G3) CPU 512k level 2 cache
256 MB RAM
20 GB HDD
LG CD-ROM CRN-8245B
2X AGP ATI Mobility Radeon 16 MB of VRAM

I'm using a CD-RW and I burned the ISO with CyberLink Power2Go 8 at x4 on a Sony DVD-RW AW-Q1T0A Drive.
I'm also using a 2GB MicroSD card with an USB adapter (both San Disk)(i have a San Disk flash drive 8GB I could use but would need to back up the data first)

The IBook doesnt recognize the USB or the CD (when not in Mac OS X 10.3.9) nor will it boot from it when holding "C" during startup so I have to go into Open Firmware. Using these commands i get the following errors:

Command: boot CD,\INSTALL\YABOOT (Without ethernet cord plugged in)
Error: can't open: enet:bootp

Command: boot CD,\\TBXI
Error: BOOTP/BSDP failed: no filename specified can't OPEN: enet:bootp

Sometimes when using either command for a CD I get this
"block0 is bad can't open"

Command: boot USB,\\TBXI
Error: BOOTP/BSDP failed: no filename specified can't OPEN: enet:bootp

Command: boot usb,\install\yaboot
Error: BOOTP/BSDP failed: no filename specified can't OPEN: enet:bootp



I put the vmlinux, yaboot, yaboot.conf files on the root of the HDD, tho I cant find where initrd.gz is, the closest thing is Packages.gz. When I try the following commands:

Command: boot hd:0,yaboot
Error: DISK-LABEL: LOAD (NONINTERPOSED) not supportedload-size=0 adler32=1 LOAD-SIZE is too small

Command: boot hd:0,\\tbxi
Error: DISK-LABEL: LOAD (NONINTERPOSED) not supportedload-size=0 adler32=1 LOAD-SIZE is too small

I used the following guides as help:
[https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick](https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick) (used manual approach)

[https://help.ubuntu.com/10.04/installation-guide/powerpc/boot-drive-files.html](https://help.ubuntu.com/10.04/installation-guide/powerpc/boot-drive-files.html)

[https://help.ubuntu.com/10.04/installation-guide/powerpc/ch05s01.html#boot-newworld](https://help.ubuntu.com/10.04/installation-guide/powerpc/ch05s01.html#boot-newworld)

What is wrong with this machine, that wont let it start yaboot?

---

