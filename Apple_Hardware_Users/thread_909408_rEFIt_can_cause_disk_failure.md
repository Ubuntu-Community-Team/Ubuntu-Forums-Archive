---
title: "rEFIt can cause disk failure?"
date: 2008-09-03
forum: Apple Hardware Users
---

### Post by PaulFXH on 2008-09-03
I've been using a MB (C2D) for about a year with 11 partitions on a 160 GB HDD. I use these partitions for OS X (10.5.4) and four Linux OSes (including Hardy Heron).
I use rEFIt and Grub for my multibooting setup.
Yesterday, I ran into a problem in OS X which looked like it was permissions/priviledges-related but I was unable to fix the problem with Repair Permissions (errored out with 
> The underlying task reported failure on exit
I then tried to reinstall OS X on its partition but the installer claimed that installation was not possible because of a Volume Check error.
So, into Disk Utility to try and erase everything in the OS X partition. This seemed to be going fine until it errored out at the last minute saying
> Disk Utility Internal Error
Please quit and relaunch Disk Utility
However, still get the same error no matter how many times I try the erase.
I spoke at length with Apple about this problem and they, perhaps understandably, tended to blame rEFIt and the large number of partitions on my HD as perhaps interfering with the directory structure on the OS X partition.
I would like to ask if anybody has ever seen anything even approaching this as a consequence of multibooting using rEFIt?

---

### Post by cyberdork33 on 2008-09-03
rEFIt has nothing to do with all that so I don't know how you could blame it. The Apple people apparently spread a lot of FUD about rEFIt for some reason as can be evidenced by a number of posts here.

Based on what you are saying here, I have gotten a similar error in OSX before (without any other partitions on the disk). I was unable to repair it with the utilities available. The only thing that recovered my system was Disk Warrior. 

However, since you said you have so many partitions, I would assume that you are using a normal MBR style partition table with no GPT. This would be the reason that OS X will not install. It will only allow installs to GPT disks.

---

### Post by PaulFXH on 2008-09-03
> **cyberdork33 said:**
> rEFIt has nothing to do with all that so I don't know how you could blame it. The Apple people apparently spread a lot of FUD about rEFIt for some reason as can be evidenced by a number of posts here.
Thanks for this lucid explanation. That clears up a lot for me. I'm glad to hear rEFIt is not the culprit as I'll be using it later today to restore my setup [Although I now have the problem of knowing what in fact WAS the culprit:)]

> **cyberdork33 said:**
> Based on what you are saying here, I have gotten a similar error in OSX before (without any other partitions on the disk). I was unable to repair it with the utilities available. The only thing that recovered my system was Disk Warrior. 
Maybe it's time for me to save up and buy Disk Warrior. I know the guys in the repair shops speak very highly of it.

> **cyberdork33 said:**
> However, since you said you have so many partitions, I would assume that you are using a normal MBR style partition table with no GPT. This would be the reason that OS X will not install. It will only allow installs to GPT disks.
Well, actually, both a MBR and a GPT table appear in the partition section which is available on the rEFIt menu page. I don't really know a whole lot about this area but I did my partitioning with Parted Magic.
Is GPT vs MBR an option I can consider as I prepare to carve up my disk space again if GPT will allow me to re-install OS X without erasing the whole disk (which is what I had to do this time)?

---

### Post by cyberdork33 on 2008-09-03
> **PaulFXH said:**
> Is GPT vs MBR an option I can consider as I prepare to carve up my disk space again if GPT will allow me to re-install OS X without erasing the whole disk (which is what I had to do this time)?
I honestly don't know how you can get much more than a couple "legacy OS" installs without going to an MBR disk. To get around the installer check for that, you can install normally, create an image of the partition on an external drive or so, then carve up your main drive and restore the OSX image to the correct MBR partition.

---

### Post by PaulFXH on 2008-09-03
Thanks for the reply.
However, I really believe that what I have set up on my MB HD is a GPT partition system.
Parted Magic refused to allow me to create extended partitions and, in consequence, logical partitions. All eleven partitions are primary. An MBR system allows a maximum of four.
It seems that Parted Magic knew that the existing hfsplus partition will only be happy in a GPT table.
Actually, the reason I couldn't reinstall OS X was because its partition had been damaged somehow or other.

---

### Post by cyberdork33 on 2008-09-03
> **PaulFXH said:**
> Thanks for the reply.
However, I really believe that what I have set up on my MB HD is a GPT partition system.
Parted Magic refused to allow me to create extended partitions and, in consequence, logical partitions. All eleven partitions are primary. An MBR system allows a maximum of four.
It seems that Parted Magic knew that the existing hfsplus partition will only be happy in a GPT table.
Actually, the reason I couldn't reinstall OS X was because its partition had been damaged somehow or other.Yep from all that you have posted so far, that sounds more likely. You might make a nice detailed post on how you have so many bootable Linux installs on your machine someday :)

---

### Post by PaulFXH on 2008-09-04
I am quite sure that there's nothing in what I have done that will either surprise or enlighten you. It's all very straightforward and much, if not all of it, I picked up from this forum.
By no means does this merit a detailed howto, but here are the esential parts of how I built my multiboot system on my MB (C2D, 160 GB HDD)

1. Install Mac OS X
2. Use Parted Magic to create as many extra partitions as you will need (I created 9; 8 are ext3 and 1 linux-swap)
3. Install rEFIt in OS X
4. Install Ubuntu (I used partition #9 for ubuntu / and  #10 for ubuntu /home)
5. Put Ubuntu Grub bootloader in MBR

Now when you start the Mac, the rEFIt screen will allow you to choose either OS X or Linux/Penguin. Choosing Linux brings you to a Grub menu.

6. Install other Linux OSes (I created a / and a /home for each OS. Then I put Foresight in partitions 3 & 4, openSUSE in partitions 5 & 6, and Sidux in partitions 7 & 8. Totally unecessarily, Foresight refuses to install on anything but the first 4 partitions). In the case of each new OS, I either did NOT install a bootloader or I put it in the root partition of the OS itself. IOW, DON'T put it in the MBR)
7. Now just go into Ubuntu and modify the /boot/grub/menu.lst file to include all of the additional Linux OSes you want to boot through Ubuntu's Grub
8. Reboot

That's all there is to it.
Indeed, I have another 7 Linux OSes on an external USB drive that I can similarly boot from Ubuntu's Grub.

---

### Post by cyberdork33 on 2008-09-04
> **PaulFXH said:**
> 4. Install Ubuntu (I used partition #9 for ubuntu / and  #10 for ubuntu /home)
5. Put Ubuntu Grub bootloader in MBR

Now when you start the Mac, the rEFIt screen will allow you to choose either OS X or Linux/Penguin. Choosing Linux brings you to a Grub menu.

6. Install other Linux OSes (I created a / and a /home for each OS. Then I put Foresight in partitions 3 & 4, openSUSE in partitions 5 & 6, and Sidux in partitions 7 & 8. Totally unecessarily, Foresight refuses to install on anything but the first 4 partitions). In the case of each new OS, I either did NOT install a bootloader or I put it in the root partition of the OS itself. IOW, DON'T put it in the MBR)
7. Now just go into Ubuntu and modify the /boot/grub/menu.lst file to include all of the additional Linux OSes you want to boot through Ubuntu's Grub
8. RebootI guess this is the issue that is different for you as opposed to others... GRUB should only be capable of "booting" from one of the 4 MBR partitions... that's it. This is especially true since the supporting GRUB files (like menu.lst) are not on a partition that is in the MBR... Are you using GRUB-efi or something? How are you able to get GRUB to boot a partition other than one defined in the MBR?

> **PaulFXH said:**
> Indeed, I have another 7 Linux OSes on an external USB drive that I can similarly boot from Ubuntu's Grub.That is even MORE suprising... Almost nobody can get "booting from an external hard drive" to work... period. (other than placing a /boot partition on the internal drive within the MBR table).

What specific hardware are you on?

---

### Post by PaulFXH on 2008-09-04
I have been running a multiboot system like this on an old Dell desktop with a 160 GB Philips usb HDD attached for more than two years. I have never had any problems with it.
When I got the MacBook about a year ago, I simply replicated what I had done on the Dell.
If there is anything at all to be learnt, it is in how to set up the /boot/grub/menu.lst  Note that, in both cases, ALL booting (other than OS X on the Mac) is done through Ubuntu's Grub. I don't go near any of the other boot menus.
So, for example, on the Dell, this is an example of parts of my /boot/grub/menu.lst file

```
title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=/dev/sda6 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet


title		Foresight Linux vmlinuz-2.6.25.9-2-fl.smp.gcc4.1.x86.i686
root		(hd0,5)
kernel		/boot/foresight/vmlinuz-2.6.25.9-2-fl.smp.gcc4.1.x86.i686 root=/dev/sdb9 quiet ro vga=0x317 splash 
initrd		/boot/foresight/initrd-2.6.25.9-2-fl.smp.gcc4.1.x86.i686.img
savedefault
boot

title		Arch Linux
root		(hd0,5)
kernel		/boot/arch/vmlinuz26 root=/dev/sdb8 ro 
initrd		/boot/arch/kernel26.img
savedefault
boot

title		Kurumin Linux 2.6.24-19-generic
root		(hd0,5)
kernel		/boot/kurumin/vmlinuz-2.6.24-19-generic root=/dev/sdb15 vga=791  
initrd		/boot/kurumin/initrd.img-2.6.24-19-generic


title		FreeBSD 7.0
root		(hd0,3,a)
kernel		/boot/loader

title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

Here, only Ubuntu, FreeBSD and WindowsXP are stored on the Dell internal HDD. Foresight, Kurumin and Arch are all stored on the external usb drive.
In these cases, the vmlinuz and initrd.img files for each OS must be available within the /boot on the Ubuntu / partition on the internal drive which is the only drive that is bootable in my situation. For this reason, the root line for all the OSes externally stored is the same as for Ubuntu because that's where the bootloader must look for the vmlinuz and initrd.img files of whatever OS is being booted. 
However, once booting has started, Grub needs to be directed to where all the rest of the stuff is which is its partition on the external drive.
So, you can see in /boot/grub/menu.lst for Foresight, Grub is first directed to (hd0,5) in the root line (which is /dev/sda6). However, it then is redirected to /dev/sda9 in the kernel line.

Basically, there's very little more to it than just that. I haven't at all done anything especial on the Mac to get the same thing to work fine other than install rEFIt to handle booting the OS X

---

### Post by cyberdork33 on 2008-09-04
> **PaulFXH said:**
> I have been running a multiboot system like this on an old Dell desktop with a 160 GB Philips usb HDD attached for more than two years. I have never had any problems with it. 
not suprised, this is really just a Mac-specific issue...
> **PaulFXH said:**
> When I got the MacBook about a year ago, I simply replicated what I had done on the Dell.
If there is anything at all to be learnt, it is in how to set up the /boot/grub/menu.lst  Note that, in both cases, ALL booting (other than OS X on the Mac) is done through Ubuntu's Grub. I don't go near any of the other boot menus.Yes, I understand that. You can also chainload bootloaders so that each install of linux can keep it's own menu.lst up to date properly when you do updates. For example, on my Dell Inspiron, I have a small ext2 partition at the front of the drive with Grub installed there. the menu.lst only contains chainloader entries to load grub on each of the individual Linux installs> You have to go through two menus, but you don't have to manually edit the menu.lst all the time.

> **PaulFXH said:**
> So, for example, on the Dell, this is an example of parts of my /boot/grub/menu.lst file

```
title        Ubuntu 8.04, kernel 2.6.24-19-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-19-generic root=/dev/sda6 ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet
```See, for most (on the macs), this simply would not work. Because hd0,5 is not an entry in the MBR partition table, then grub cannot even tell it exists. What do the MBR table and GPT look like on your Mac? (In OS X, in /Applications/Utilities there is a partition inspector that is part of rEFIt. You can copy and paste the table data from there. the output of 'sudo fdisk -l' in ubuntu would be nice too to compare against.

> **PaulFXH said:**
> Here, only Ubuntu, FreeBSD and WindowsXP are stored on the Dell internal HDD. Foresight, Kurumin and Arch are all stored on the external usb drive.
In these cases, the vmlinuz and initrd.img files for each OS must be available within the /boot on the Ubuntu / partition on the internal drive which is the only drive that is bootable in my situation. OK, yea this is similar to the work around that has been found generally for booting from an external drive. The /boot partition for the OS has to be on the internal disk (basically it needs the kernel) Once the kernel loads then the USB disk is accessible for other things. 

> **PaulFXH said:**
> Basically, there's very little more to it than just that. I haven't at all done anything especial on the Mac to get the same thing to work fine other than install rEFIt to handle booting the OS X
What hardware and version is it? Are you completely up-to-date with firmware, etc?
```
sudo dmidecode -s system-product-version
sudo dmidecode -s bios-version
```

---

### Post by PaulFXH on 2008-09-05
> **cyberdork33 said:**
> not suprised, this is really just a Mac-specific issue...
OK
> **cyberdork33 said:**
> Yes, I understand that. You can also chainload bootloaders so that each install of linux can keep it's own menu.lst up to date properly when you do updates. For example, on my Dell Inspiron, I have a small ext2 partition at the front of the drive with Grub installed there. the menu.lst only contains chainloader entries to load grub on each of the individual Linux installs> You have to go through two menus, but you don't have to manually edit the menu.lst all the time.
I need to manually edit /boot/grub/menu.lst in Ubuntu any time there is a kernel change in any of the other OSes. If the OS is also stored on the usb drive, I must copy the vmlinuz and initrd.img files to the /boot directory of the Ubuntu / partition as otherwsie Grub won't see the new kernel.

> **cyberdork33 said:**
> See, for most (on the macs), this simply would not work. Because hd0,5 is not an entry in the MBR partition table, then grub cannot even tell it exists. What do the MBR table and GPT look like on your Mac? (In OS X, in /Applications/Utilities there is a partition inspector that is part of rEFIt. You can copy and paste the table data from there.
Here you go,

> *** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    188333191  Mac OS X HFS+
 3      188333192    203238314  EFI System (FAT)
 4      203238315    218323349  Basic Data
 5      218323350    233215604  Basic Data
 6      233215605    248300639  Basic Data
 7      248300640    263080439  Basic Data
 8      263080440    278133344  Basic Data
 9      278133345    292800689  Basic Data
 10      292800690    308190959  Basic Data
 11      308190960    312576704  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    188333191  af  Mac OS X HFS+
 3 *    188333192    203238314  83  Linux
 4      203238315    218323349  83  Linux

MBR contents:
 Boot Code: GRUB

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 188333192:
 Boot Code: None
 File System: ext3
 Listed in GPT as partition 3, type EFI System (FAT)
 Listed in MBR as partition 3, type 83  Linux, active

Partition at LBA 203238315:
 Boot Code: None
 File System: ext3
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 83  Linux

Partition at LBA 218323350:
 Boot Code: None
 File System: ext3
 Listed in GPT as partition 5, type Basic Data

Partition at LBA 233215605:
 Boot Code: None
 File System: ext3
 Listed in GPT as partition 6, type Basic Data

Partition at LBA 248300640:
 Boot Code: None
 File System: ext3
 Listed in GPT as partition 7, type Basic Data

Partition at LBA 263080440:
 Boot Code: None
 File System: ext3
 Listed in GPT as partition 8, type Basic Data

Partition at LBA 278133345:
 Boot Code: None
 File System: ext3
Listed in GPT as partition 9, type Basic Data

Partition at LBA 292800690:
 Boot Code: None
 File System: ext3
 Listed in GPT as partition 10, type Basic Data

Partition at LBA 308190960:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 11, type Linux Swap


 > **cyberdork33 said:**
> the output of 'sudo fdisk -l' in ubuntu would be nice too to compare against.

> paul@ubuntu-mac:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  EFI GPT
/dev/sda2              26       11724    93961776   af  Unknown
/dev/sda3   *       11724       12651     7452561+  83  Linux
/dev/sda4           12652       13590     7542517+  83  Linux

 > **cyberdork33 said:**
> OK, yea this is similar to the work around that has been found generally for booting from an external drive. The /boot partition for the OS has to be on the internal disk (basically it needs the kernel) Once the kernel loads then the USB disk is accessible for other things. 
That's it.

> **cyberdork33 said:**
> What hardware and version is it? Are you completely up-to-date with firmware, etc?
```
sudo dmidecode -s system-product-version
sudo dmidecode -s bios-version
```

> paul@ubuntu-mac:~$ sudo dmidecode -s system-version
1.0

> paul@ubuntu-mac:~$ sudo dmidecode -s bios-version
    MB21.88Z.00A5.B07.0706270922


---

### Post by mabovo on 2008-09-05
Cara, matou a cobra e mostrou o pau !

I would just want to install WinXP and I couldn't because a separated /home partition  : - ((

---

### Post by cyberdork33 on 2008-09-05
Interesting, you only have the four partitions listed in the MBR table (as expected). I'll have to look over your data here in more detail and see if I can find anything specific. This is a big deal. I think you are the only one that has successfully reporting doing anything like this.

PS You missed a part of one of the dmidecode commnds.

> **mabovo said:**
> I would just want to install WinXP and I couldn't because a separated /home partition  : - ((
You can put the home partition after windows and it will work fine. once the kernel loads all the partition in the GPT become available to the system. so you can have home, swap, or whatever on a partition higher than #4 and it will be fine as long as the root partition (or /boot if you have a separate partition) is one of the primary (in the first 4).

---

### Post by PaulFXH on 2008-09-05
> **cyberdork33 said:**
> 
PS You missed a part of one of the dmidecode commnds.

Yes, but the first time I ran
```
sudo dmidecode -s system-product-version
```
I got this error
> Invalid string keyword: system-product-version
Valid string keywords are:
  bios-vendor
  bios-version
  bios-release-date
  system-manufacturer
  system-product-name
  system-version
  system-serial-number
  system-uuid
  baseboard-manufacturer
  baseboard-product-name
  baseboard-version
  baseboard-serial-number
  baseboard-asset-tag
  chassis-manufacturer
  chassis-type
  chassis-version
  chassis-serial-number
  chassis-asset-tag
  processor-family
  processor-manufacturer
  processor-version
  processor-frequency

I got the same thing when I ran it again after seeing your post.
But, I tried one more time and got this (no idea why the error occurred although system-product-version is NOT in the list of valid string keywords):
> # dmidecode 2.9
SMBIOS 2.4 present.
37 structures occupying 1429 bytes.
Table at 0x000E0000.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
        Vendor: Apple Inc.
        Version:     MB21.88Z.00A5.B07.0706270922
        Release Date: 06/27/07
        ROM Size: 2048 kB
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

Handle 0x0001, DMI type 1, 27 bytes
System Information
        Manufacturer: Apple Inc.
        Product Name: MacBook2,1
        Version: 1.0
        Serial Number: xxxxxxxxxxxx
        UUID: xxxxxxxxxxxxxxxxxxxxxxxxxxxx
        Wake-up Type: Power Switch
        SKU Number: System SKUNumber
        Family: MacBook

Handle 0x0002, DMI type 2, 16 bytes
Base Board Information
        Manufacturer: Apple Inc.
        Product Name: Mac-F4208CAA
        Version: PVT
        Serial Number: 1
        Asset Tag: Base Board Asset Tag
        Features:
                Board is a hosting board
                Board is replaceable
        Location In Chassis: Part Component
        Chassis Handle: 0x0003
        Type: Unknown
        Contained Object Handles: 0

Handle 0x0003, DMI type 3, 21 bytes
Chassis Information
        Manufacturer: Apple Inc.
        Type: Notebook
        Lock: Not Present
        Version: Mac-F4208CAA
        Serial Number: xxxxxxxxxxxxxxxxxxxx
        Asset Tag: Asset Tag
        Boot-up State: Safe
        Power Supply State: Safe
        Thermal State: Other
        Security Status: Other
        OEM Information: 0x00000000
        Height: Unspecified
        Number Of Power Cords: Unspecified
        Contained Elements: 0

Handle 0x0004, DMI type 32, 20 bytes
System Boot Information
        Status: No errors detected

Handle 0x0005, DMI type 13, 22 bytes
BIOS Language Information
        Installable Languages: 1
                <BAD INDEX>
        Currently Installed Language: Not Specified

Handle 0x0106, DMI type 12, 5 bytes
System Configuration Options

Handle 0x0107, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: None
        Internal Connector Type: None
        External Reference Designator: DVI
        External Connector Type: Other
        Port Type: Video Port

Handle 0x0108, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: None
        Internal Connector Type: None
        External Reference Designator: USBA
        External Connector Type: Access Bus (USB)
        Port Type: USB

Handle 0x0109, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: None
        Internal Connector Type: None
        External Reference Designator: USBC
        External Connector Type: Access Bus (USB)
        Port Type: USB

Handle 0x010A, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: None
        Internal Connector Type: None
        External Reference Designator: 1394A
        External Connector Type: IEEE 1394
        Port Type: Firewire (IEEE P1394)

Handle 0x010B, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: None
        Internal Connector Type: None
        External Reference Designator: Audio Out
        External Connector Type: Mini Jack (headphones)
        Port Type: Audio Port

Handle 0x010C, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: None
        Internal Connector Type: None
        External Reference Designator: Microphone
        External Connector Type: Mini Jack (headphones)
        Port Type: Audio Port

Handle 0x010D, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: None
        Internal Connector Type: None
        External Reference Designator: RJ-45
        External Connector Type: RJ-45
        Port Type: Network Port

Handle 0x010E, DMI type 9, 13 bytes
System Slot Information
        Designation: AirPort
        Type: x1 PCI Express
        Current Usage: Available
        Length: Short
        ID: 2
        Characteristics:
                3.3 V is provided
                Hot-plug devices are supported
                SMBus signal is supported

Handle 0x010F, DMI type 10, 6 bytes
On Board Device Information
        Type: Video
        Status: Enabled
        Description: Integrated Graphics Controller

Handle 0x0110, DMI type 10, 6 bytes
On Board Device Information
        Type: Sound
        Status: Enabled
        Description: Azalia Audio Codec

Handle 0x0111, DMI type 10, 6 bytes
On Board Device Information
        Type: Ethernet
        Status: Enabled
        Description: Yukon Ethernet Controller

Handle 0x0112, DMI type 10, 6 bytes
On Board Device Information
        Type: Other
        Status: Enabled
        Description: SATA

Handle 0x0113, DMI type 10, 6 bytes
On Board Device Information
        Type: Other
        Status: Enabled
        Description: PATA

Handle 0x0114, DMI type 10, 6 bytes
On Board Device Information
        Type: Other
        Status: Enabled
        Description: Sudden Motion Sensor

Handle 0x0115, DMI type 136, 6 bytes
OEM-specific Type
        Header and Data:
                88 06 15 01 00 00

Handle 0x0116, DMI type 4, 35 bytes
Processor Information
        Socket Designation: U2E1
        Type: Central Processor
        Family: Unknown
        Manufacturer: Intel(R) Corporation
        ID: F6 06 00 00 FF FB EB BF
        Version: Intel(R) Core(TM)2 CPU
        Voltage: 1.6 V
        External Clock: 166 MHz
        Max Speed: 2160 MHz
        Current Speed: 2160 MHz
        Status: Populated, Enabled
        Upgrade: ZIF Socket
        L1 Cache Handle: 0x0119
        L2 Cache Handle: 0x0117
        L3 Cache Handle: Not Provided
        Serial Number: Not Specified
        Asset Tag: Unknown
        Part Number: Not Specified

Handle 0x0117, DMI type 7, 19 bytes
Cache Information
        Socket Designation: Unknown
        Configuration: Enabled, Not Socketed, Level 2
        Operational Mode: Write Back
        Location: Internal
        Installed Size: 4096 KB
        Maximum Size: 4096 KB
        Supported SRAM Types:
                Asynchronous
        Installed SRAM Type: Asynchronous
        Speed: Unknown
        Error Correction Type: Single-bit ECC
        System Type: Unified
        Associativity: 16-way Set-associative

Handle 0x0118, DMI type 7, 19 bytes
Cache Information
        Socket Designation: Unknown
        Configuration: Enabled, Not Socketed, Level 1
        Operational Mode: Write Back
        Location: Internal
        Installed Size: 32 KB
        Maximum Size: 32 KB
        Supported SRAM Types:
                Asynchronous
        Installed SRAM Type: Asynchronous
        Speed: Unknown
        Error Correction Type: Single-bit ECC
        System Type: Instruction
        Associativity: 8-way Set-associative

Handle 0x0119, DMI type 7, 19 bytes
Cache Information
        Socket Designation: Unknown
        Configuration: Enabled, Not Socketed, Level 1
        Operational Mode: Write Back
        Location: Internal
        Installed Size: 32 KB
        Maximum Size: 32 KB
        Supported SRAM Types:
                Asynchronous
        Installed SRAM Type: Asynchronous
        Speed: Unknown
        Error Correction Type: Single-bit ECC
        System Type: Data
        Associativity: 8-way Set-associative

Handle 0x011A, DMI type 4, 35 bytes
Processor Information
        Socket Designation: U2E1
        Type: Central Processor
        Family: Unknown
        Manufacturer: Intel(R) Corporation
        ID: F6 06 00 00 FF FB EB BF
        Version: Intel(R) Core(TM)2 CPU
        Voltage: 1.6 V
        External Clock: 166 MHz
        Max Speed: 2160 MHz
        Current Speed: 2160 MHz
        Status: Populated, Enabled
        Upgrade: ZIF Socket
        L1 Cache Handle: 0x011D
        L2 Cache Handle: 0x011B
        L3 Cache Handle: Not Provided
        Serial Number: Not Specified
        Asset Tag: Unknown
        Part Number: Not Specified

Handle 0x011B, DMI type 7, 19 bytes
Cache Information
        Socket Designation: Unknown
        Configuration: Enabled, Not Socketed, Level 2
        Operational Mode: Write Back
        Location: Internal
        Installed Size: 4096 KB
        Maximum Size: 4096 KB
        Supported SRAM Types:
                Asynchronous
        Installed SRAM Type: Asynchronous
        Speed: Unknown
        Error Correction Type: Single-bit ECC
        System Type: Unified
        Associativity: 16-way Set-associative

Handle 0x011C, DMI type 7, 19 bytes
Cache Information
        Socket Designation: Unknown
        Configuration: Enabled, Not Socketed, Level 1
        Operational Mode: Write Back
        Location: Internal
        Installed Size: 32 KB
        Maximum Size: 32 KB
        Supported SRAM Types:
                Asynchronous
        Installed SRAM Type: Asynchronous
        Speed: Unknown
        Error Correction Type: Single-bit ECC
        System Type: Instruction
        Associativity: 8-way Set-associative

Handle 0x011D, DMI type 7, 19 bytes
Cache Information
        Socket Designation: Unknown
        Configuration: Enabled, Not Socketed, Level 1
        Operational Mode: Write Back
        Location: Internal
        Installed Size: 32 KB
        Maximum Size: 32 KB
        Supported SRAM Types:
                Asynchronous
        Installed SRAM Type: Asynchronous
        Speed: Unknown
        Error Correction Type: Single-bit ECC
        System Type: Data
        Associativity: 8-way Set-associative

Handle 0x011E, DMI type 16, 15 bytes
Physical Memory Array
        Location: System Board Or Motherboard
        Use: System Memory
        Error Correction Type: None
        Maximum Capacity: 4 GB
        Error Information Handle: Not Provided
        Number Of Devices: 2

Handle 0x011F, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x011E
        Error Information Handle: No Error
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 512 MB
        Form Factor: DIMM
        Set: None
        Locator: DIMM0
        Bank Locator: BANK 0
        Type: DDR2
        Type Detail: Synchronous
        Speed: 667 MHz (1.5 ns)
        Manufacturer: 0xAD00000000000000
        Serial Number: 0x00005028
        Asset Tag: Unknown
        Part Number: 0x48594D503536345336344350362D59352020

Handle 0x0120, DMI type 20, 19 bytes
Memory Device Mapped Address
        Starting Address: 0x00000000000
        Ending Address: 0x0001FFFFFFF
        Range Size: 512 MB
        Physical Device Handle: 0x011F
        Memory Array Mapped Address Handle: 0x0123
        Partition Row Position: 1
        Interleave Position: 1
        Interleaved Data Depth: 1

Handle 0x0121, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x011E
        Error Information Handle: No Error
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 512 MB
        Form Factor: DIMM
        Set: None
        Locator: DIMM1
        Bank Locator: BANK 1
        Type: DDR2
        Type Detail: Synchronous
        Speed: 667 MHz (1.5 ns)
        Manufacturer: 0xAD00000000000000
        Serial Number: 0x00001001
        Asset Tag: Unknown
        Part Number: 0x48594D503536345336344350362D59352020

Handle 0x0122, DMI type 20, 19 bytes
Memory Device Mapped Address
        Starting Address: 0x00020000000
        Ending Address: 0x0003FFFFFFF
        Range Size: 512 MB
        Physical Device Handle: 0x0121
        Memory Array Mapped Address Handle: 0x0123
        Partition Row Position: 2
        Interleave Position: 2
        Interleaved Data Depth: 1

Handle 0x0123, DMI type 19, 15 bytes
Memory Array Mapped Address
        Starting Address: 0x00000000000
        Ending Address: 0x0003FFFFFFF
        Range Size: 1 GB
        Physical Array Handle: 0x011E
        Partition Width: 0

Handle 0xFFFD, DMI type 127, 4 bytes
End Of Table


---

### Post by cyberdork33 on 2008-09-05
> **PaulFXH said:**
> Yes, but the first time I ran
```
sudo dmidecode -s system-product-version
```
I got this error

I got the same thing when I ran it again after seeing your post.
But, I tried one more time and got this (no idea why the error occurred although system-product-version is NOT in the list of valid string keywords):
Ah I see, I think that is supposed to be system-product-name. I think I got them mixed around somehow. Anywho, you gave the full dmidecode the last time, and the one line I wanted to see is in there:
```
Product Name: MacBook2,1
```

---

