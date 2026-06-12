---
title: "I believe I need Ubuntu source for nForce install but where to dl?"
date: 2005-11-13
forum: Absolute Beginner Talk
---

### Post by cafevincent on 2005-11-13
There you have it all in the title.  nForce drivers ask the source to be installed but I can't find it in ubuntu downloads so I need some help with that.

---

### Post by DJ_Max on 2005-11-13
We're going to need a little more information to help. What exactly does nForce ask for?

Have you looked here [http://help.ubuntu.com/starterguide/C/ch04.html](http://help.ubuntu.com/starterguide/C/ch04.html) ?

---

### Post by jdong on 2005-11-13
[QUOTE=cafevincent]There you have it all in the title.  nForce drivers ask the source to be installed but I can't find it in ubuntu downloads so I need some help with that.[/QUOTE]

nForce requires kernel *headers* to build, which you can install by running **sudo apt-get install linux-headers-`uname -r`** at a Terminal.

Do you really *need* nForce drivers? Ubuntu includes OSS alternatives to the nForce drivers, which I find to be adequate for most purposes, except maybe surround sound support, which I have yet to use.

---

### Post by cafevincent on 2005-11-13
Using these drivers and instructions
[http://www.nvidia.com/object/linux_nforce_1.0-0306.html](http://www.nvidia.com/object/linux_nforce_1.0-0306.html)
this is what it prints to /var/log/nvidia-nforce-installer.log

```
nforce-installer log file '/var/log/nvidia-nforce-installer.log'
creation time: Sun Nov 13 20:20:52 2005

option status:
  license pre-accepted      : false
  expert                    : false
  uninstall                 : false
  driver info               : false
  no precompiled interface  : false
  no ncurses color          : false
  no questions              : false
  silent                    : false
  Installer install prefix  : /usr
  kernel source path        : (not specified)
  net kernel install path   : (not specified)
  audio kernel install path : (not specified)
  proc mount point          : /proc
  ui                        : (not specified)
  tmpdir                    : /tmp

Using: nvidia-installer ncurses user interface
-> Found package NVIDIA network driver for Linux-x86
-> Found package NVIDIA audio driver for Linux-x86
-> Please select packages for installation:
   Selections:
   NVIDIA audio driver for Linux-x86 (1.0-6)
-> Starting install of NVIDIA audio driver for Linux-x86
-> Checking for loaded module nvsound
-> Checking for loaded module nvaudio
-> License accepted.
-> Skipping check for conflicting rpms.
-> /proc/version is Linux version 2.6.12-9-386 (buildd@rothera) (gcc version
   3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36
   BST 2005
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
ERROR: Unable to find the kernel source tree for the currently running kernel. 
       Please make sure you have installed the kernel source files for your
       kernel; on Red Hat Linux systems, for example, be sure you have the
       'kernel-source' rpm installed.  If you know the correct kernel source
       files are installed, you may specify the kernel source path with the
       '--kernel-source-path' commandline option.
ERROR: Installation of the audio driver has failed.  Please see the file
       '/var/log/nvidia-nforce-installer.log' for details.  You may find
       suggestions on  fixing installation problems in the README available on
       the Linux driver download page at www.nvidia.com.

```

---

### Post by jdong on 2005-11-13
Please answer my post from above. It provides the headers necessary to compile these drivers, but then again evaluate **carefully** whether or not your require the drivers, because I've had lots of "fun" configuring these binary drivers before just to figure out that I really didn't need them.

---

### Post by cafevincent on 2005-11-13
[QUOTE=jdong]nForce requires kernel *headers* to build, which you can install by running **sudo apt-get install linux-headers-`uname -r`** at a Terminal.

Do you really *need* nForce drivers? Ubuntu includes OSS alternatives to the nForce drivers, which I find to be adequate for most purposes, except maybe surround sound support, which I have yet to use.[/QUOTE]

I'm willing to try anything that supports stereo in all basics like mixing audio from different applications like audio player + game. It should also be capable or Dolby Digital and DTS output for my receiver to process. I don't know if what you suggested has anything to do with this [nForce2 audio alternative]("http://www.ubuntuforums.org/showthread.php?t=30076") but it seems to be unable to mix audio from different applications. Please tell me how to install the OSS alternative.

---

### Post by jdong on 2005-11-13
Alright, you sound like you'll need the NVidia binary drivers. I think there's a guide in a Tips Tricks and Customization forum (Hoary's, IIRC) that details exactly how to get it set up, but it's not as simple as just running the installer.

---

### Post by cafevincent on 2005-11-13
[QUOTE=jdong]Alright, you sound like you'll need the NVidia binary drivers. I think there's a guide in a Tips Tricks and Customization forum (Hoary's, IIRC) that details exactly how to get it set up, but it's not as simple as just running the installer.[/QUOTE]

Thanks, got it [http://www.ubuntuforums.org/showthread.php?t=75074]("http://www.ubuntuforums.org/showthread.php?t=75074"). I'll look into it.

---

### Post by jdong on 2005-11-13
no, that's for the NVidia video card.


[http://www.ubuntuforums.org/showpost.php?p=255066&postcount=2](http://www.ubuntuforums.org/showpost.php?p=255066&postcount=2)

This post roughly outlines the post-installation configuration necessary. If you're having trouble following it (it's kind of brief) let us know.

---

### Post by cafevincent on 2005-11-13
> From a console type:
sudo sh NFORCE-Linux-x86-1.0-0301-pkg1.run --uninstall
type:
sh NFORCE-Linux-x86-1.0-0301-pkg1.run -A
to see all te options.

To get the nvidia driver working I created the file /etc/modprobe.d/nvsound with the following line in it:
alias sound-slot-0 nvsound
I added the module that was loaded by default (snd-intel8x0 in my case) to the file /etc/hotplug/blacklist.
The nvsound module is for OSS and not ALSA so your applications should use OSS.

Mo X

Would it be safe to assume I need to add "snd-amd8x0" to /etc/hotplug/blacklist because I use Athlon XP? Or what other modules should I be confused about?

---

### Post by jdong on 2005-11-13
no, add snd-intel8x0 to the blacklist as stated. The NVidia nvsound system is fully compatible with the Intel i810 sound cards, hence the intel8x0. Replacing it with amd makes no sense.

---

### Post by cafevincent on 2005-11-13
[QUOTE=jdong]no, add snd-intel8x0 to the blacklist as stated. The NVidia nvsound system is fully compatible with the Intel i810 sound cards, hence the intel8x0. Replacing it with amd makes no sense.[/QUOTE]

I did all that and rebooted. Can't hear sound, in fact the volume control is now grayed out.  I can find nForce AC97 Audio Controller in the device manager tho (status: status), if that matters.

---

### Post by jdong on 2005-11-13
Post output of lsmod

---

### Post by cafevincent on 2005-11-13
[QUOTE=jdong]Post output of lsmod[/QUOTE]

How do I do that?

---

### Post by jdong on 2005-11-13
Applications->Accessories->Terminal

Type in **lsmod**. Select the output, right click, copy. Then, paste it into here.

---

### Post by cafevincent on 2005-11-13
```
Module                  Size  Used by
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
ipv6                  217408  6
tsdev                   7616  0
analog                 10528  0
gameport               14472  1 analog
snd_mpu401              6344  1
snd_mpu401_uart         6784  1 snd_mpu401
snd_rawmidi            22816  1 snd_mpu401_uart
snd_seq_device          8204  1 snd_rawmidi
snd                    48644  6 snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9184  1 snd
irtty_sir               7808  0
sir_dev                17324  1 irtty_sir
irda                  159804  2 irtty_sir,sir_dev
crc_ccitt               2176  1 irda
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
ohci1394               30644  0
shpchp                 80612  0
pci_hotplug            24628  1 shpchp
i2c_nforce2             6528  0
i2c_core               19728  2 i2c_acpi_ec,i2c_nforce2
nvidia_agp              7964  1
agpgart                32328  1 nvidia_agp
xfs                   499256  4
exportfs                5376  1 xfs
dm_mod                 50364  1
evdev                   9088  0
sr_mod                 15652  0
sbp2                   21128  0
ieee1394               90936  2 ohci1394,sbp2
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
sd_mod                 17424  4
usbhid                 30688  0
3c59x                  37544  0
mii                     5248  1 3c59x
sata_sil                9476  4
forcedeth              19072  0
ehci_hcd               29448  0
ohci_hcd               18564  0
usbcore               104188  4 usbhid,ehci_hcd,ohci_hcd
ide_cd                 36996  0
cdrom                  33952  2 sr_mod,ide_cd
ide_disk               16128  7
ide_generic             1664  0
sata_nv                 9092  0
libata                 47876  2 sata_sil,sata_nv
scsi_mod              124872  4 sr_mod,sbp2,sd_mod,libata
amd74xx                12828  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,amd74xx
unix                   24624  693
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

```

---

### Post by jdong on 2005-11-13
edit /etc/modules, add **nvsound** to the bottom of the list, then reboot.

---

### Post by cafevincent on 2005-11-13
No change.

---

### Post by cafevincent on 2005-11-14
I started to check if everything is still the way it was described in the guide and I ran into this  error message (I hope it helps):

```
sudo gedit /etc/modules
Password:
- using device default
- using device default
ALSA lib pcm_dmix.c:802:(snd_pcm_dmix_open) unable to open slave

```

---

### Post by jdong on 2005-11-14
Post lsmod again.

---

### Post by cafevincent on 2005-11-14
```
Module                  Size  Used by
nls_cp437               5888  1
isofs                  32824  1
udf                    75524  0
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
ipv6                  217408  6
tsdev                   7616  0
analog                 10528  0
gameport               14472  1 analog
snd_mpu401              6344  1
snd_mpu401_uart         6784  1 snd_mpu401
snd_rawmidi            22816  1 snd_mpu401_uart
snd_seq_device          8204  1 snd_rawmidi
snd                    48644  6 snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9184  1 snd
irtty_sir               7808  0
sir_dev                17324  1 irtty_sir
irda                  159804  2 irtty_sir,sir_dev
crc_ccitt               2176  1 irda
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
ohci1394               30644  0
shpchp                 80612  0
pci_hotplug            24628  1 shpchp
i2c_nforce2             6528  0
i2c_core               19728  2 i2c_acpi_ec,i2c_nforce2
nvidia_agp              7964  1
agpgart                32328  1 nvidia_agp
xfs                   499256  4
exportfs                5376  1 xfs
dm_mod                 50364  1
evdev                   9088  0
sr_mod                 15652  0
sbp2                   21128  0
ieee1394               90936  2 ohci1394,sbp2
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
sd_mod                 17424  4
usbhid                 30688  0
3c59x                  37544  0
mii                     5248  1 3c59x
sata_sil                9476  4
forcedeth              19072  0
ehci_hcd               29448  0
ohci_hcd               18564  0
usbcore               104188  4 usbhid,ehci_hcd,ohci_hcd
ide_cd                 36996  1
cdrom                  33952  2 sr_mod,ide_cd
ide_disk               16128  7
ide_generic             1664  0
sata_nv                 9092  0
libata                 47876  2 sata_sil,sata_nv
scsi_mod              124872  4 sr_mod,sbp2,sd_mod,libata
amd74xx                12828  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,amd74xx
unix                   24624  656
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

```

---

### Post by cafevincent on 2005-11-18
[QUOTE=jdong]Post lsmod again.[/QUOTE]

Please help a little more. There's not much I can do with a computer that has no sound. It is the center piece of my living room.

---

### Post by cafevincent on 2005-11-19
Sometimes when doing something else in the terminal I get this error message:

```
- using device default
- using device default
ALSA lib pcm_dmix.c:802:(snd_pcm_dmix_open) unable to open slave

```

---

