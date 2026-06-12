---
title: "OldWorld 6400: &quot;Unable to mount root fs on unknown-block(0,0)&quot;"
date: 2007-04-27
forum: Apple PPC Users
---

### Post by nym.null on 2007-04-27
Hi All,

I'm trying to inject some new life (read: more modern apps) into an OldWorld Performa 6400 by using **X**ubuntu and have run into the problem in the thread title: "Unable to mount root fs on unknown-block(0,0)".

I know that this problem is not unique, but I have not been able to use the forum articles I've found to be able to actually get to boot.  The restrictions of using BootX and not being able to boot a live CD make this more frustrating than I expected. (I've successfully installed Kubuntu and OpenSuSE x86 prior to this but still consider myself quite the newb.)

The gory details are posted below.
Any help you might be able to provide will be much[!] appreciated.

Cheers,
Tom

**_Distro:_** **Xubuntu**, 6.06.1, alternate disk

**_Hardware:_**[LIST][*]Mac Performa 6400/200 (603e chip), 72 MB RAM
[*]10 GB IDE drive
[*]Apple CD-ROM
[*]Mac OS 8.6
[*]BootX 1.2.2
[/LIST]

**_Partitioning:_**
IDE master (hda) - 10.1 GB
[INDENT][FONT="Courier New"]
1    32.3 kB		Apple
2    27.6 kB		Macintosh
3    37.9 kB		Macintosh
4  262.1 kB		Patch Partit
5      2.8 GB	ext3	/
6      2.1 GB	hfs	(MacOS 8.6)
7    10.0 MB	ext2	/boot
8      4.7 GB	ext3	/home
9  483.5 MB		/swap[/FONT][/INDENT]

(The separate /boot folder is only as a result of where I left off after trying different partitioning schemes, trying to resolve the no-boot problem.)

Installation was performed as per "[zcat's howto]("https://help.ubuntu.com/community/Installation/OldWorldMacs")", including the fstab entry and copying of "vmlinux" and "initrd.img" over to "System Folder:Linux Kernels".

**_Xubuntu Boot Messsages_** (disk-related only):
```
.....
ide:  Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
..... output messages about adb devices ...
ide0: no intrs for device /bandit/ohare/ATA, using 13
ide0: Found Apple OHare ATA controller, bus ID 0, irq13
..... output messages about mice, IP/TCP/NET
hda:  IBM-DYYA-351010, ATA DISK drive
hda:  Enabling MultiWord DMA 2
ide0  at 0xc5012000-0xc5012007,0xc5012160 on irq 13
.....
VFS: Cannot open root device "hda5" or unknown-block(0,0)
Please append a correct "root=" boot option
Kernel Panic - Not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
<0>Rebooting in 180 seconds..
```

**_Post-Installation:_**
Mac "System Folder:Linux Kernels" contains:
(timestamps = time of copy from installation)

[INDENT][FONT="Courier New"]vmlinux(4,208,331 bytes)
ramdisk.image.gz (4,866,901 / 5,218,304 bytes *)[/FONT] [/INDENT]
(*with/without install attempt with "modprobe mesh", also as recommended on the "[Installation/OldWorldMacs page ]("https://help.ubuntu.com/community/Installation/OldWorldMacs")"

**_Other correction attempts:_**
[LIST]
[*]Try with/without separate /boot directory
[*]Try ext2/ext3 filesystem for /boot directory (read that BootX doesn't always play well with ext3 <penguinppc.org?>).
[*]Specifying in BootX: root device = /dev/hda(x,y)
[*]Specify ramdisk.image.gz iin BootX, only gives different errors[INDENT][FONT="Courier New"]RAMDISK: incomplete write (-28 !=32768) 8388608
RAMDISK: ran out of compressed data 
RAMDISK: invalid compressed format (err=1)[/FONT][/INDENT]
[*]I see that **miBoot** may be an alternative boot manager. I'm not looking forward to running that down, but will consider it if BootX fails completely. (Installing in Low Memory mode with a 2x CD-ROM drive sucks.)
[*]At the end of the last installation attempt I copied the complete contents of /boot over to the hfs/Mac side of things in case this may be of use.
[*]...
[/LIST]


If you got this far ...thanks for reading!, and please let me know if I can provide any additional information to help you help me get this going.

---

### Post by SycloneMedia on 2007-05-03
I didn't get a chance to read through your whole post, but I occassionally get the same error on boot-up, and it was suggested that one of my ram memory modules might be bad...

...for what it's worth. Don't know if it helps!

---

### Post by anders_gud on 2007-05-03
> **nym.null said:**
> 
[INDENT][FONT="Courier New"]RAMDISK: incomplete write (-28 !=32768) 8388608
RAMDISK: ran out of compressed data 
RAMDISK: invalid compressed format (err=1)[/FONT][/INDENT]

This is strange...
You have to specify the right initrd (fi. in a Feisty install: initrd.img-2.6.20-15-powerpc) and vmlinux in BootX or your kernel will not be able to load the right drivers. (unless you build your own kernel with all needed modules compiled in...)

---

