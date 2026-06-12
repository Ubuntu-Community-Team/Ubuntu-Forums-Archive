---
title: "[SOLVED] macbook no sound device found"
date: 2008-10-29
forum: Apple Hardware Users
---

### Post by alwayshere on 2008-10-29
macbook gen 1 single boot ubuntu hardy 8.04 
does not find a sound device 

any help please

---

### Post by cyberdork33 on 2008-10-29
Have you checked that you do not have muted channels? Run 'alsamixer' in a terminal and you can make sure that there are not any channels marked with an 'M'.

---

### Post by manpaz on 2008-10-30
Check your settings on gnome-volume-control, and ensure that you have checked *Line In* in preferences menu.

Then on mixer go to *Line In* and check the box that says ***Line in as output***.

Finally ensure that *PCM* and *Side* are not muted and have volume.

Also you can have done with alsamixer.

   Thanks.

---

### Post by alwayshere on 2008-10-31
The trouble is the sound device itself is not found so i have nothing to adjust or set

---

### Post by alwayshere on 2008-10-31
i think the sound device is sigmatel  it s a generation one  black mackbook

---

### Post by cyberdork33 on 2008-10-31
> **alwayshere said:**
> The trouble is the sound device itself is not found so i have nothing to adjust or set
oh well, that is a deeper issue indeed.

does 'lspci' show your audio device? what is the output of 'lsmod'?

---

### Post by alwayshere on 2008-10-31
lsmod>  lsmod
Module                  Size  Used by
af_packet              21636  2 
ipv6                  255300  8 
i915                   31360  2 
drm                    80660  3 i915
hci_usb                15644  2 
rfcomm                 39188  2 
l2cap                  23300  13 rfcomm
bluetooth              56964  7 hci_usb,rfcomm,l2cap
vboxdrv                42160  0 
uinput                  9216  2 
ppdev                   9348  0 
acpi_cpufreq            7820  1 
cpufreq_powersave       1792  0 
cpufreq_ondemand        8084  1 
cpufreq_userspace       4120  0 
cpufreq_conservative     7200  0 
cpufreq_stats           5124  0 
freq_table              4484  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
sbs                    14216  0 
dock                   10124  0 
sbshc                   6784  1 sbs
container               4736  0 
iptable_filter          2944  0 
ip_tables              13000  1 iptable_filter
x_tables               14852  1 ip_tables
sbp2                   22920  0 
parport_pc             35108  0 
lp                     11332  0 
parport                35912  3 ppdev,parport_pc,lp
loop                   17796  0 
joydev                 11840  0 
usbhid                 30976  0 
hid                    36480  1 usbhid
appletouch             10368  0 
video                  18832  0 
output                  3712  1 video
evdev                  11776  11 
tpm_infineon            9256  0 
tpm                    15392  1 tpm_infineon
tpm_bios                7424  1 tpm
rtc                    13212  0 
sky2                   45572  0 
battery                13316  0 
ac                      6020  0 
button                  8336  0 
pcspkr                  3072  0 
iTCO_wdt               11808  0 
iTCO_vendor_support     3972  1 iTCO_wdt
shpchp                 33428  0 
pci_hotplug            29728  1 shpchp
intel_agp              24596  1 
agpgart                33328  3 drm,intel_agp
ext3                  132872  1 
jbd                    43028  1 ext3
mbcache                 8192  1 ext3
sd_mod                 29584  3 
sg                     36256  0 
sr_mod                 16804  0 
cdrom                  36512  1 sr_mod
pata_acpi               7424  0 
ata_generic             7428  0 
ata_piix               18692  2 
ohci1394               32688  0 
ieee1394               92216  2 sbp2,ohci1394
libata                159728  3 pata_acpi,ata_generic,ata_piix
scsi_mod              151180  5 sbp2,sd_mod,sg,sr_mod,libata
ehci_hcd               36748  0 
uhci_hcd               25616  0 
usbcore               144108  6 hci_usb,usbhid,appletouch,ehci_hcd,uhci_hcd
thermal                15772  0 
processor              28464  3 acpi_cpufreq,thermal
fan                     4740  0 
fbcon                  41888  0 
tileblit                2560  1 fbcon
font                    8576  1 fbcon
bitblit                 5888  1 fbcon
softcursor              2176  1 bitblit
fuse                   48404  3 


---

### Post by alwayshere on 2008-10-31
lspci>  lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:07.0 Performance counters: Intel Corporation Unknown device 27a3 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
03:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)


---

### Post by cyberdork33 on 2008-10-31
Well, we see the hardware exists, but in lsmod, there is no mention of any sound drivers... I think the kernel is failing to load up the driver for some reason.

Try running:
```
sudo modprobe snd-hda-intel
``` and see if it works.

If it does, then you need to add "snd-hda-intel" to /etc/modules

---

### Post by alwayshere on 2008-10-31
sudo modprobe snd-hda-intel>  sudo modprobe snd-hda-intel
FATAL: Module snd_hda_intel not found.
FATAL: Error running install command for snd_hda_intel


---

### Post by cyberdork33 on 2008-10-31
try to reinstall the package linux-ubuntu-modules

```
sudo aptitude reinstall linux-ubuntu-modules
```

(You might have to install aptitude for that command to work.)

---

### Post by manpaz on 2008-10-31
That's true, sounds like you don't have installed the snd-hda-intel module.

Try to install the modules as mentioned above by cyberdork33, then double check you can load modules by issuing the command
```

depmod -a

```

When you have loaded the module on system, check your /etc/modprobe.conf, there is a forum that will explain clear how to  set this file in order to load correctly the modules on boot time.

The link to the mentioned forum is:
[http://ph.ubuntuforums.com/showthread.php?t=611345]("http://ph.ubuntuforums.com/showthread.php?t=611345")

---

### Post by alwayshere on 2008-10-31
I have now done a full reinstall of 8.04 and it now detecting sound devices,I guess it must have been a bad install that caused the trouble

Thanks for all the help :)

---

### Post by cyberdork33 on 2008-11-01
> **alwayshere said:**
> I have now done a full reinstall of 8.04 and it now detecting sound devices,I guess it must have been a bad install that caused the trouble

Thanks for all the help :)

you should be using 8.10 now... it was released 2 days ago.

---

