---
title: "Loaded Ubuntu/lost xp"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by greypoet on 2008-01-19
Hi all, I'd say I'm a newbie but I'll have to work hard to get to that level. 

AMD64 3500, 1GB ram, NVIDIA 6200(?), 2 Maxtor IDE HDD, 1 Seagate SATA, 8 logical drives. 

Loaded Ubuntu on HDD L:, no partitions. Now can't get back to XP. I have (Through stupidity) 2 versions of XP Home loaded on E: and F: one of them is missing NTLDR, so it says. Of course, that's the one the system tries to boot to from Ubuntu.

Spent a couple days reading everything I could find on this forum and other sources. Downloaded Super Grub but need a Windows puter to open the file.:confused: Also tried the one for linux but, same thing.:confused::confused:
Checked Grub but couldn't get anything there. Probably doing it wrong. 

Wouldn't mind learning proper parsing for the coding but am lost, obviously.

So... What's next. Thanks in advance for any help.
jim

---

### Post by thelatinist on 2008-01-19
> **greypoet said:**
> Hi all, I'd say I'm a newbie but I'll have to work hard to get to that level. 

AMD64 3500, 1mB ram, NVIDIA 6200(?), 2 Maxtor IDE HDD, 1 Seagate SATA, 8 logical drives. 

Loaded Ubuntu on HDD L:, no partitions. Now can't get back to XP. I have (Through stupidity) 2 versions of XP Home loaded on E: and F: one of them is missing NTLDR, so it says. Of course, that's the one the system tries to boot to from Ubuntu.

Spent a couple days reading everything I could find on this forum and other sources. Downloaded Super Grub but need a Windows puter to open the file.:confused: Also tried the one for linux but, same thing.:confused::confused:
Checked Grub but couldn't get anything there. Probably doing it wrong. 

Wouldn't mind learning proper parsing for the coding but am lost, obviously.

So... What's next. Thanks in advance for any help.
jim

Go to Applications > Accessories > Terminal.  Type the following two commands at the prompt, highlight and copy (ctrl + shift + c) the output and paste (ctrl + v) it here:

```
sudo fdisk -l
```

and

```
cat /boot/grub/menu.lst
```

---

### Post by greypoet on 2008-01-19
Hi, Thank you for that. One question: is "fdisk" the same as format disc" "? If not, what is it going to do?
Thanks in advance.
jim

---

### Post by ifthengoto on 2008-01-19
> **greypoet said:**
> Hi, Thank you for that. One question: is "fdisk" the same as format disc" "? If not, what is it going to do?
Thanks in advance.
jim

fdisk -l is a command you use in the terminal and it shows you what partitions you have and what is installed on them.

It does nothing to alter or change you system in any way.

Further info can me had by entering

```
man fdisk
```if you are not sure. 

Its good you ask.

(for most terminal commands you can enter "man" beforehand and the "manual" will tel you what the command actually means before you execute it).

(edit as per thelatinsit below).

---

### Post by thelatinist on 2008-01-19
> **ifthengoto said:**
> fdisk is a command you use in the terminal and it shows you what partitions you have and what is installed on them.

It does nothing to alter or change you system in any way.

This is not quite true; I wouldn't want to mislead the OP.  fdisk is a program that **can** be used to modify the partition table of your hard disk and set the format of each partition.  **However**, the -l switch after the command means 'list' and will just list the partitions on all your installed hard disks.

**greypoet**: you are right to ask questions if you don't understand what a command does.  Some commands in the terminal can cause serious damage to your system if used improperly.  Nobody here will ever complain if you ask for explanation (or if they do you should be questioning what they say anyway).

---

### Post by greypoet on 2008-01-19
Thanks people. Here goes:

> greypoet@greypoet-desktop:~$ sudo fdisk -l

Disk /dev/hda: 13.6 GB, 13662609408 bytes
195 heads, 63 sectors/track, 2172 cylinders
Units = cylinders of 12285 * 512 = 6289920 bytes
Disk identifier: 0x3838f743

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2173    13341951    c  W95 FAT32 (LBA)

Disk /dev/hdb: 15.3 GB, 15367790592 bytes
255 heads, 63 sectors/track, 1868 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb065b065

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1275    10241406    7  HPFS/NTFS
/dev/hdb2            1276        1867     4755240    f  W95 Ext'd (LBA)
/dev/hdb5            1276        1867     4755208+   7  HPFS/NTFS

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb87db87d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9352    75119908+  83  Linux
/dev/sda2            9353        9729     3028252+   5  Extended
/dev/sda5            9353        9729     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xb879b879

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3877    29310088+   c  W95 FAT32 (LBA)
/dev/sdb2            3878       10337    48837600    f  W95 Ext'd (LBA)
/dev/sdb5            3878        7753    29302528+   b  W95 FAT32
/dev/sdb6            7754       10337    19535008+   b  W95 FAT32
greypoet@greypoet-desktop:~$ cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=cd8b9a8c-4d24-4b46-bf95-0a58814679d6 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=cd8b9a8c-4d24-4b46-bf95-0a58814679d6 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=cd8b9a8c-4d24-4b46-bf95-0a58814679d6 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd2,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1


---

### Post by thelatinist on 2008-01-19
Okay, there is one more thing I need before I can help you. You have so many drives in there, and they are a mixture of ATA and IDE, that it's impossible for me to guess what number grub has given each of these drives.

Please post the output of:

```
cat /boot/grub/device.map
```

It should look something like this:

```
(hd0) /dev/hda
(hd1) /dev/hdb
(hd2) /dev/sda
(hd3) /dev/sdb
```

---

### Post by greypoet on 2008-01-19
I understand Latinist, sort of a dogs breakfast of informatiion.
Here is the information:
> greypoet@greypoet-desktop:~$ cat /boot/grub/device.map
(hd0)   /dev/hda
(hd1)   /dev/hdb
(hd2)   /dev/sda
(hd3)   /dev/sdb
Hope that helps. 
I find it interesting that what you expected is *precisely* what I have.:)

Thanks again.
jim

---

### Post by thelatinist on 2008-01-19
> **greypoet said:**
> I find it interesting that what you expected is *precisely* what I have.:)

Well, that was the most likely order. ;-)

Here's what you need to do:

(I am assuming you have XP installed on the 15.3 GB drive that Ubuntu is calling /dev/hdb since that is the drive that has two NTFS partitions.  If this is not the case, post back here so we can figure out which one it is.)

1. Enter the following command to back up your menu.lst file:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```

2. Enter the following command to open menu.lst for editing:

```
sudo gedit /boot/grub/menu.lst
```

3. Edit the line fourth from the end that currently reads

```
root (hd0,0)
```

to read

```
root (hd1,0)
```

Restart and try to boot into Windows XP.  If that does not work, repeat the steps above, replacing that line in menu.lst with the following:

```
root (hd1,4)
```

This will try to boot into your other installation of Windows XP.

If neither of those lines works, post back here and let us know.

---

### Post by torgrot on 2008-01-19
If you are trying to boot windows off of the second hard drive you will need to add the map command to your menu.lst for example to boot windows off of the second hard drive you will need 
map             (hd0) (hd1)
map             (hd1) (hd0)
in the menu.lst entry for windows.  I regularly boot windows off of my second hard drive using a grub enty like this
```

title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

```

torgot

---

### Post by greypoet on 2008-01-19
I think we're making headway. Tried both codes (hd1,0-hd1,4). First one got me "Loading" and a short line of gibberish ascii characters, the second "NTLDR is missing".
Tried something different: On DOS startup there is a line something like 'press F8 for boot popup'. Tried that and it gives me a list of HDD and CD drives. Tried each one with the following results.

HDD:PM-MAXTOR 91366U4
Error 12: Invalid device selected.

HDD:PS MAXTOR 51536U3
NTLDR is missing

HDD:3M ST380211AS
Error 22:No such partition

ST380211AS is my SATA drive so I am wondering if there is a software problem that is not allowing it to be read by Ubuntu? Checked all the connections and they are solid.
Would this be a possibility?
jim

---

### Post by greypoet on 2008-01-19
Thanks** torgot**, I'll give that a try once I find out about the SATA drive problem. 
All help vigorously appreciated.
jim

---

### Post by greypoet on 2008-01-21
Looking around at other posts and found a command: lspci  which brought up the following,

>  lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
**00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)**
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 VGA compatible controller: nVidia Corporation GeForce 7100 GS (rev a1)
04:09.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
04:09.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
04:09.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)

(SATA controller in bold)

Partial output of command lshw:
>    *-ide:1
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv


So to my uninformed mind, the commands are saying that Ubuntu sees the SATA drive but for some reason can't find it? Needs glasses?  :confused:

I'll keep looking if this doesn't help. 
jim

---

### Post by greypoet on 2008-01-22
I am really hoping someone can help with this. I've been spending 4 - 5 hours a day looking for answers on forums/canonical/ubuntu and still can't find anything. Seems I don't have to worry about the SATA drive after all. It's not where my XP boot files are. 
One good thing, I'm learning a lot about Ubuntu.
Thanks 
jim

---

### Post by thelatinist on 2008-01-22
Have you tried mounting all these drives in Ubuntu and verifying which one has XP on it?

Also, have you tried restoring NTLDR on /dev/sda4 using the recovery console?

---

### Post by greypoet on 2008-01-22
Thanks Latinist, but I think what I'm going to do is uninstall Ubuntu, check out xp files and reinstall Ubuntu. Any comments on the reality involved in doing this? Should that work or...?

---

### Post by thelatinist on 2008-01-22
> **greypoet said:**
> Thanks Latinist, but I think what I'm going to do is uninstall Ubuntu, check out xp files and reinstall Ubuntu. Any comments on the reality involved in doing this? Should that work or...?

What do you mean by "check out XP files"?  Uninstalling Ubuntu won't automatically make your XP installations bootable. You will have to restore ntloader, since Ubuntu overwrote it during the installation.

Frankly, what I would do is move all my data to one of those drives, format and repartition the others, install XP on one of them, and *then* install Ubuntu on another.

---

### Post by greypoet on 2008-01-23
Hello? What is the recovery console? I may be a little(or more) dense but haven't heard of this. How do you access it and how do I use it?
Thank you for furthering my education. Feel like I'm back in kindergarten. ](*,)  ;)

---

### Post by ifthengoto on 2008-01-23
> **greypoet said:**
> Hello? What is the recovery console? I may be a little(or more) dense but haven't heard of this. How do you access it and how do I use it?


I think it may be helpful to read the following links on the recovery console and the MBR (master boot record) and dual booting. It may take a while and seem complicated at first but it will provide very useful information. 

[Recovery Console]("http://support.microsoft.com/kb/314058")
[MBR]("http://en.wikipedia.org/wiki/Master_boot_record")
 also I have often used the [super grub disk]("http://supergrub.forjamari.linex.org/") to repair my MBR and [Herman]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html") has been indispensable to me. Also see this [Herman]("http://users.bigpond.net.au/hermanzone/") link on dual boot.

Its not as complicated as it seems...

---

### Post by thelatinist on 2008-01-23
> **greypoet said:**
> Hello? What is the recovery console? I may be a little(or more) dense but haven't heard of this. How do you access it and how do I use it?
Thank you for furthering my education. Feel like I'm back in kindergarten. ](*,)  ;)

The recovery console is a feature of the XP install disk.  When you boot the install CD it gives you options including installing windows and repairing a previous installation.  One of the tools in the repair menu is Recovery Console, which is kind of like the terminal in *nix (though not as powerful).  You just type the following command at the prompt:

```
fixmbr
```

---

### Post by greypoet on 2008-01-23
Well, looks like I'm going to be busy for a while. Thank you Latinist, for the links and ideas.
I think I'll go home now. My brain is full.  :-\"  :lol:

---

