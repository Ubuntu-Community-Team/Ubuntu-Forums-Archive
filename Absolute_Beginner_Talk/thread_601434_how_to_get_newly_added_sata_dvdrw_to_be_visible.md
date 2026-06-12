---
title: "how to get newly added sata dvdrw to be visible"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by bear2 on 2007-11-03
Hello community.
I am interested in getting a newly added sata internal dvdrw to recognize in ubuntu 6.06
I am running gnome as my desktop environment.
is there a utility that would assist with scanning for this new hardware and adding the 
correct entry to fstab ?
if not, what are some of the manual steps i need to do?
Thanks much in advance for any help !

I have an amd 64x2 system that has ubuntu 6.06 server installed and running ok.
when i first installed, i had 1 80gb ide HD and 1 ide cdrom.
The fstab looks like this:
    # /etc/fstab: static file system information.
    #
    # <file system> <mount point>   <type>  <options>       <dump>  <pass>
    proc            /proc           proc    defaults        0       0
    /dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
    /dev/hda5       none            swap    sw              0       0
    /dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
    /dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
Since my motherboard (MSI K9N Neo) has 1 ide chanel and 4 sata chanels, 
and i wanted to add a dvdrw, i bought a SATA dvdrw internal.
The bios sees it ok. It's on sata ch. 4.

:|

---

### Post by Pumalite on 2007-11-03
What happens after reboot? Do you have a cdrom device in /dev?

---

### Post by natehatewindows on 2007-11-03
yeah i bet it just mounted it in /dev you might have to manually change where it mounts it in the properties.

---

### Post by bear2 on 2007-11-03
This is what i see in /dev .....i dont see anything obvious....what to look for?

root@pc1:/dev# ls -al | more
total 4
drwxr-xr-x 14 root root       20100 Nov  3 07:35 .
drwxr-xr-x 23 root root        4096 Oct 28 12:16 ..
drwxr-xr-x  2 root root         100 Nov  3 07:34 .initramfs
-rw-r--r--  1 root root           0 Nov  3 07:34 .initramfs-tools
drwxr-xr-x  3 root root          60 Nov  3 07:35 .static
drwxr-xr-x  4 root root          80 Nov  3 07:37 .udev
lrwxrwxrwx  1 root root          13 Nov  3 07:35 MAKEDEV -> /sbin/MAKEDEV
crw-rw----  1 root root     10,  62 Nov  3 07:35 acpi
drwxr-xr-x  3 root root          60 Nov  3 07:35 bus
lrwxrwxrwx  1 root root           3 Nov  3 07:35 cdrom -> hdb
crw-------  1 root root      5,   1 Nov  3 07:35 console
lrwxrwxrwx  1 root root          11 Nov  3 07:35 core -> /proc/kcore
crw-rw----  1 root dialout  52,   0 Nov  3 07:35 dcbri0
crw-rw----  1 root dialout  52,   1 Nov  3 07:35 dcbri1
crw-rw----  1 root dialout  52,   2 Nov  3 07:35 dcbri2
crw-rw----  1 root dialout  52,   3 Nov  3 07:35 dcbri3
drwxr-xr-x  5 root root         100 Nov  3 07:35 disk
drwxr-xr-x  4 root root         120 Nov  3 07:33 evms
crw-rw----  1 root video    29,   0 Nov  3 07:34 fb0
lrwxrwxrwx  1 root root          13 Nov  3 07:35 fd -> /proc/self/fd
brw-rw----  1 root floppy    2,   0 Nov  3 07:35 fd0
crw-rw-rw-  1 root root      1,   7 Nov  3 07:34 full
brw-rw----  1 root disk      3,   0 Nov  3 07:35 hda
brw-rw----  1 root disk      3,   1 Nov  3 07:35 hda1
brw-rw----  1 root disk      3,   2 Nov  3 07:35 hda2
brw-rw----  1 root disk      3,   5 Nov  3 07:35 hda5
brw-rw----  1 root cdrom     3,  64 Nov  3 07:35 hdb
crw-rw----  1 root root     10, 228 Nov  3 07:34 hpet

---

### Post by bear2 on 2007-11-03
After doing some more research....here is more info that may help someone to help me :)

root@pc1:~# lspci
0000:00:00.0 RAM memory: nVidia Corporation: Unknown device 0444 (rev a3)
0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 0441 (rev a3)
0000:00:01.1 SMBus: nVidia Corporation: Unknown device 0446 (rev a1)
0000:00:01.2 RAM memory: nVidia Corporation: Unknown device 0445 (rev a1)
0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 0454 (rev a3)
0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 0455 (rev a3)
0000:00:07.0 0403: nVidia Corporation: Unknown device 044a (rev a1)
0000:00:08.0 PCI bridge: nVidia Corporation: Unknown device 0449 (rev a1)
0000:00:09.0 IDE interface: nVidia Corporation: Unknown device 0448 (rev a1)
0000:00:0a.0 IDE interface: nVidia Corporation: Unknown device 045d (rev a3)
0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 045b (rev a1)
0000:00:0c.0 PCI bridge: nVidia Corporation: Unknown device 045a (rev a1)
0000:00:0d.0 PCI bridge: nVidia Corporation: Unknown device 0458 (rev a1)
0000:00:0e.0 PCI bridge: nVidia Corporation: Unknown device 0459 (rev a1)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:09.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 30)
0000:03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd.: Unknown device 8168 (rev 01)
0000:04:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0392 (rev a1)


root@pc1:~# lsmod
Module                  Size  Used by
isofs                  46848  0
udf                    93984  0
vmnet                  61464  13
vmmon                 159128  0
binfmt_misc            22032  1
ppdev                  18568  0
video                  25992  0
tc1100_wmi             16264  0
sony_acpi              14356  0
pcc_acpi               23296  0
hotkey                 20936  0
dev_acpi               22404  0
container              13440  0
button                 16032  0
acpi_sbs               31768  0
battery                19464  1 acpi_sbs
ac                     14344  1 acpi_sbs
i2c_acpi_ec            14208  1 acpi_sbs
i2c_core               33024  1 i2c_acpi_ec
dm_mod                 69704  1
md_mod                 83192  0
lp                     22208  0
ipv6                  327680  14
r1000                  26240  0
psmouse                47492  0
3c59x                  58676  0
mii                    14848  1 3c59x
pcspkr                 10760  0
tsdev                  17408  0
shpchp                 58272  0
serio_raw              16900  0
floppy                 81160  0
pci_hotplug            38800  1 shpchp
parport_pc             47728  1
parport                50700  3 ppdev,lp,parport_pc
evdev                  21632  1
ext3                  152208  1
jbd                    72872  1 ext3
usbhid                 50080  0
ide_generic             9984  0
ohci_hcd               30596  0
ehci_hcd               43144  0
usbcore               153404  4 usbhid,ohci_hcd,ehci_hcd
ide_disk               26496  3
ide_cd                 42912  0
cdrom                  48312  1 ide_cd
generic                14340  0
amd74xx                24240  0 [permanent]
sata_nv                19716  0
libata                 92576  1 sata_nv
scsi_mod              167032  1 libata
thermal                23692  0
processor              37640  1 thermal
fan                    13576  0
capability             14344  0
commoncap              16896  1 capability
vga16fb                22288  1
cfbcopyarea            12288  1 vga16fb
vgastate               17536  1 vga16fb
cfbimgblt              11392  1 vga16fb
cfbfillrect            12928  1 vga16fb
fbcon                  49792  72
tileblit               11264  1 fbcon
font                   17152  1 fbcon
bitblit                14592  1 fbcon
softcursor             10880  1 bitblit
root@pc1:~#

---

### Post by bear2 on 2007-11-03
Also, i am running this kernel, according to "kernelcheck" :

2.6.15-29-amd64-server

---

### Post by bear2 on 2007-11-03
Looks like switching the sata cable connection from the 'ch-4' motherboard connector to the  'ch-1' connector got it working.  
Does anyone know if there is a fix to this ? Ie. being able to use all 4 sata chanels?
The reason i am interested is that i planned to use the other 3 for sata hard disks in a raid-5 set (supported by my motherboard).

---

