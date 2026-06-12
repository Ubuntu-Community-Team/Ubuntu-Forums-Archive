---
title: "OldWorld Feisty install: disk detection issues"
date: 2007-05-11
forum: Apple PPC Users
---

### Post by SubGothius on 2007-05-11
**Synopsis:**
On my OldWorld PPC/SCSI Mac using BootX, the Feisty cdrom installer does not recognize my [Feisty PPC Alt. Install CD](http://cdimage.ubuntu.com/ports/releases/feisty/release/), and the netoot installer [partitioner only shows one SCSI disk](http://ubuntuforums.org/showthread.php?t=433486) (out of 3 in my system) available for partitioning.

After successfully [installing 6.10 Edgy on my OldWorld PowerMac clone](http://ubuntuforums.org/showthread.php?t=395441), I subsequently borked that system myself, making a fresh reinstall the easiest obvious option for me.  Having heard of "many PPC fixes in Feisty", I decided to try booting into a [PowerPC installer for 7.04 Feisty](http://ftp.ubuntu.com/ubuntu/dists/feisty/main/installer-powerpc/current/images/powerpc/).  Impressed by the initially-apparent improvement vs. the Edgy installer (e.g., correct display with all boot-time kernel messages, console and installer text fully visible, at my chosen resolution, and no longer jittery/distorted), I decided to proceed and try my hand at a clean install of Feisty, which seemed to start off well, until...

The vmlinux kernel and initrd.gz ramdisk files for the cdrom installer (whether copied from the CD or D/L'd from the FTP site) cannot detect that I have a CD inserted in the CD-ROM drive at all.  Trying the initrd.gz ramdisk file for the netboot installer instead, I get all the way to the partitioner stage, but that only shows one SCSI disk (the overall-largest out of 3 HDDs installed in my system) available for partitioning... and it's not the drive I want for my / and /boot -- I want my / and /boot and a swap on another drive, and only my /home, /tmp and another swap on the one drive appearing in the netboot installer.  At least the Edgy cdrom installer detected all my SCSI drives and made all of them available to partition to my liking (FWIW, the Edgy netboot installer had failed at the network-detection/DHCP stage, but I now suspect a few retries would have worked).

Since I can now see the boot-time HW detection messages (unlike Edgy, where all I got was an all-black signal during kernel boot time, and distorted/jittery console text otherwise), I notice that the cdrom installer boots up with the "mesh" (Mac built-in SCSI) kernel module correctly detecting all my SCSI drives (strange then that it cannot detect any CD when the installer looks for one?), but the netboot installer does not appear to do this (strange then that it eventuall finds any SCSI disk at all!).

Is there any way, like say a kernel argument / boot variable in BootX, to make the netboot installer load the "mesh" module (akin to the "modprobe mesh" command) during boot, and thus detect all SCSI disks present?  I have already tried running "modprobe mesh" from an F-key virtual console during install before the partitioner starts, but that doesn't seem to work.

---

### Post by SubGothius on 2007-05-13
UPDATE:
I tried physically unplugging the one drive it recognized, then I rebooted into the Feisty netboot installer.  That time, the install partitioner did not find *any* disks to partition, so I know it's not just defaulting to find only the overall-largest disk; it only ever found one accessible disk at all -- tho' it did assign /dev/sdc to the disk it found, indicating that it knows sda and sdb devices at least exist on the bus.  Although it offered me a list of drivers/modules to load and then rescan for more devices, selecting "mesh" (Macintosh Enhanced SCSI Hardware) did not help, nor did "sd_mod", nor "scsi_mod" (I think the latter was called?).

The only thing different about the one disk it consistently found was that it's an Ultra SCSI Wide (Seagate ST19171W SUN9.0G), rather than a SCSI-2 "Fast SCSI" device native to my built-in drive bus like the other devices, so it has a small adapter/bridge to plug its Micro D connector into the 50-pin ribbon connectors of my built-in SCSI2 bus.  Also, the "SUN9.0G" identifier suggests it was prolly intended for use in a Sun box, which would of course have been running Solaris or some other *nix variant originally.

After trying combinations of Feisty/Edgy install kernels and installer initrds and finding no cross-version combo that worked, I went ahead with the Feisty netboot install on the one drive available to me, thinking I might be able to access my other SCSI devices and add more partitions on another disk post-install, once I had a complete system to work with.  However...

No dice.  My newly-installed Feisty system still only allows me access to this one SCSI drive, none of the other HDDs, no CD-ROMs, nothing.  It appears to me that something about Feisty broke either the specific "mesh" kernel module for the OldWorld PowerMac Fast SCSI-II bus, or the general Linux SCSI driver(s) themselves, or something about the interaction between the two.  Strangely, tho' my one usable disk showed as /dev/sdc during install, it changed to /dev/sdb in the installed system!  Gparted does not even acknowledge the other disks exist.

FWIW, here's the relevant section of my syslog, showing how it finds and then offlines all my other SCSI devices:```
[  124.072081] SCSI subsystem initialized
[  124.108863] mesh: configured for synchronous 5 MB/s
[  124.334925] mesh: performing initial bus reset...
[  128.358871] scsi0 : MESH
[  128.382765] mesh: target 0 synchronous at 5.0 MB/s
[  128.408258] scsi 0:0:0:0: Direct-Access     MICROP   4421-07   0502SJ 0502 PQ: 0 ANSI: 2
[  128.440829] mesh: target 1 synchronous at 5.0 MB/s
[  128.466960] scsi 0:0:1:0: Direct-Access     SEAGATE  ST19171W SUN9.0G 0A7E PQ: 0 ANSI: 2
[  128.495884] mesh: target 2 synchronous at 5.0 MB/s
[  128.519396] scsi 0:0:2:0: Direct-Access     FUJITSU  M2954S-512       0153 PQ: 0 ANSI: 2
[  128.546252] mesh: target 3 synchronous at 5.0 MB/s
[  128.571826] scsi 0:0:3:0: CD-ROM            MATSHITA CD-ROM CR-506    8S04 PQ: 0 ANSI: 2
[  128.669950] Capability LSM initialized
[  129.125337] mesh: target 6 synchronous at 5.0 MB/s
[  129.151218] scsi 0:0:6:0: CD-ROM            TEAC     CD-R55S          1.0K PQ: 0 ANSI: 2
[  146.099028] usbcore: registered new interface driver usbfs
[  146.121706] usbcore: registered new interface driver hub
[  146.144157] usbcore: registered new device driver usb
[  146.188035] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[  146.188625] PCI: Enabling device 0000:01:03.0 (0014 -> 0016)
[  146.211099] ohci_hcd 0000:01:03.0: OHCI Host Controller
[  146.249614] ieee1394: Initialized config rom entry `ip1394'
[  146.283106] PCI: Enabling device 0000:00:0d.0 (0014 -> 0016)
[  146.374783] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[23]  MMIO=[80900000-809007ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[  146.635507] scsi1 : 53C94
[  146.841895] eth0: MACE at 00:05:9a:40:59:ef, chip revision 9.64
[  147.224947] ohci_hcd 0000:01:03.0: new USB bus registered, assigned bus number 1
[  147.247970] ohci_hcd 0000:01:03.0: irq 25, io mem 0x80800000
[  147.406559] usb usb1: configuration #1 chosen from 1 choice
[  147.432404] hub 1-0:1.0: USB hub found
[  147.454104] hub 1-0:1.0: 2 ports detected
[  147.704760] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0030dd8000201367]
[  147.882761] usb 1-1: new low speed USB device using ohci_hcd and address 2
[  148.122328] usb 1-1: configuration #1 chosen from 1 choice
[  148.450737] usb 1-2: new full speed USB device using ohci_hcd and address 3
[  148.691475] usb 1-2: configuration #1 chosen from 1 choice
[  148.780899] mesh_host_reset
[  150.420712] usbcore: registered new interface driver hiddev
[  150.732041] input: Kensington Kensington USB/PS2 Trackball as /class/input/input3
[  150.758249] input: USB HID v1.00 Mouse [Kensington Kensington USB/PS2 Trackball] on usb-0000:01:03.0-1
[  150.828672] usbcore: registered new interface driver libusual
[  150.977225] usbcore: registered new interface driver usbhid
[  150.999486] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[  151.083307] Initializing USB Mass Storage driver...
[  151.106370] scsi2 : SCSI emulation for USB Mass Storage devices
[  151.129428] usb-storage: device found at 3
[  151.129464] usb-storage: waiting for device to settle before scanning
[  151.129593] usbcore: registered new interface driver usb-storage
[  151.151903] USB Mass Storage support registered.
[  156.128576] usb-storage: device scan complete
[  156.135485] scsi 2:0:0:0: Direct-Access     Multi    Flash Reader     1.00 PQ: 0 ANSI: 0
[  158.803395] mesh: target 0 synchronous at 5.0 MB/s
[  158.825998] sd 0:0:0:0: scsi: Device offlined - not ready after error recovery
[  158.848870] sd 0:0:0:0: rejecting I/O to offline device
[  158.871005] sd 0:0:0:0: rejecting I/O to offline device
[  158.892952] sd 0:0:0:0: rejecting I/O to offline device
[  158.914883] sd 0:0:0:0: rejecting I/O to offline device
[  158.936783] sda : READ CAPACITY failed.
[  158.936795] sda : status=0, message=00, host=1, driver=00 
[  158.979911] sda : sense not available. 
[  159.001318] sd 0:0:0:0: rejecting I/O to offline device
[  159.023182] sda: Write Protect is off
[  159.044460] sda: Mode Sense: 00 00 00 00
[  159.044545] sd 0:0:0:0: rejecting I/O to offline device
[  159.066400] sda: asking for cache data failed
[  159.087923] sda: assuming drive cache: write through
[  159.113797] sd 0:0:0:0: Attached scsi disk sda
[  159.144061] mesh: target 1 synchronous at 5.0 MB/s
[  159.168178] SCSI device sdb: 17689267 512-byte hdwr sectors (9057 MB)
[  159.193640] sdb: Write Protect is off
[  159.215256] sdb: Mode Sense: cf 00 10 08
[  159.218795] SCSI device sdb: write cache: enabled, read cache: enabled, supports DPO and FUA
[  159.244755] SCSI device sdb: 17689267 512-byte hdwr sectors (9057 MB)
[  159.270292] sdb: Write Protect is off
[  159.291913] sdb: Mode Sense: cf 00 10 08
[  159.295430] SCSI device sdb: write cache: enabled, read cache: enabled, supports DPO and FUA
[  159.318633]  sdb: [mac] sdb1 sdb2 sdb3 sdb4 sdb5 sdb6 sdb7
[  159.383189] sd 0:0:1:0: Attached scsi disk sdb
[  159.409225] mesh: target 2 synchronous at 5.0 MB/s
[  159.433463] mesh_host_reset
[  169.459222] mesh: target 2 synchronous at 5.0 MB/s
[  169.482258] sd 0:0:2:0: scsi: Device offlined - not ready after error recovery
[  169.505172] sd 0:0:2:0: rejecting I/O to offline device
[  169.527190] sd 0:0:2:0: rejecting I/O to offline device
[  169.549147] sd 0:0:2:0: rejecting I/O to offline device
[  169.571078] sd 0:0:2:0: rejecting I/O to offline device
[  169.593410] sdc : READ CAPACITY failed.
[  169.593424] sdc : status=0, message=00, host=1, driver=00 
[  169.636697] sdc : sense not available. 
[  169.658129] sd 0:0:2:0: rejecting I/O to offline device
[  169.680009] sdc: Write Protect is off
[  169.701266] sdc: Mode Sense: 00 00 00 00
[  169.701353] sd 0:0:2:0: rejecting I/O to offline device
[  169.723313] sdc: asking for cache data failed
[  169.744817] sdc: assuming drive cache: write through
[  169.770645] sd 0:0:2:0: Attached scsi disk sdc
[  169.797693] mesh: target 3 synchronous at 5.0 MB/s
[  169.822133] mesh_host_reset
[  169.854134] sd 2:0:0:0: Attached scsi removable disk sdd
[  170.177078] sd 0:0:0:0: Attached scsi generic sg0 type 0
[  170.202733] sd 0:0:1:0: Attached scsi generic sg1 type 0
[  170.228126] sd 0:0:2:0: Attached scsi generic sg2 type 0
[  170.253591] sr 0:0:3:0: Attached scsi generic sg3 type 5
[  170.279048] scsi 0:0:6:0: Attached scsi generic sg4 type 5
[  170.304611] sd 2:0:0:0: Attached scsi generic sg5 type 0
[  179.847513] mesh: target 3 synchronous at 5.0 MB/s
[  179.870231] sr 0:0:3:0: scsi: Device offlined - not ready after error recovery
[  179.893109] sr 0:0:3:0: rejecting I/O to offline device
[  179.915157] sr 0:0:3:0: rejecting I/O to offline device
[  179.939283] sr0: scsi3-mmc drive: 0x/0x caddy
[  179.961029] Uniform CD-ROM driver Revision: 3.20
[  179.986981] sr 0:0:3:0: Attached scsi CD-ROM sr0
[  179.989786] mesh: target 6 synchronous at 5.0 MB/s
[  180.016383] mesh_host_reset
[  190.040456] mesh: target 6 synchronous at 5.0 MB/s
[  190.064217] sr 0:0:6:0: scsi: Device offlined - not ready after error recovery
[  190.087037] sr 0:0:6:0: rejecting I/O to offline device
[  190.114103] sr 0:0:6:0: rejecting I/O to offline device
[  190.136585] mesh: target 1 synchronous at 5.0 MB/s
[  190.158456] sr1: scsi3-mmc drive: 0x/0x caddy
[  190.422948] sr 0:0:6:0: Attached scsi CD-ROM sr1
[  193.180780] EXT3-fs: INFO: recovery required on readonly filesystem.
[  193.203324] EXT3-fs: write access will be enabled during recovery.
[  208.251608] kjournald starting.  Commit interval 5 seconds
[  208.274097] EXT3-fs: recovery complete.
[  208.305522] EXT3-fs: mounted filesystem with ordered data mode.
```

---

### Post by daaawooo on 2007-05-18
hello,

I have similar problems ... no CD-access from xubuntu-alternate feisty daily 20070415.
if I want to use internel CD-drive on MESH and an external HDD on 2nd built-in scsi-controller NCR53c94, from text during boot and/or syslog and/or cat /proc/modules I can see correct loading of modules MESH and mac53c94 and correct detection of all HDD/CD-drives on their controllers, but install-cd is not inserted means installer.
same attemps like you with kernel from ftp from motther ubuntu - still no success.

old 6.06.1 ubuntu-alternate found only my internal HDD-drives on MESH and also the CD, good but I don´t want to install this old stuff.

so I took an old asus as-300 - an "aic7xxx" based scsi-controller out of the basement.
plugged the target HDD and also an old plextor px-32cs on the controller.
and wow I can boot with kernel/initrd from xubuntu cd and install-cd and hdd (as sdc) is found correctly and usable, so I went on installing 2-3 hrs on the slow old beast.
aic7xxx module means 10mb/s-mode even controller can do 20 mb/s in a pc.
for mesh and ncr 5mb/s, even I tested my hdd under mac-os with 6-7 mb/s.

let installer use full hdd, no mac-partition on it. so he created / ext3, /root ext2 and swap (if I correctly remember).
wrote down the root-device and root info at the end of the install.
but now I can´t boot into my install, because I didn´t copy the updated initrd like you at the end of the install to a mac-part. even recovering like you in your 6.10.1 install won´t work because I didn´t get my mac-part. mounted, because sda and sdb are not mountable (not valid block device), both drives are found on correct controller have same info like in your log:

> sda : READ CAPACITY failed.

so later at home I try to hook the hdd to a pc booting with sysresc-cd and copy the initrd to another computer.

---

### Post by SubGothius on 2007-05-28
Still no joy in this issue.  Other things I've tried since my last post, all to no avail:[list][*]Unplugging all USB devices (on a PCI USB card);
[*]Physically removing a FireWire PCI card;
[*]Physically removing the USB PCI card;
[*]Physically removing both PCI cards;
[*]Rearranging the PCI slot order/position of USB and/or FireWire cards.[/list]Why, oh why, can't Feisty I/O with *any* of my native SCSI-2 devices?
:confused: ](*,)

---

### Post by pxwpxw on 2007-05-29
Just a stab in the dark, but maybe relevant info (or missing info) in /proc/device-tree/  and /proc/scsi/

have a look in  /proc/device-tree/

and 

cat /proc/scsi/scsi

should list all scsi devices.

keep you enterrtained anyway.

---

### Post by SubGothius on 2007-05-29
And the results are...```
$ cat /proc/scsi/scsi
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: MICROP   Model: 4421-07   0502SJ Rev: 0502
  Type:   Direct-Access                    ANSI SCSI revision: 02
Host: scsi0 Channel: 00 Id: 01 Lun: 00
  Vendor: SEAGATE  Model: ST19171W SUN9.0G Rev: 0A7E
  Type:   Direct-Access                    ANSI SCSI revision: 02
Host: scsi0 Channel: 00 Id: 02 Lun: 00
  Vendor: FUJITSU  Model: M2954S-512       Rev: 0153
  Type:   Direct-Access                    ANSI SCSI revision: 02
Host: scsi0 Channel: 00 Id: 03 Lun: 00
  Vendor: MATSHITA Model: CD-ROM CR-506    Rev: 8S04
  Type:   CD-ROM                           ANSI SCSI revision: 02
Host: scsi0 Channel: 00 Id: 06 Lun: 00
  Vendor: TEAC     Model: CD-R55S          Rev: 1.0K
  Type:   CD-ROM                           ANSI SCSI revision: 02
Host: scsi2 Channel: 00 Id: 00 Lun: 00
  Vendor: Multi    Model: Flash Reader     Rev: 1.00
  Type:   Direct-Access                    ANSI SCSI revision: 02
```
So all SCSI devices do show up in /proc/scsi/scsi (flash reader is a USB device, doesn't matter if I unplug it or remove the USB PCI card entirely) -- same info here as what I see early in the boot process, before almost everything gets offlined later on.  This may be related to why the one accessible drive is /dev/sdb[1-7] rather than /dev/sda... it's detecting some device as /dev/sda at SCSI ID:0 (also /dev/sdc at ID:2, etc.), but some error is leading to the devices getting offlined later during boot, like this:```
mesh: target 0 synchronous at 5.0 MB/s
sd 0:0:0:0: scsi: Device offlined - not ready after error recovery
sd 0:0:0:0: rejecting I/O to offline device
```
Also, what am I looking for here:
```
$ ls -la /proc/device-tree
total 0
dr-xr-xr-x 13 root root  0 2007-05-29 03:25 .
dr-xr-xr-x 95 root root  0 2007-05-28 22:00 ..
-r--r--r--  1 root root  4 2007-05-29 03:25 AAPL,cpu-id
dr-xr-xr-x  2 root root  0 2007-05-29 03:25 AAPL,ROM
-r--r--r--  1 root root  4 2007-05-29 03:25 #address-cells
dr-xr-xr-x  2 root root  0 2007-05-29 03:25 aliases
dr-xr-xr-x  7 root root  0 2007-05-29 03:25 bandit
dr-xr-xr-x  2 root root  0 2007-05-29 03:25 chosen
-r--r--r--  1 root root  4 2007-05-29 03:25 clock-frequency
-r--r--r--  1 root root 18 2007-05-29 03:25 compatible
dr-xr-xr-x  2 root root  0 2007-05-29 03:25 hammerhead
dr-xr-xr-x  2 root root  0 2007-05-29 03:25 memory
-r--r--r--  1 root root 16 2007-05-29 03:25 model
-r--r--r--  1 root root  1 2007-05-29 03:25 name
dr-xr-xr-x  2 root root  0 2007-05-29 03:25 offscreen-display
dr-xr-xr-x  2 root root  0 2007-05-29 03:25 openprom
dr-xr-xr-x  2 root root  0 2007-05-29 03:25 options
dr-xr-xr-x 12 root root  0 2007-05-29 03:25 packages
dr-xr-xr-x  3 root root  0 2007-05-29 03:25 PowerPC,604
-r--r--r--  1 root root  4 2007-05-29 03:25 #size-cells
```
:confused:

---

### Post by pxwpxw on 2007-05-29
Read the  aliases, it lists the device tree patths for the drives, then you can see what else to look at in the tree, which is just the open firmware side.
Might give a clue what to search for in some init scripts which try to interpret /proc fs.
Looks like the problem is with the linux system not using what its got, but you already know that.

Edit:

On re-reading above, perhaps your earlier comment about driver modules might still be the right direction if you have added pci cards, I recall in earlier versions a great list of driver modules to choose from - adaptec and all sorts. But I dont know if you have added pci or added devices to the scsi bus or both. 

```

lspci -v
lsmod

```

Perhaps rerun the edgy installer startup to check what if any difference in modules (assuming from your earlier post that edgy gave access to all drives ?? ).

But I am out of my depth here, I dont have any added drives on my old 7300 here to eperiment with, but interested in your conclusions.

---

### Post by SubGothius on 2007-05-30
The presence, absence, or order of PCI cards does not seem to make any difference.  I have tried unplugging all peripherals and have removed, readded, and switched around, all in various combinations of slots, the two PCI cards I do have (a USB card and a FireWire card), and I did flash the PRAM and reset the mobo CUDA switch in between each iteration, all without any improvement to the drive-access issue.  Thx for the suggestion anyway.

However, as for your other line of inquiry:```
tye@vesta:~$ ls -la /proc/device-tree/aliases
total 0
dr-xr-xr-x  2 root root  0 2007-05-30 02:21 .
dr-xr-xr-x 13 root root  0 2007-05-30 02:21 ..
-r--r--r--  1 root root 16 2007-05-30 02:21 enet
-r--r--r--  1 root root 17 2007-05-30 02:21 fd
-r--r--r--  1 root root 33 2007-05-30 02:21 kbd
-r--r--r--  1 root root  8 2007-05-30 02:21 name
-r--r--r--  1 root root 17 2007-05-30 02:21 pci1
-r--r--r--  1 root root 17 2007-05-30 02:21 pci2
-r--r--r--  1 root root 17 2007-05-30 02:21 scsi
-r--r--r--  1 root root 16 2007-05-30 02:21 scsi-int
-r--r--r--  1 root root 21 2007-05-30 02:21 ttya
-r--r--r--  1 root root 21 2007-05-30 02:21 ttyb
-r--r--r--  1 root root 16 2007-05-30 02:21 vci0
tye@vesta:~$ ls -la /proc/device-tree/aliases/scsi*
-r--r--r-- 1 root root 17 2007-05-30 02:21 /proc/device-tree/aliases/scsi
-r--r--r-- 1 root root 16 2007-05-30 02:21 /proc/device-tree/aliases/scsi-int
tye@vesta:~$ cat /proc/device-tree/aliases/scsi*
/bandit/gc/53c94/bandit/gc/meshtye@vesta:~$ cat /proc/device-tree/aliases/scsi
/bandit/gc/53c94tye@vesta:~$ cat /proc/device-tree/aliases/scsi-int
/bandit/gc/meshtye@vesta:~$
```Odd thing strikes me about the lines of output from those alias-files -- the apparent lack of a final Return character; perhaps I might try editing those files to end on a blank line?

Also, am I to presume that the initial / from those two aliases is intended to be relative to /proc/device-tree -- i.e., there is no /bandit in my filesystem /, but there is a /proc/device-tree/bandit/gc/ -- or could that be a bug also?```
tye@vesta:~$ ls -la /bandit
ls: /bandit: No such file or directory
tye@vesta:~$ ls -la /proc/device-tree/bandit/gc/53c94
total 0
dr-xr-xr-x  4 root root  0 2007-05-30 02:37 .
dr-xr-xr-x 10 root root  0 2007-05-30 02:37 ..
-r--r--r--  1 root root  8 2007-05-30 02:37 AAPL,address
-r--r--r--  1 root root  5 2007-05-30 02:37 AAPL,connector
-r--r--r--  1 root root  8 2007-05-30 02:37 AAPL,interrupts
-r--r--r--  1 root root  4 2007-05-30 02:37 clock-frequency
-r--r--r--  1 root root  5 2007-05-30 02:37 device_type
-r--r--r--  1 root root 24 2007-05-30 02:37 driver-ist
-r--r--r--  1 root root  6 2007-05-30 02:37 name
-r--r--r--  1 root root 16 2007-05-30 02:37 reg
dr-xr-xr-x  2 root root  0 2007-05-30 02:37 sd
dr-xr-xr-x  2 root root  0 2007-05-30 02:37 st
tye@vesta:~$ ls -la /proc/device-tree/bandit/gc/mesh
total 0
dr-xr-xr-x  4 root root  0 2007-05-30 02:38 .
dr-xr-xr-x 10 root root  0 2007-05-30 02:38 ..
-r--r--r--  1 root root  8 2007-05-30 02:38 AAPL,address
-r--r--r--  1 root root  9 2007-05-30 02:38 AAPL,connector
-r--r--r--  1 root root  8 2007-05-30 02:38 AAPL,interrupts
-r--r--r--  1 root root  4 2007-05-30 02:38 clock-frequency
-r--r--r--  1 root root  5 2007-05-30 02:38 device_type
-r--r--r--  1 root root 24 2007-05-30 02:38 driver-ist
-r--r--r--  1 root root 14 2007-05-30 02:38 model
-r--r--r--  1 root root  5 2007-05-30 02:38 name
-r--r--r--  1 root root 16 2007-05-30 02:38 reg
dr-xr-xr-x  2 root root  0 2007-05-30 02:38 sd
dr-xr-xr-x  2 root root  0 2007-05-30 02:38 st
```

---

### Post by pxwpxw on 2007-06-01
On /proc/device-tree/ you have a mirror of your mac open firmware device tree as seen from its top level, at restart.

In each node, the files = properties, and the text  = value of the property.

Only suggested to see whats in open firmware, not suggesting any bugs there. 

If you have all your scsi devices on the scsi-int bus (mesh) then maybe the problem is dealing with the scsi ids, maybe change id jumper on the scsi hardware settings (if there is one). I dont know, I just fired up my 7300 with 2 internal scsi hard disk + cd + external scsi zip drive on the external socket + usb flash on usc pci card. All go, using ubuntu 510. I might give feisty a go to see what happens.

Depends how you want to pursue the problem.

I did find that
```

lshw -short
lshw -enable device-tree

```

give very good mapping of /dev/xxx names, scsi info etc.

Also find 2 very handy console utilities for this sort of stuff 

midnight commander (file manager) and gpm (console mouse). Maybe you have them, if not
```

apt-get install mc gpm

```

And a good reference for Oldmacs is at:

> 
Apple Developer Connection

ADC Home > Reference Library > Technical Notes > Legacy Documents > 

Technical Notes
Legacy Documents ListApple Developer Connection


[http://developer.apple.com/technicalnotes/LegacyTechnologies/index-date.html#doclist](http://developer.apple.com/technicalnotes/LegacyTechnologies/index-date.html#doclist)

search in technotes for your model number, they have .pdf for 9600, 7200, 7300 complete with block diagram showing bandit, grand central, mesh and all that.

---

### Post by SubGothius on 2007-06-01
Since this is a Mac clone, not an Apple box, those technotes may be of limited value, and I'd have no idea what to look for there nor how to make sense of any of it.  Perhaps something for a guru much more knowledgeable than I to investigate...

Feisty is the only one with this problem; all disks worked perfectly fine in Edgy and also in Debian Sarge, Etch and even Lenny, so what was I looking for in my open firmware /proc/device-tree nodes...?  All I know is, something changed in Feisty (guessing prolly in the 2.6.20-series kernel?) to break what was working flawlessly before.

Running 'lshw -enable device-tree' just confirms what I already know -- that Feisty can't access most of my disk devices (here marked as 'UNCLAIMED') -- unless this reveals some further clues of value:```
vesta                     
    description: Computer
    product: Power Macintosh
  *-core
       description: Motherboard
       physical id: 0
       clock: 50MHz
       capabilities: aapl_____ macrisc
     *-firmware
          product: Open Firmware, 1.0.5
          physical id: 0
          logical name: /proc/device-tree
     *-memory
          description: System memory
          physical id: 1
          size: 128MB
     *-cpu
          product: 604e
          physical id: 2
          bus info: cpu@0
          version: 2.2 (pvr 0009 0202)
     *-pci
          description: Host bridge
          product: Bandit PowerPC host bridge
          vendor: Apple Computer Inc.
          physical id: 100
          bus info: pci@00:0b.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: latency=32
        *-usb
             description: USB Controller
             product: 82C861
             vendor: OPTi Inc.
             physical id: d
             bus info: pci@00:0d.0
             logical name: /dev/fb0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master fb accelerated
             configuration: depth=32 driver=ohci_hcd frequency=93.05Hz latency=32 mode=1024x768 visual=directcolor xres=1024 yres=768
             resources: iomemory:80900000-80900fff irq:23
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.20-15-powerpc-smp ohci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb:0
                   description: Mouse
                   product: Kensington USB/PS2 Trackball
                   vendor: Kensington
                   physical id: 1
                   bus info: usb@1:1
                   version: 1.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
              *-usb:1
                   description: Mass storage device
                   product: Mass Storage Device
                   vendor: Generic
                   physical id: 2
                   bus info: usb@1:2
                   logical name: scsi2
                   version: 1.00
                   serial: 058F0O1111B
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=100mA speed=12.0MB/s
                 *-disk
                      description: SCSI Disk
                      product: Flash Reader
                      vendor: Multi
                      physical id: 0.0.0
                      bus info: scsi@2:0.0.0
                      logical name: /dev/sdd
                      version: 1.00
                      capabilities: removable
                    *-disc
                         physical id: 0
                         logical name: /dev/sdd
        *-display
             description: Display controller
             product: IMS9128 [Twin turbo 128]
             vendor: Integrated Micro Solutions Inc.
             physical id: e
             bus info: pci@00:0e.0
             version: 01
             size: 16MB
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=imsttfb latency=32 maxlatency=8 mingnt=8
             resources: iomemory:82000000-82ffffff irq:24
        *-pci
             description: PCI bridge
             product: DECchip 21052
             vendor: Digital Equipment Corporation
             physical id: f
             bus info: pci@00:0f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-firewire
                description: FireWire (IEEE 1394)
                product: FW323
                vendor: Agere Systems
                physical id: 3
                bus info: pci@01:03.0
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=24 mingnt=12
                resources: iomemory:80800000-80800fff irq:25
        *-generic
             product: Grand Central I/O
             vendor: Apple Computer Inc.
             physical id: 10
             bus info: pci@00:10.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=macio latency=32
             resources: iomemory:f3000000-f301ffff irq:22
     *-scsi
          physical id: 3
          logical name: scsi0
          capabilities: scsi-host
          configuration: driver=mesh
        *-disk:0 UNCLAIMED
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
        *-disk:1
             description: SCSI Disk
             product: ST19171W SUN9.0G
             vendor: SEAGATE
             physical id: 0.1.0
             bus info: scsi@0:0.1.0
             logical name: /dev/sdb
             version: 0A7E
             serial: LAN56198
             size: 8637MB
             capabilities: 7200rpm partitioned partitioned:mac
             configuration: ansiversion=2
           *-volume:0
                description: Apple partition map
                physical id: 1
                bus info: scsi@0:0.1.0,1
                logical name: /dev/sdb1
                capacity: 50KB
           *-volume:1
                description: FWB Driver Components
                physical id: 2
                bus info: scsi@0:0.1.0,2
                logical name: /dev/sdb2
                capacity: 512KB
           *-volume:2
                description: Apple Driver43
                physical id: 3
                bus info: scsi@0:0.1.0,3
                logical name: /dev/sdb3
                capacity: 38KB
           *-volume:3
                description: Apple HFS
                physical id: 4
                bus info: scsi@0:0.1.0,4
                logical name: /dev/sdb4
                capacity: 4GB
           *-volume:4
                description: Apple UNIX SVR2
                physical id: 5
                bus info: scsi@0:0.1.0,5
                logical name: /dev/sdb5
                capacity: 4021MB
           *-volume:5
                description: Apple UNIX SVR2
                physical id: 6
                bus info: scsi@0:0.1.0,6
                logical name: /dev/sdb6
                capacity: 488MB
           *-volume:6
                description: Apple UNIX SVR2
                physical id: 7
                bus info: scsi@0:0.1.0,7
                logical name: /dev/sdb7
                capacity: 30MB
        *-disk:2 UNCLAIMED
             description: SCSI Disk
             physical id: 0.2.0
             bus info: scsi@0:0.2.0
        *-cdrom:0 UNCLAIMED
             description: SCSI CD-ROM
             physical id: 0.3.0
             bus info: scsi@0:0.3.0
        *-cdrom:1 UNCLAIMED
             description: SCSI CD-ROM
             physical id: 0.6.0
             bus info: scsi@0:0.6.0
  *-scsi
       physical id: 1
       bus info: scsi@1
       logical name: scsi1
       capabilities: scsi-host
       configuration: driver=53c94
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: eth0
       serial: 00:05:9a:40:59:ef
       capabilities: ethernet physical
       configuration: broadcast=yes ip=192.168.1.66 multicast=yes
```

---

### Post by SubGothius on 2007-06-01
Since this now seems beyond the scope of a minor glitch with a simple DIY fix, I have formally reported this issue as [Bug #118319 in linux-source-2.6.20](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/118319)

pxwpxw (or anyone else with an OldWorld PPC Mac reading this), if you could [D/L the Feisty installer vmlinux and initrd.gz files](http://ftp.ubuntu.com/ubuntu/dists/feisty/main/installer-powerpc/current/images/powerpc/) (netboot versions should be fine if you can plug your 7300 into a DHCP'd broadband link) and then boot into that installer, your results there could confirm or refute that my problem generally affects any/every Mac inboard Fast SCSI-2 bus and its 'mesh' driver module in Linux.  You don't need to complete an install (if the partitioner gives you any disks to install on!), just watch the kernel boot messages, or get to the partitioning stage, and see if the Feisty installer's 2.6.20-series kernel can detect any of your onboard SCSI devices at all.

---

### Post by pxwpxw on 2007-06-02
OK will do soon.

---

### Post by pxwpxw on 2007-06-03
Same here, I will append comparison data 704/610 t to the Launch Pad bug report.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/118319](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/118319)

ubuntu 704 installer scsi bug.

 Alternate install CD ubuntu704

Oldworld powermac 7300/180, internal scsi bus = 2 x hard drive + 1 cd.
external scsi bus = 1 zip drive
external usb 1 usb flash stick.

```

/proc/cpuinfo

processor	: 0
cpu		: 604e
clock		: 180.000000MHz
revision	: 2.4 (pvr 0009 0204)
bogomips	: 22.46
timebase	: 11249783
platform	: PowerMac
machine		: Power Macintosh
motherboard	: AAPL,7500 MacRISC
detected as	: 16 (PowerMac 7500)
pmac flags	: 00000000
L2 cache	: 256K unified
pmac-generation	: OldWorld

====================================
==u704 installer vmlinux and initrd, fails to mount cdrom
=====================================

1. installer Alternate CD ubuntu704::::::

uname -a 
Linux (none) 2.6.20-15-powerpc #3 Sun Apr 15 06:45:49 UTC 2007 ppc unknown



dmesg | grep scsi


[  152.900916] scsi0 : 53C94
[  154.174178] scsi 0:0:5:0: Direct-Access     IOMEGA   ZIP 100          J.02 PQ: 0 ANSI: 2
[  154.540944] scsi2 : SCSI emulation for USB Mass Storage devices
[  158.335149] scsi1 : MESH
[  158.368828] scsi 1:0:0:0: Direct-Access     IBM      DDRS-34560       S97B PQ: 0 ANSI: 2
[  158.398443] scsi 1:0:1:0: Direct-Access     QUANTUM  FIREBALL_TM2100S 3016 PQ: 0 ANSI: 2
[  158.685588] scsi 1:0:3:0: CD-ROM            MATSHITA CD-ROM CR-8012   1.0f PQ: 0 ANSI: 2
[  159.556707] scsi 2:0:0:0: Direct-Access     Flash    Drive AL_USB20   1.00 PQ: 0 ANSI: 2
[  164.723535] sd 0:0:5:0: scsi: Device offlined - not ready after error recovery
[  164.841393] sd 0:0:5:0: Attached scsi removable disk sda
[  174.881355] sd 1:0:0:0: scsi: Device offlined - not ready after error recovery
[  174.989819] sd 1:0:0:0: Attached scsi disk sdb
[  175.204392] sd 1:0:1:0: Attached scsi disk sdc
[  175.369089] sd 2:0:0:0: Attached scsi removable disk sdd
[  175.453273] sd 0:0:5:0: Attached scsi generic sg0 type 0
[  175.464744] sd 1:0:0:0: Attached scsi generic sg1 type 0
[  175.475798] sd 1:0:1:0: Attached scsi generic sg2 type 0
[  175.486542] sr 1:0:3:0: Attached scsi generic sg3 type 5
[  175.497531] sd 2:0:0:0: Attached scsi generic sg4 type 0
[  185.248676] sr 1:0:3:0: scsi: Device offlined - not ready after error recovery
[  185.284636] sr0: scsi3-mmc drive: 0x/0x caddy
[  185.304588] sr 1:0:3:0: Attached scsi CD-ROM sr0

/proc/scs/scsi

Attached devices:
Host: scsi0 Channel: 00 Id: 05 Lun: 00
  Vendor: IOMEGA   Model: ZIP 100          Rev: J.02
  Type:   Direct-Access                    ANSI SCSI revision: 02
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: IBM      Model: DDRS-34560       Rev: S97B
  Type:   Direct-Access                    ANSI SCSI revision: 02
Host: scsi1 Channel: 00 Id: 01 Lun: 00
  Vendor: QUANTUM  Model: FIREBALL_TM2100S Rev: 3016
  Type:   Direct-Access                    ANSI SCSI revision: 02
Host: scsi1 Channel: 00 Id: 03 Lun: 00
  Vendor: MATSHITA Model: CD-ROM CR-8012   Rev: 1.0f
  Type:   CD-ROM                           ANSI SCSI revision: 02
Host: scsi2 Channel: 00 Id: 00 Lun: 00
  Vendor: Flash    Model: Drive AL_USB20   Rev: 1.00
  Type:   Direct-Access                    ANSI SCSI revision: 02


```

---

### Post by SubGothius on 2007-06-07
Peter (or anyone else following along), are you able to mark this bug report as "confirmed"?  How about its importance status as "undecided"?  I presume I cannot affect those flags because I created the initial bug report, but you may be able to do so as a respondent and independent confirmer.  This may help get the bug some notice (or at least lift it out above the unconfirmed/undecided doldrums ;) ).  Thx!

---

### Post by pxwpxw on 2007-06-08
Just checked the bug report, I found no way to change the status/action, I assume that is an adminisrtrative function, awaitng review. I have said in my report that i confirm the bug, that seems to be all I may do.

I wonder what the policy is on bug reports for Applemacs in general, given that  support is now left to the forum Community  Support.  However this is a software issue which restricts application of ubuntu distributions. Debian seems to have a more sympathetic approach, including some acknowledgement of Old Worldd macs.

---

### Post by SubGothius on 2007-06-08
Thx for checking into it anyway.  AFAIK, "Community Support" does not mean this Forum alone; it only means that Canonical/Shuttleworth is no longer devoting any funding nor paid staffing towards PPC-specific issues, projects, ports, bugs, etc.; thus, it's left up to "the Ubuntu community" -- i.e., enthusiast volunteers with a personal/academic interest in the PowerPC platform in this case -- to tackle PPC-specific bugs, etc. on our own time and dime.

---

### Post by pxwpxw on 2007-06-19
I will try my hand at compiling a kernel with built in scsi support = not requiring to load modules (if thats posible ). Something I saw re scsi. Also maybe a timing factor in initramdisk, there is a setting for delay. 
Just have to find how to do it - I have a 32bit ibook g4 ready for the job.

---

### Post by SubGothius on 2007-06-19
You mean recompile a custom kernel on the G4 (for faster compiling), to run on the oldworld 7300?  Sounds like a plan...

However, before going to all that trouble, I'd say we could first try simply updating the initrd with a different delay value, as you say... BTW, where is that delay value specified?  A file in /etc/initramfs-tools/ perhaps?  I might try a different initrd delay (or several) myself, if I knew where to look for or specify it...

Also, do we know where the kernel gets a list of modules to load in what order during boot?  I know the initrd loads just enough modules to mount a root fs and get the kernel booting, but if I'm not mistaken, the kernel finds and loads all the rest of its own boot modules from there, yes?  Perhaps we might have some success simply reordering the load order SCSI-relevant modules (e.g., putting all generic SCSI mods before the 'mesh' mod)?

Thx again for keeping up with this! 8)

---

### Post by pxwpxw on 2007-06-20
The timing idea came from this which is i386  and USB, but probably the same mkinitramfs options, seems relevant: 

half way down in the Linux Kernel section WAIT=

> 
### This makes the bootup wait until any USB drives are ready
WAIT=15


( refers to /etc/intramfs-tools/initramfs.conf but I cant find a list of available items )

 help.ubuntu.com/community/BootFromUSB

[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

Maybe something better in /usr/share/doc/  or man for initramfs tools, have not found a comprehensive howto so far. Probably something in debian, or the Linux Documentation Project.

edit: spent some hours looking for refs about initramfs options. Found nothing useful.

---

### Post by SubGothius on 2007-07-16
FWIW, this *appears* to be fixed in Gutsy -- at least, I was able to [netboot-install the latest Gutsy beta](http://ftp.ubuntu.com/ubuntu/dists/gutsy/main/installer-powerpc/current/images/powerpc/netboot/) on my OldWorld PowerMac clone, and it detected all SCSI devices and installed just fine.

I had a bit of a problem getting X to launch (something about "no valid modes found" -- same problem I had with a recent Debian Lenny testing install), but researching that error I saw some mention of the new Xorg having more autodetect/autoconfig and no longer relying on xorg.conf (at all?), so deleting the xorg.conf file (actually renamed it, just in case ;)) allowed X to start up for me in the latest Gutsy.  Not clear yet if I have full graphics accelleration or even what resolution or depth I have (at least 800x600@16bit, maybe even 1024x768@24?), as there are no selections in the Monitor setting panel and no obvious way to echo what the current settings are, but at least Gutsy installed and X is nominally working! \\:D/

From what I've seen this far, assuming stuff that's presently working doesn't get broken by the final release [-o<, Gutsy promises to be the best Linux yet for an OldWorld Mac. 8)

---

### Post by pxwpxw on 2007-07-18
Thats very interesting, maybe the bug report had some impact. Maybe the new xorg is getting the settings from firmware and using whatever you had it set to in macos - thts what it used to do in some earlier versions - if so, just set what you want in macos first then boot ubuntu.
Keep up the good work.:o

---

### Post by Tommy on 2007-07-18
> **SubGothius said:**
> From what I've seen this far, assuming stuff that's presently working doesn't get broken by the final release [-o<, Gutsy promises to be the best Linux yet for an OldWorld Mac. 8)

That is very good news!

I follow the Debian PowerPC mailing list. I believe some bugs slipped into Debian unstable due to some leadership changes in PowerPC development, and they seriously affected the Ubuntu versions after Dapper. Now it sounds like critical bug fixes have filtered through to Gutsy -- it's the first release with Debian 4.0 under it. 

I look forward to throwing out all my Edgy and Feisty PPC "coasters" (burned CDs) and trying a Gutsy Net Install!

---

### Post by Tommy on 2007-07-18
> w/ ixMicro/IMS TwinTurbo 128+ (imstt) PCI vidcard

BY THE WAY... I have been reading your posts with interest because I gave up on my IMS TwinTurbo card YEARS ago -- that one has always been a real pain for me. It's the one that came with my PowerMac 9600, but I bought something else on eBay ... can't remember now, but it was a card more common in a Blue & White G3, and it has always been easier to configure.

I mention all this because it means even that nasty old Twin Turbo card is gettin' some lovin' now from x.org, so maybe I'll try reinstalling mine. (I care for two reasons... one, all the "hints" you'll see on the 'net assume you have that card in a 9600, and two, it's an "old fashioned" Mac card that has the Mac interface that connects directly to the Apple Monitor so it knows the resolution etc. automatically. I use PC to Mac adapter on the newer one so the Mac can't tell what's connected.)

---

### Post by SubGothius on 2007-07-24
Looks like I may have spoken too soon? Maybe it's just beta teething problems... Running a 'sudo aptitude update && aptitude upgrade' on my Gutsy install, now X won't start, something about the vesa driver not found. This at least confirms my suspicion that Xorg without an xorg.conf was not using the proper imstt driver at all, but rather falling back to a generic video driver (vesa) instead. Guess I should really be taking these issues up on the Debian or Xorg side of things, since this is surely all upstream stuff...

FYI, FWIW... :roll:

---

