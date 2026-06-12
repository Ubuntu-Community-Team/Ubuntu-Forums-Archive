---
title: "SATA driver install -  need help"
date: 2005-11-01
forum: Absolute Beginner Talk
---

### Post by janne5011 on 2005-11-01
Hi. i got a SATA disk. I have never bother before to install it but now need it so I know NOTHING of this from start:rolleyes: 
After some time spent on google i found a file I think can be the one .
As I understand tis what i need to do is install uppurt for RAID and this file do it:

"sis18x_2.6.10_1.00.00"
in the readme file it says:

"1. Files List
   - Makefile
   - sata_sis.c

   Since the ata_host_set structure is redefined from kernel-2.6.10,
   I have to part the sata_sis.c to different branch.

2. How to build the driver ?

   1. You have to prepare the kernel source. Downlad it / Untar it / and link it to /usr/src/linux
   2. Check you kernel version. Take 2.6.10 for an example, cd sis18x_2.6.10_1.00.00
   2. Change to administrator.
   3. Type " make " to build the driver
   4. Type " make install " to intall the sata_sis.ko module

3. How to use it ?
   1. To load the driver, use " modprobe sata_sis ". Or "load-18x"
   2. To unload the driver, type " rmmod sata_sis ". Or "unload-18x"
   3. For SATA devices will be named to /dev/sda, /dev/sdb, /dev/sdc etc,.
   4. For S-ATAPI devices will be named  to /dev/scd0, /dev/scd1, /dev/scd2, etc,.

4. Partion the disk

   If you disk does not have any partition, you have to create some first.
  	fdisk /dev/sd[a-d]

5. Mount the partition to somewhere
   After you get some partitions, mount it to somewhere to use.
   like, mount /dev/sda1 /mnt/dos  ....

6. Summary of Current Status
   1. Fedore Core-3 use kernel 2.6.9, at this release does not support S-ATAPI devices
   2. From kernel 2.6.10, libata port support S-ATAPI devices.
   3. MSI ODD device, model MS-8452T could not pass the identify command."

now the 2. questions
1 Shall I use this for kernel v.2.6.10 there  is another driver for 2.6.9.
or is it simply wrong?

2 how do I do this from 1. in readmefile "and link it to /usr/src/linux"? (in case I should try this att all...

SATA is enabled in bios but i still cant see no drive nowhere but I assume it appears with this raiddriver...
hmmm
:)

thanks

---

### Post by Kyral on 2005-11-01
Is Ubuntu already installed on another disk (IDE?) and you are adding this SATA HD? Or are you trying to install onto it?

---

### Post by janne5011 on 2005-11-01
[QUOTE=Kyral]Is Ubuntu already installed on another disk (IDE?) and you are adding this SATA HD? Or are you trying to install onto it?[/QUOTE]

Ubuntu is already installed on IDE:)

---

### Post by Kyral on 2005-11-01
Then the sata_sis module will already be on the system. First do

```
sudo modprobe sata_sis
```

and if you want to confirm that its there

```
lsmod
```

And find it in the list.

Then to get it to load at boot

```
sudo nano /etc/modules
```

and add sata_sis to the file and save it.

For the disk itself. Can I see output from "sudo fdisk -l" (preferably before and after you load the module so I can find out which disk it was)

---

### Post by janne5011 on 2005-11-01
[QUOTE=Kyral]Then the sata_sis module will already be on the system. First do

```
sudo modprobe sata_sis
```

and if you want to confirm that its there

```
lsmod
```

And find it in the list.

Then to get it to load at boot

```
sudo nano /etc/modules
```

and add sata_sis to the file and save it.

For the disk itself. Can I see output from "sudo fdisk -l" (preferably before and after you load the module so I can find out which disk it was)[/QUOTE]


here is after reboot:
Disk /dev/hda: 120,0 GB, 120034123776 byte
255 huvuden, 63 sektorer/sp&#229;r, 14593 cylindrar
Enheter = cylindrar av 16065 &#215; 512 = 8225280 byte

    Enhet Start     B&#246;rjan        Slut     Block    Id  System
/dev/hda1   *           1       14215   114181956   83  Linux
/dev/hda2           14216       14593     3036285    5  Ut&#246;kad
/dev/hda5           14216       14593     3036253+  82  Linux v&#228;xling / Solaris

dont look good:(
maybe must look in bios hm..:confused:

here is lsmod:

rocessor              23100  1 thermal
fan                     4740  0
usbhid                 30688  0
sata_sis                7552  0
libata                 47876  1 sata_sis
scsi_mod              124872  1 libata
sis900                 19456  0
mii                     5248  1 sis900
ehci_hcd               29448  0
ohci_hcd               18564  0
usbcore               104188  4 usbhid,ehci_hcd,ohci_hcd
ide_cd                 36996  1
cdrom                  33952  1 ide_cd
ide_disk               16128  3
ide_generic             1664  0
sis5513                14472  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,sis5513
unix                   24624  612
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon
janne@ubuntu:~$

---

### Post by Kyral on 2005-11-01
hmm...the module loaded right? And it loads after a reboot....(check with lsmod)

---

### Post by janne5011 on 2005-11-01
[QUOTE=Kyral]hmm...the module loaded right? And it loads after a reboot....(check with lsmod)[/QUOTE]

part of lsmod efter rebbot:


usbhid                 30688  0
sata_sis                7552  0
libata                 47876  1 sata_sis
scsi_mod              124872  1 libata

---

### Post by Kyral on 2005-11-01
Okay, so the Module loads. Are you sure that SiS makes your RAID Controller? Can you paste the output from lspci? Don't worry, we will fix this :D

---

### Post by janne5011 on 2005-11-01
here goes it goes...:D 
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 655 Host (rev 50)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS]: Unknown device 0003
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
0000:00:05.0 RAID bus controller: Silicon Integrated Systems [SiS]: Unknown device 0180 (rev 01)
0000:00:0b.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:00:0b.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:00:0b.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:00:0b.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV15DDR [GeForce2 Ti] (rev a4)

---

### Post by Kyral on 2005-11-01
Okay, so it is a SiS based RAID Controller. Hmm. Right now the only thing I can think of is that there is something in the BIOS. I'd go over it with a fine tooth comb and the manual to make sure.

---

### Post by janne5011 on 2005-11-01
ok in the manual it only tells how to do it with windows.I look again in bios...
thanks for all help! I think i at least is in right direction:smile: ..

---

### Post by Kyral on 2005-11-01
Keep me posted mkay (No pun intended ;P)

---

### Post by janne5011 on 2005-11-02
ok the big problem is fixed now. :p How can I format-make partition using the SATA disk using fdisk?

---

### Post by Kyral on 2005-11-02
Yea! It got fixed! Really its like partitioning any other drive with fdisk (you know how to use fdisk?)

Or you could use a GUI thing like GParted

---

### Post by janne5011 on 2005-11-02
yep SATA is ok and mounted and worked as i hoped:))))

big appluase and thanks Kyral :)

---

### Post by Kyral on 2005-11-02
Glad I could be of assistance. :D

---

