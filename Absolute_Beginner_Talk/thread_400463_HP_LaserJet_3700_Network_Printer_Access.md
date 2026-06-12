---
title: "HP LaserJet 3700 Network Printer Access"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by theninthdimension on 2007-04-03
I have been attempting to connect to an HP Color LaserJet 3700n printer that is connected directly to our local area network. This printer is not shared through a computer, but is residing at a static IP address. For the life of me, I can not get my Ubuntu 6.10 install to locate or use this printer. I have been working through CUPS, but to no avail. I have attempted to install the HP Linux drivers, but that process seems to hang (I assume that if the cursor in the command line continues to spin after 3 hours and 49 minutes, the thing has stalled). Any suggestions?

Thanks,

Jeff.

---

### Post by 11hjpphty76lkjj on 2007-04-03
Can you terminate the install,

then 

```
cd hplip-1.7.3
./install.py -g
```

and post the log.

A

---

### Post by theninthdimension on 2007-04-04
kalosaurusrex ,

Here it is in all it's glory:

        libBLTlite.2.4.so.8.4 (libc6) => /usr/lib/libBLTlite.2.4.so.8.4
        libBLTlite.2.4.so.8.3 (libc6) => /usr/lib/libBLTlite.2.4.so.8.3
        libBLT.2.4.so.8.4 (libc6) => /usr/lib/libBLT.2.4.so.8.4
        libBLT.2.4.so.8.3 (libc6) => /usr/lib/libBLT.2.4.so.8.3
        libAiksaurus-1.2.so.0 (libc6) => /usr/lib/libAiksaurus-1.2.so.0
        ld-linux.so.2 (ELF, hwcap: 0x8008000000008000) => /lib/tls/i686/cmov/ld-linux.so.2
        ld-linux.so.2 (ELF) => /lib/ld-linux.so.2

hplip-install[7677]: debug: ***
hplip-install[7677]: debug: Checking for dependency 'libcrypto'...

hplip-install[7677]: debug: Checking for library 'libcrypto'...
hplip-install[7677]: debug: Found.
hplip-install[7677]: debug: Searching for file 'crypto.h' under '/usr/include'...
hplip-install[7677]: debug: File not found.
hplip-install[7677]: debug: have libcrypto = 0
hplip-install[7677]: debug: ***
hplip-install[7677]: debug: Checking for dependency 'gcc'...

hplip-install[7677]: debug: Checking: gcc --version (min ver=0.000000)
hplip-install[7677]: debug: gcc (GCC) 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.


hplip-install[7677]: debug: Found.
hplip-install[7677]: debug: Checking: g++ --version (min ver=0.000000)
hplip-install[7677]: debug: g++ (GCC) 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.


hplip-install[7677]: debug: Found.
hplip-install[7677]: debug: have gcc = 1
hplip-install[7677]: debug: ***
hplip-install[7677]: debug: Checking for dependency 'sane'...

hplip-install[7677]: debug: Checking for library 'libsane'...
hplip-install[7677]: debug: Found.
hplip-install[7677]: debug: have sane = 1
hplip-install[7677]: debug: ***
hplip-install[7677]: debug: Checking for dependency 'gs'...

hplip-install[7677]: debug: Checking: gs -v (min ver=7.050000)
hplip-install[7677]: debug: ESP Ghostscript 8.15.2 (2006-04-19)
Copyright (C) 2004 artofcode LLC, Benicia, CA.  All rights reserved.

hplip-install[7677]: debug: ESP Ghostscript 8.15.2 (2006-04-19)
hplip-install[7677]: debug: Ver=8.150000 Min ver=7.050000
hplip-install[7677]: debug: have gs = 1
hplip-install[7677]: debug: ***
hplip-install[7677]: debug: Checking for dependency 'libjpeg'...

hplip-install[7677]: debug: Checking for library 'libjpeg'...
hplip-install[7677]: debug: Found.
hplip-install[7677]: debug: Searching for file 'jpeglib.h' under '/usr/include'...
hplip-install[7677]: debug: File not found.
hplip-install[7677]: debug: have libjpeg = 0
hplip-install[7677]: debug: ***
hplip-install[7677]: debug: Checking for dependency 'libpthread'...

hplip-install[7677]: debug: Checking for library 'libpthread'...
hplip-install[7677]: debug: Found.
hplip-install[7677]: debug: Searching for file 'pthread.h' under '/usr/include'...
hplip-install[7677]: debug: File found at '/usr/include/pthread.h'
hplip-install[7677]: debug: have libpthread = 1
hplip-install[7677]: debug: ***
hplip-install[7677]: debug: Checking for dependency 'make'...

hplip-install[7677]: debug: Checking: make --version (min ver=3.000000)
hplip-install[7677]: debug: GNU Make 3.81
Copyright (C) 2006  Free Software Foundation, Inc.
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.

This program built for i486-pc-linux-gnu

hplip-install[7677]: debug: GNU Make 3.81
hplip-install[7677]: debug: Ver=3.810000 Min ver=3.000000
hplip-install[7677]: debug: have make = 1
hplip-install[7677]: debug: ***
hplip-install[7677]: debug: Checking for dependency 'python-devel'...

hplip-install[7677]: debug: Searching for file 'Python.h' under '/usr/include'...
hplip-install[7677]: debug: File not found.
hplip-install[7677]: debug: have python-devel = 0
hplip-install[7677]: debug: ***
hplip-install[7677]: debug: Checking for dependency 'reportlab'...

hplip-install[7677]: debug: Trying to import 'reportlab'...
hplip-install[7677]: debug: Failed.
hplip-install[7677]: debug: have reportlab = 0
hplip-install[7677]: debug: ***
hplip-install[7677]: debug: Checking for dependency 'pyqt'...

hplip-install[7677]: debug: PYQT_VERSION_STR = 3.16
hplip-install[7677]: debug: Version 3.16.0 installed.
hplip-install[7677]: debug: have pyqt = 1
hplip-install[7677]: debug: ***
hplip-install[7677]: debug: Checking for dependency 'cups-devel'...

hplip-install[7677]: debug: Searching for file 'cups.h' under '/usr/include'...
hplip-install[7677]: debug: File not found.
hplip-install[7677]: debug: have cups-devel = 0
hplip-install[7677]: debug: ***
hplip-install[7677]: debug: Checking for dependency 'ppdev'...

hplip-install[7677]: debug: Module                  Size  Used by
nls_cp437               6912  1 
isofs                  38076  1 
udf                    89348  0 
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
nfsd                  234276  13 
exportfs                7296  1 nfsd
lockd                  67976  2 nfsd
sunrpc                165948  8 nfsd,lockd
speedstep_centrino      9760  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  2 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sbs                    16804  0 
sony_acpi               6412  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
hotkey                 11556  0 
dev_acpi               12292  0 
button                  7952  0 
battery                11652  0 
container               5632  0 
ac                      6788  0 
asus_acpi              17688  0 
sctp                  171440  2 [unsafe]
dlm                   101180  0 
configfs               29840  2 dlm
ipv6                  272288  21 sctp
nls_utf8                3200  1 
ntfs                  112116  1 
dm_mod                 62872  0 
md_mod                 82836  0 
sbp2                   24584  0 
parport_pc             37796  0 
lp                     12964  0 
parport                39496  2 parport_pc,lp
af_packet              24584  2 
nvidia               4554836  12 
joydev                 11200  0 
snd_hda_intel          20116  4 
snd_hda_codec         164608  1 snd_hda_intel
tsdev                   9152  0 
i2c_core               23424  2 i2c_ec,nvidia
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
sr_mod                 18212  1 
cdrom                  38944  1 sr_mod
psmouse                41352  0 
sg                     37404  0 
snd_pcm                84612  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25348  2 snd_pcm
usb_storage            75072  0 
libusual               17040  1 usb_storage
intel_agp              26012  1 
agpgart                34888  2 nvidia,intel_agp
hw_random               7320  0 
serio_raw               8452  0 
usbhid                 45152  0 
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
pcspkr                  4352  0 
snd                    58372  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
e1000                 128452  0 
evdev                  11392  2 
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
floppy                 63044  0 
ext3                  142856  1 
jbd                    62228  1 ext3
ohci1394               37040  0 
ieee1394              306104  2 sbp2,ohci1394
ehci_hcd               34696  0 
uhci_hcd               24968  0 
usbcore               134912  6 usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd
ide_generic             2432  0 
sd_mod                 22656  5 
ahci                   20356  4 
libata                 74892  1 ahci
scsi_mod              144648  7 sbp2,sr_mod,sg,usb_storage,sd_mod,ahci,libata
thermal                15624  0 
processor              31560  2 speedstep_centrino,thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability

hplip-install[7677]: debug: have ppdev = 0
hplip-install[7677]: debug: ***
hplip-install[7677]: debug: Checking for dependency 'libusb'...

hplip-install[7677]: debug: Checking for library 'libusb'...
hplip-install[7677]: debug: Found.
hplip-install[7677]: debug: Searching for file(s) 'usb.h' under '/usr/include'...
hplip-install[7677]: debug: No files not found.
hplip-install[7677]: debug: have libusb = 0
hplip-install[7677]: debug: ***
hplip-install[7677]: debug: Checking for dependency 'scanimage'...

hplip-install[7677]: debug: Checking: scanimage --version (min ver=1.000000)
hplip-install[7677]: debug: Not found!
hplip-install[7677]: debug: have scanimage = 0
hplip-install[7677]: debug: ***
hplip-install[7677]: debug: Checking for dependency 'libnetsnmp-devel'...

hplip-install[7677]: debug: Checking for library 'libnetsnmp'...
hplip-install[7677]: debug: Found.
hplip-install[7677]: debug: Searching for file 'net-snmp-config.h' under '/usr/include'...
hplip-install[7677]: debug: File not found.
hplip-install[7677]: debug: have libnetsnmp-devel = 0
hplip-install[7677]: debug: ***
hplip-install[7677]: debug: Checking for dependency 'python2x'...

hplip-install[7677]: debug: Python ver=2.4
hplip-install[7677]: debug: have python2x = 1
hplip-install[7677]: debug: ***
hplip-install[7677]: debug: Checking for dependency 'lsb'...

hplip-install[7677]: debug: Searching for file 'install_initd' under '/usr/lib/lsb'...
hplip-install[7677]: debug: File not found.
hplip-install[7677]: debug: Searching for file 'install_initd' under '/usr/sbin'...
hplip-install[7677]: debug: File not found.
hplip-install[7677]: debug: Searching for file 'install_initd' under '/usr/bin'...
hplip-install[7677]: debug: File not found.
hplip-install[7677]: debug: have lsb = 0
hplip-install[7677]: debug: ***
hplip-install[7677]: debug: Checking for dependency 'xsane'...

hplip-install[7677]: debug: Checking: xsane --version (min ver=0.900000)
hplip-install[7677]: debug: xsane-0.991 (c) 1998-2006 Oliver Rauch
  E-mail: [email]Oliver.Rauch@xsane.org[/email]
  package xsane-0.991
  compiled with GTK-2.10.6
  with GIMP support, compiled with GIMP-2.2.13
  XSane output formats: jpeg, pdf(compr.), png, pnm, ps(compr.), tiff, txt

hplip-install[7677]: debug: xsane-0.991 (c) 1998-2006 Oliver Rauch
hplip-install[7677]: debug: Ver=0.991000 Min ver=0.900000
hplip-install[7677]: debug: have xsane = 1
hplip-install[7677]: debug: ***
hplip-install[7677]: debug: Checking for dependency 'cups'...

hplip-install[7677]: debug: scheduler is running

hplip-install[7677]: debug: CUPS is running.
hplip-install[7677]: debug: have cups = 1
hplip-install[7677]: debug: ***
hplip-install[7677]: debug: Checking for dependency 'python23'...

hplip-install[7677]: debug: Python ver=2.4
hplip-install[7677]: debug: have python23 = 1
hplip-install[7677]: debug: ******
hplip-install[7677]: debug: have libcrypto = 0
hplip-install[7677]: debug: have gcc = 1
hplip-install[7677]: debug: have sane = 1
hplip-install[7677]: debug: have gs = 1
hplip-install[7677]: debug: have libjpeg = 0
hplip-install[7677]: debug: have libpthread = 1
hplip-install[7677]: debug: have make = 1
hplip-install[7677]: debug: have python-devel = 0
hplip-install[7677]: debug: have reportlab = 0
hplip-install[7677]: debug: have pyqt = 1
hplip-install[7677]: debug: have cups-devel = 0
hplip-install[7677]: debug: have ppdev = 0
hplip-install[7677]: debug: have libusb = 0
hplip-install[7677]: debug: have scanimage = 0
hplip-install[7677]: debug: have libnetsnmp-devel = 0
hplip-install[7677]: debug: have python2x = 1
hplip-install[7677]: debug: have lsb = 0
hplip-install[7677]: debug: have xsane = 1
hplip-install[7677]: debug: have cups = 1
hplip-install[7677]: debug: have python23 = 1
hplip-install[7677]: debug: ******
hplip-install[7677]: debug: Searching for '['yast', 'yast2', 'yum', 'rpm', 'up2date', 'apt-get', 'synaptic', 'dpkg', 'update-manager', 'adept', 'adept-notifier', 'aptitude', 'urpmi']' in 'ps' output...
hplip-install[7677]: debug: Running package manager: dpkg
hplip-install[7677]: debug: Bitness = 32
hplip-install[7677]: debug: Endian = 1
hplip-install[7677]: debug: Determining distro...
hplip-install[7677]: debug: Using 'lsb_release -i/-r'
hplip-install[7677]: debug: Distributor ID:     Ubuntu

hplip-install[7677]: debug: Release:    6.10

hplip-install[7677]: debug: LSB: ubuntu 6.10
hplip-install[7677]: debug: distro=12, distro_version=6.10
hplip-install[7677]: debug: Distro = 12 Distro Name = ubuntu Display Name= Ubuntu Version = 6.10 Supported = True
hplip-install[7677]: debug: Checking for 'HPOJ'...
hplip-install[7677]: debug: Searching any process(es) '['ptal-mlcd', 'ptal-printd', 'ptal-photod']' in 'ps' output...
hplip-install[7677]: debug:   PID TTY      STAT   TIME COMMAND
    1 ?        Ss     0:03 /sbin/init splash
    2 ?        S      0:00 [migration/0]
    3 ?        SN     0:00 [ksoftirqd/0]
    4 ?        S      0:00 [watchdog/0]
    5 ?        S      0:00 [migration/1]
    6 ?        SN     0:00 [ksoftirqd/1]
    7 ?        S      0:00 [watchdog/1]
    8 ?        S<     0:00 [events/0]
    9 ?        S<     0:00 [events/1]
   10 ?        S<     0:00 [khelper]
   11 ?        S<     0:00 [kthread]
   14 ?        S<     0:00 [kblockd/0]
   15 ?        S<     0:00 [kblockd/1]
   16 ?        S<     0:00 [kacpid]
   17 ?        S<     0:00 [kacpi_notify]
   95 ?        S<     0:00 [kseriod]
  136 ?        S      0:00 [pdflush]
  137 ?        S      0:00 [pdflush]
  138 ?        S      0:00 [kswapd0]
  139 ?        S<     0:00 [aio/0]
  140 ?        S<     0:00 [aio/1]
  774 ?        S      0:00 [kirqd]
 1629 ?        S<     0:00 [ata/0]
 1630 ?        S<     0:00 [ata/1]
 1636 ?        S<     0:00 [scsi_eh_0]
 1637 ?        S<     0:00 [scsi_eh_1]
 1638 ?        S<     0:00 [scsi_eh_2]
 1639 ?        S<     0:00 [scsi_eh_3]
 1640 ?        S<     0:00 [scsi_eh_4]
 1641 ?        S<     0:00 [scsi_eh_5]
 1784 ?        S<     0:00 [khubd]
 1796 ?        S<     0:00 [khpsbpkt]
 1853 ?        S      0:00 [knodemgrd_0]
 1898 ?        S<     0:00 [kjournald]
 1988 ?        Ss     0:00 //sbin/logd
 2135 ?        S<s    0:00 /sbin/udevd --daemon
 2968 ?        S<     0:00 [shpchpd]
 3074 ?        S<     0:00 [scsi_eh_6]
 3075 ?        S<     0:00 [usb-storage]
 3077 ?        S<     0:00 [scsi_eh_7]
 3078 ?        S<     0:00 [usb-storage]
 3082 ?        S<     0:00 [scsi_eh_8]
 3083 ?        S<     0:00 [usb-storage]
 3112 ?        S<     0:00 [kpsmoused]
 3285 ?        S<     0:00 [hda_codec]
 3534 ?        S<s    0:00 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/lib
 3876 ?        Ss     0:00 /sbin/portmap
 4012 ?        Ssl    0:00 /usr/sbin/ccsd
 4050 ?        S<s    0:00 /usr/sbin/clurgmgrd
 4051 ?        S<     0:00 /usr/sbin/clurgmgrd
 4139 tty1     Ss+    0:00 /sbin/getty 38400 tty1
 4140 tty2     Ss+    0:00 /sbin/getty 38400 tty2
 4141 tty3     Ss+    0:00 /sbin/getty 38400 tty3
 4142 tty4     Ss+    0:00 /sbin/getty 38400 tty4
 4143 tty5     Ss+    0:00 /sbin/getty 38400 tty5
 4144 tty6     Ss+    0:00 /sbin/getty 38400 tty6
 4372 ?        Ss     0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid
 4496 ?        Ss     0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
 4498 ?        Ss     0:00 /sbin/klogd -P /var/run/klogd/kmsg
 4572 ?        Ss     0:00 /usr/sbin/gdm
 4627 ?        Ss     0:00 /usr/sbin/hpiod
 4633 ?        S      0:00 python /usr/sbin/hpssd
 4682 ?        Ss     0:00 /usr/sbin/apt-index-watcher watch --syslog
 4698 ?        Ss     0:00 /usr/bin/dbus-daemon --system
 4713 ?        Ss     0:01 /usr/sbin/hald
 4714 ?        S      0:00 hald-runner
 4720 ?        S      0:00 /usr/lib/hal/hald-addon-acpi
 4726 ?        S      0:00 /usr/lib/hal/hald-addon-keyboard
 4729 ?        S      0:00 /usr/lib/hal/hald-addon-keyboard
 4745 ?        S      0:00 /usr/lib/hal/hald-addon-storage
 4747 ?        S      0:00 /usr/lib/hal/hald-addon-storage
 4751 ?        S      0:00 /usr/lib/hal/hald-addon-storage
 4753 ?        S      0:00 /usr/lib/hal/hald-addon-storage
 4757 ?        S      0:00 /usr/lib/hal/hald-addon-storage
 4759 ?        S      0:00 /usr/lib/hal/hald-addon-storage
 4761 ?        S      0:00 /usr/lib/hal/hald-addon-storage
 4763 ?        S      0:00 /usr/lib/hal/hald-addon-storage
 4765 ?        S      0:00 /usr/lib/hal/hald-addon-storage
 4767 ?        S      0:00 /usr/lib/hal/hald-addon-storage
 4791 ?        S      0:00 perl /usr/share/system-tools-backends-2.0/scripts/Sys
 4852 ?        S<     0:00 [nfsd4]
 4853 ?        S      0:00 [nfsd]
 4854 ?        S      0:00 [lockd]
 4855 ?        S<     0:00 [rpciod/0]
 4856 ?        S<     0:00 [rpciod/1]
 4857 ?        S      0:00 [nfsd]
 4858 ?        S      0:00 [nfsd]
 4859 ?        S      0:00 [nfsd]
 4860 ?        S      0:00 [nfsd]
 4861 ?        S      0:00 [nfsd]
 4862 ?        S      0:00 [nfsd]
 4863 ?        S      0:00 [nfsd]
 4867 ?        Ss     0:00 /usr/sbin/rpc.mountd
 4887 ?        S<     0:00 [ondemand]
 4897 ?        Ss     0:00 pure-ftpd (SERVER)                                  
 4906 ?        Ss     0:00 /usr/sbin/nvtvd --quiet
 4912 ?        Ss     0:00 /usr/sbin/nmbd -D
 4914 ?        Ss     0:00 /usr/sbin/smbd -D
 4967 ?        Ss     0:00 /sbin/rpc.statd
 4968 ?        S      0:00 /usr/sbin/smbd -D
 4984 ?        Ss     0:00 /usr/sbin/hcid -x
 4988 ?        Ss     0:00 /usr/sbin/sdpd
 5008 ?        S<     0:00 [krfcommd]
 5022 ?        Ss     0:00 /sbin/mdadm --monitor --pid-file /var/run/mdadm.pid -
 5044 ?        SLs    0:00 /usr/sbin/ntpd -p /var/run/ntpd.pid -u 112:116
 5076 ?        Ss     0:00 /usr/sbin/atd
 5089 ?        Ss     0:00 /usr/sbin/cron
 5287 ?        SNs    0:00 /usr/sbin/cupsd
 5416 ?        SNs    0:00 /sbin/syslogd
 5574 ?        S      0:00 /usr/lib/libgconf2-4/gconfd-2 5
 6209 ?        S      0:00 /usr/sbin/gdm
 6210 tty7     SLs+   0:34 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:
 6231 ?        Ss     0:00 x-session-manager
 6266 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-s
 6269 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session x-session-ma
 6270 ?        Ss     0:00 /usr/bin/dbus-daemon --fork --print-pid 8 --print-add
 6273 ?        S      0:00 /usr/bin/gnome-keyring-daemon
 6276 ?        Sl     0:00 /usr/lib/control-center/gnome-settings-daemon
 6286 ?        Ss     0:00 /bin/sh -c /usr/bin/esd -terminate -nobeeps -as 1 -sp
 6287 ?        S      0:00 /usr/bin/esd -terminate -nobeeps -as 1 -spawnfd 19
 6294 ?        Ss     0:01 /usr/bin/metacity --sm-client-id=default0
 6299 ?        Ss     0:02 gnome-panel --sm-client-id default1
 6301 ?        Ss     0:06 nautilus --no-default-window --sm-client-id default2
 6305 ?        Ssl    0:00 /usr/lib/bonobo-activation/bonobo-activation-server -
 6308 ?        Sl     0:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
 6316 ?        Ss     0:00 gnome-volume-manager --sm-client-id default4
 6318 ?        Ss     0:00 update-notifier
 6320 ?        Ssl    0:00 /usr/lib/evolution/2.8/evolution-alarm-notify
 6337 ?        Ss     0:00 gnome-cups-icon --sm-client-id default3
 6346 ?        Sl     0:00 /usr/lib/evolution/evolution-data-server-1.8 --oaf-ac
 6347 ?        Ss     0:00 gnome-power-manager
 6361 ?        Sl     0:00 /usr/lib/evolution/2.8/evolution-exchange-storage --o
 6376 ?        S      0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid
 6390 ?        S      0:00 /usr/lib/gnome-applets/cpufreq-applet --oaf-activate-
 6392 ?        S      0:00 /usr/lib/gnome-netstatus/gnome-netstatus-applet --oaf
 6394 ?        S      0:00 /usr/lib/gnome-applets/multiload-applet-2 --oaf-activ
 6396 ?        S      0:00 /usr/lib/gnome-applets/stickynotes_applet --oaf-activ
 6399 ?        S      0:00 /usr/lib/nautilus-cd-burner/mapping-daemon
 6402 ?        S      0:00 /usr/lib/gnome-utils/gnome-dictionary-applet --oaf-ac
 6404 ?        S      0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-i
 6449 ?        Ss     0:00 gnome-screensaver
 6534 ?        Sl     0:37 /usr/lib/firefox/firefox-bin
 6660 ?        SLs    0:00 mplayer -wid 0x2c019cb -vf scale=280:-3 -osdlevel 0 -
 6662 ?        S      0:00 mplayer -wid 0x2c019cb -vf scale=280:-3 -osdlevel 0 -
 6675 ?        Ss     0:00 mplayer -wid 0x2c019cb -vf scale=280:-3 -osdlevel 0 -
 7454 ?        Ss     0:00 dpkg --configure -a
 7455 ?        S      0:00 /bin/sh /var/lib/dpkg/info/flumotion.postinst configu
 7456 ?        S      0:00 /usr/bin/perl -w /usr/share/debconf/frontend /usr/sbi
 7462 ?        S      0:00 /bin/bash -e /usr/sbin/make-ssl-cert /usr/share/ssl-c
 7464 ?        R      3:43 whiptail --backtitle Ubuntu Configuration --title Con
 7648 ?        Sl     0:00 gnome-terminal
 7651 ?        S      0:00 gnome-pty-helper
 7652 pts/0    Ss     0:00 bash
 7677 pts/0    S+     0:00 python ./install.py -g
 7696 pts/2    Rs+    0:00 /bin/ps ax

hplip-install[7677]: debug: Process not found.
hplip-install[7677]: debug: HPOJ = False
hplip-install[7677]: debug: Checking for HPLIP (previous install)...
hplip-install[7677]: debug: Searching any process(es) '['hpssd', 'hpiod']' in 'ps' output...
hplip-install[7677]: debug: ' 4627 ?        Ss     0:00 /usr/sbin/hpiod' found.
hplip-install[7677]: debug: HPLIP (prev install) = True
Initializing...

note: Defaults for each question are maked with a '*'. Press <enter> to accept the default.


INSTALLATION MODE
-----------------
Please choose the installation mode (a=automatic*, c=custom, q=quit) :

---

### Post by 11hjpphty76lkjj on 2007-04-04
>  INSTALLATION MODE
-----------------
Please choose the installation mode (a=automatic*, c=custom, q=quit) :

When at the above step you'll need to enter 'a' and press enter...

continue with the install procedure until hplip stops or hangs.  then copy the log to a text file and upload that instead.

A

---

### Post by theninthdimension on 2007-04-04
kalosaurusrex,

     I'm sorry, I thought that was what I had posted. To be honest, I'm not sure that the hplip process every really stops or hangs per se. I started the process today at 09:24 and it is still spinning away in the terminal at 11:53. All I have is the following message:

Running 'sudo dpkg --configure -a'
Please wait, this may take several minutes...


with a spinning dash/slash sign. I may not have correctly stopped or terminated the process before the last output I attached. How do I stop something like this? All I've been doing is closing the terminal window.

I should note that the result seems to be the same regardless of whether I go with the automated or custom install.

Thanks,

Jeff.

---

### Post by theninthdimension on 2007-04-04
Folks,

     This problem has been fixed. Apparently, I had a partial install of Flumotion sitting on my system. Once I found this and got the partial install fully uninstalled, the HPLIP program worked like a dream.

Thanks,

Jeff.

---

