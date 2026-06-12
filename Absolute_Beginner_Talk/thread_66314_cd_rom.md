---
title: "cd rom"
date: 2005-09-16
forum: Absolute Beginner Talk
---

### Post by andrewllan on 2005-09-16
I have installed Ubuntu on a pc and when I try to mount cdrom I get the following message 
special device /dev/hdc does not exsist 
anybody please help
Thanks

---

### Post by Kapre on 2005-09-16
[QUOTE=andrewllan]I have installed Ubuntu on a pc and when I try to mount cdrom I get the following message 
special device /dev/hdc does not exsist 
anybody please help
Thanks[/QUOTE]

Andrewllan - I would guest that when you installed ubuntu on your PC, you've used this drive. On the terminal type "sudo mount /media/cdrom0 -o unhide (this is assuming it has been mounted at /media/cdrom0.

EDIT: Did you try putting a Disc on the CDDrive. Maybe it is just hiding and once a disc is in it will show.

K

---

### Post by andrewllan on 2005-09-19
I tried to type in what you said but still keeps up special device  /dev/hdc does not exsist

---

### Post by bereillyte on 2005-10-13
I had exactly this problem and the resolution was that I had a DVD in a CD drive, once I put a CD in, it was fine :-)

---

### Post by 11hjpphty76lkjj on 2005-10-14
I'm having the same problem.  Was working great before, did a reinstall and now the cd-rom isn't there.

The /dev/hdc isn't even in the dev dir. Nor is there any /dev/hd*.  (I'm booting from a usb device) this WAS working before I reinstalled.  So I'm really confused as to what the problem is.  I've added an ide modules to the modules file and reboot.  Same thing..any ideas?

Thanks.

Aaron

---

### Post by 11hjpphty76lkjj on 2005-10-14
/dev$ ls -la | grep h*
crw-rw----   1 root root     10, 228 2005-10-14 11:25 hpet

I've tried restarting udev.

hald is running:

/dev$ ps ax | grep hal
 5951 ?        Ss     0:00 /usr/sbin/hald

I've tried changing the /etc/default/hal and commenting out the:

DAEMON_OPTS=--drop-privileges

then restarting.

Next i'm going to try booting the ubuntu cd and going through rescue and remaking the boot img.  I'll update in t a few min.

Aaron

---

### Post by 11hjpphty76lkjj on 2005-10-14
Still not working...here is everything I could think of to check:


```
aaron@ubuntu:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
ehci-hcd
uhcd-hcd
ohcd-hcd
usb-storage
ide-core
ide-common
ide-cd




aaron@ubuntu:$ lsmod
Module                  Size  Used by
isofs                  33848  0
udf                    77060  0
proc_intf               4100  0
freq_table              4100  0
cpufreq_userspace       4572  0
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0
video                  16260  0
sony_acpi               6280  0
pcc_acpi               11264  0
button                  6800  0
battery                10244  0
container               4608  0
ac                      4996  0
lp                     10792  0
ipv6                  229376  18
af_packet              20744  2
3c59x                  37160  0
amd74xx                13340  0
pci_hotplug            30512  0
snd_intel8x0           29984  2
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  3 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm
i2c_nforce2             6400  0
i2c_core               21264  1 i2c_nforce2
nvidia_agp              7452  1
agpgart                31784  1 nvidia_agp
floppy                 54864  0
parport_pc             34372  1
parport                33480  2 lp,parport_pc
mousedev               11160  1
tsdev                   7488  0
psmouse                19336  0
pcspkr                  3816  0
rtc                    12216  0
evdev                   9088  0
md                     43856  0
dm_mod                 53116  1
capability              5000  0
commoncap               7808  1 capability
ext3                  120968  1
jbd                    54168  1 ext3
sd_mod                 16784  3
unix                   26164  658
thermal                13576  0
processor              22708  1 thermal
fan                     4612  0
fbcon                  34048  0
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb
ide_cd                 38532  0
cdrom                  36508  1 ide_cd
usb_storage            64064  4
scsi_mod              119936  2 sd_mod,usb_storage
ide_core              118988  3 amd74xx,ide_cd,usb_storage
ohci_hcd               19848  0
uhci_hcd               30224  0
ehci_hcd               29444  0
usbcore               107384  5 usb_storage,ohci_hcd,uhci_hcd,ehci_hcd


aaron@ubuntu:~$ cd /dev
aaron@ubuntu:/dev$ ls | grep hd*
hpet
shm
aaron@ubuntu:/dev$ sudo mount /media/cdrom
Password:
mount: special device /dev/hdc does not exist
aaron@ubuntu:/dev$ sudo mount /media/cdrom0
mount: special device /dev/hdc does not exist
aaron@ubuntu:/dev$ mount -a
mount: only root can do that
aaron@ubuntu:/dev$ sudo mount -a
aaron@ubuntu:/dev$ sudo mount /dev/hdc
mount: special device /dev/hdc does not exist
aaron@ubuntu:/dev$ sudo mount /dev/hdd
mount: special device /dev/hdd does not exist
aaron@ubuntu:/dev$ sudo mount /dev/hdb
mount: can't find /dev/hdb in /etc/fstab or /etc/mtab
aaron@ubuntu:/dev$ ls | grep h*
hpet
aaron@ubuntu:/dev$ ls -a | grep h*
hpet
aaron@ubuntu:/dev$ mount /dev/hdc
mount: special device /dev/hdc does not exist
aaron@ubuntu:/dev$ mount /dev/sdb
mount: can't find /dev/sdb in /etc/fstab or /etc/mtab
aaron@ubuntu:/dev$ cat /etc/mtab
/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
usbfs /proc/bus/usb usbfs rw 0 0
/dev /.dev unknown rw,bind 0 0
none /dev tmpfs rw,size=5M,mode=0755 0 0
aaron@ubuntu:/dev$
aaron@coreprime:/dev$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0


aaron@ubuntu:/dev$ ps ax | grep udev
 1017 ?        S<s    0:00 udevd

aaron@ubuntu:/dev$ ps ax | grep hal
 6177 ?        Ss     0:00 /usr/sbin/hald --drop-privileges



aaron@coreprime:/dev$ ps ax
  PID TTY      STAT   TIME COMMAND
    1 ?        S      0:00 init [2]
    2 ?        SN     0:00 [ksoftirqd/0]
    3 ?        S<     0:00 [events/0]
    4 ?        S<     0:00 [khelper]
   22 ?        S<     0:00 [kacpid]
  108 ?        S<     0:00 [kblockd/0]
  146 ?        S      0:00 [pdflush]
  147 ?        S      0:00 [pdflush]
  149 ?        S<     0:00 [aio/0]
  148 ?        S      0:00 [kswapd0]
  736 ?        S      0:00 [kseriod]
  849 ?        S      0:00 [khubd]
  893 ?        S      0:00 [scsi_eh_0]
  894 ?        S      0:01 [usb-storage]
  966 ?        S      0:00 [kjournald]
 1017 ?        S<s    0:00 udevd
 5041 ?        S<s    0:00 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/run
 5393 ?        Ss     0:00 /sbin/syslogd -u syslog
 5408 ?        Ss     0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
 5410 ?        Ss     0:00 /sbin/klogd -P /var/run/klogd/kmsg
 5440 ?        Ss     0:00 /usr/bin/gdm
 5450 ?        S      0:00 /usr/bin/gdm
 5486 ?        S      0:17 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:
 5635 ?        Ss     0:00 /usr/sbin/cupsd -F
 6037 ?        Ss     0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid
 6154 ?        Ss     0:00 /usr/bin/freshclam -d --quiet
 6165 ?        Ss     0:00 /usr/bin/dbus-daemon-1 --system
 6177 ?        Ss     0:00 /usr/sbin/hald --drop-privileges
 6191 ?        Ss     0:00 /usr/sbin/inetd
 6288 ?        S      0:00 /bin/sh /usr/bin/mysqld_safe
 6330 ?        Sl     0:00 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/my
 6331 ?        S      0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
 6376 ?        Ss     0:00 nessusd: waiting for incoming connections
 6434 ?        Ss     0:00 x-session-manager
 6445 ?        Ss     0:00 /usr/lib/postfix/master
 6455 ?        S      0:00 pickup -l -t fifo -u -c
 6456 ?        S      0:00 qmgr -l -t fifo -u -c
 6636 ?        Ss     0:00 /usr/sbin/nmbd -D
 6643 ?        Ss     0:00 /usr/sbin/smbd -D
 6656 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-s
 6658 ?        Ss     0:00 /usr/sbin/sshd
 6668 ?        S      0:00 /usr/sbin/smbd -D
 6673 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session x-session-ma
 6678 ?        Ss     0:00 dbus-daemon-1 --fork --print-pid 8 --print-address 6
 6690 ?        Ss     0:00 /usr/sbin/atd
 6701 ?        S      0:00 /usr/lib/gconf2/gconfd-2 5
 6703 ?        Ss     0:00 /usr/sbin/cron
 6717 ?        Ss     0:00 /usr/sbin/apache2 -k start -DSSL
 6739 tty1     Ss+    0:00 /sbin/getty 38400 tty1
 6740 tty2     Ss+    0:00 /sbin/getty 38400 tty2
 6741 tty3     Ss+    0:00 /sbin/getty 38400 tty3
 6742 tty4     Ss+    0:00 /sbin/getty 38400 tty4
 6743 tty5     Ss+    0:00 /sbin/getty 38400 tty5
 6744 tty6     Ss+    0:00 /sbin/getty 38400 tty6
 6835 ?        S      0:00 /usr/sbin/apache2 -k start -DSSL
 6836 ?        S      0:00 /usr/sbin/apache2 -k start -DSSL
 6837 ?        S      0:00 /usr/sbin/apache2 -k start -DSSL
 6838 ?        S      0:00 /usr/sbin/apache2 -k start -DSSL
 6839 ?        S      0:00 /usr/sbin/apache2 -k start -DSSL
 6841 ?        S      0:00 /usr/bin/gnome-keyring-daemon
 6843 ?        S      0:00 /usr/bin/esd -nobeeps
 6845 ?        Ss     0:00 /usr/lib/bonobo-activation/bonobo-activation-server -
 6847 ?        S      0:00 /usr/lib/control-center/gnome-settings-daemon --oaf-a
 6850 ?        S      0:00 /usr/lib/gamin/gam_server
 6858 ?        S      0:00 xscreensaver -nosplash
 6882 ?        Ss     0:00 gnome-smproxy --sm-config-prefix /.gnome-smproxy-iHkl
 6884 ?        Ss     0:00 metacity --sm-save-file 1129312923-6659-3217118115.ms
 6886 ?        Ssl    0:00 gnome-panel --sm-config-prefix /gnome-panel-oBotcq/ -
 6888 ?        Ss     0:00 gnome-volume-manager --sm-config-prefix /gnome-volume
 6890 ?        Ssl    0:01 nautilus --sm-config-prefix /nautilus-m3oYLz/ --sm-cl
 6893 ?        Ss     0:00 update-notifier --sm-config-prefix /update-notifier-x
 6895 ?        Ssl    0:00 gnome-cups-icon --sm-config-prefix /gnome-cups-icon-d
 6897 ?        Ssl    0:01 gnome-terminal --sm-config-prefix /gnome-terminal-wse
 6903 ?        Sl     0:00 /usr/lib/gnome-vfs2/gnome-vfs-daemon --oaf-activate-i
 6910 ?        S      0:00 /usr/lib/nautilus-cd-burner/mapping-daemon
 6915 ?        S      0:00 gnome-pty-helper
 6916 pts/0    Ss+    0:00 bash
 6918 pts/1    Ss     0:00 bash
 6936 ?        S      0:00 /usr/lib/gnome-panel/wnck-applet --oaf-activate-iid=O
 6938 ?        S      0:00 /usr/lib/gnome-panel/notification-area-applet --oaf-a
 6940 ?        S      0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-i
 6942 ?        S      0:00 /usr/lib/gnome-panel/clock-applet --oaf-activate-iid=
 7013 ?        Sl     0:14 /usr/lib/mozilla-firefox/firefox-bin -a firefox
 7125 pts/1    R+     0:00 ps ax





cat /var/log/messages:

Oct 14 11:41:41 localhost kernel: agpgart: Detected NVIDIA nForce2 chipset
Oct 14 11:41:41 localhost kernel: agpgart: Maximum main memory to use for agp memory: 176M
Oct 14 11:41:41 localhost kernel: agpgart: AGP aperture is 64M @ 0xf4000000
Oct 14 11:41:41 localhost kernel: i2c_adapter i2c-0: nForce2 SMBus adapter at 0xfc00
Oct 14 11:41:41 localhost kernel: i2c_adapter i2c-1: nForce2 SMBus adapter at 0xfc40
Oct 14 11:41:41 localhost kernel: ACPI: PCI interrupt 0000:00:06.0[A] -> GSI 22 (level, high) -> IRQ 22
Oct 14 11:41:41 localhost kernel: AC'97 0 analog subsections not ready
Oct 14 11:41:41 localhost kernel: intel8x0_measure_ac97_clock: measured 49597 usecs
Oct 14 11:41:41 localhost kernel: intel8x0: clocking to 47455
Oct 14 11:41:41 localhost kernel: cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
Oct 14 11:41:41 localhost kernel: pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Oct 14 11:41:41 localhost kernel: ACPI: PCI interrupt 0000:14:01.0[A] -> GSI 21 (level, high) -> IRQ 21
Oct 14 11:41:41 localhost kernel: 0000:14:01.0: 3Com PCI 3c920 Tornado at 0x1000. Vers LK1.1.19
Oct 14 11:41:41 localhost kernel: ACPI: PCI interrupt 0000:14:01.0[A] -> GSI 21 (level, high) -> IRQ 21
Oct 14 11:41:41 localhost kernel: NET: Registered protocol family 17
Oct 14 11:41:41 localhost kernel: NET: Registered protocol family 10
Oct 14 11:41:41 localhost kernel: Disabled Privacy Extensions on device c02f0500(lo)
Oct 14 11:41:41 localhost kernel: IPv6 over IPv4 tunneling driver
Oct 14 11:41:42 localhost kernel: lp0: using parport0 (interrupt-driven).
Oct 14 11:41:42 localhost kernel: ACPI: Power Button (FF) [PWRF]
Oct 14 11:41:43 localhost hal.hotplug[4280]: timout(10000 ms) waiting for /bus/pci/slots
Oct 14 11:41:44 localhost pci.agent[6049]: Bad PCI agent invocation
Oct 14 11:41:44 localhost kernel: apm: BIOS not found.
Oct 14 11:41:58 localhost gconfd (aaron-6701): starting (version 2.10.0), pid 6701 user 'aaron'
Oct 14 11:41:58 localhost gconfd (aaron-6701): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Oct 14 11:41:58 localhost gconfd (aaron-6701): Resolved address "xml:readwrite:/home/aaron/.gconf" to a writable configuration source at position 1
Oct 14 11:41:58 localhost gconfd (aaron-6701): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Oct 14 11:42:09 localhost gconfd (aaron-6701): Resolved address "xml:readwrite:/home/aaron/.gconf" to a writable configuration source at position 0
Oct 14 11:43:37 localhost kernel: SCSI error : <0 0 0 0> return code = 0x8000002
Oct 14 11:43:37 localhost kernel: Current sda: sense key Hardware Error
Oct 14 11:43:37 localhost kernel: Additional sense: Data phase error
Oct 14 11:43:37 localhost kernel: end_request: I/O error, dev sda, sector 11486383


cat /var/log/dmesg:


Freeing memory... done (538 pages freed)
Restarting tasks... done
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
Adding 730916k swap on /dev/sda5.  Priority:-1 extents:1
EXT3 FS on sda1, internal journal
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: dm-devel@redhat.com
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
Real Time Clock Driver v1.12
input: PC Speaker
input: ImPS/2 Logitech Wheel Mouse on isa0060/serio1
ts: Compaq touchscreen protocol output
mice: PS/2 mouse device common for all mice
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
inserting floppy driver for 2.6.10-5-386
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected NVIDIA nForce2 chipset
agpgart: Maximum main memory to use for agp memory: 176M
agpgart: AGP aperture is 64M @ 0xf4000000
i2c_adapter i2c-0: nForce2 SMBus adapter at 0xfc00
i2c_adapter i2c-1: nForce2 SMBus adapter at 0xfc40
ACPI: PCI Interrupt Link [LACI] enabled at IRQ 22
ACPI: PCI interrupt 0000:00:06.0[A] -> GSI 22 (level, high) -> IRQ 22
PCI: Setting latency timer of device 0000:00:06.0 to 64
AC'97 0 analog subsections not ready
intel8x0_measure_ac97_clock: measured 49597 usecs
intel8x0: clocking to 47455
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
ACPI: PCI Interrupt Link [LMC1] enabled at IRQ 21
ACPI: PCI interrupt 0000:14:01.0[A] -> GSI 21 (level, high) -> IRQ 21
3c59x: Donald Becker and others. www.scyld.com/network/vortex.html
0000:14:01.0: 3Com PCI 3c920 Tornado at 0x1000. Vers LK1.1.19
ACPI: PCI interrupt 0000:14:01.0[A] -> GSI 21 (level, high) -> IRQ 21
NET: Registered protocol family 17
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver



```

oh and I can boot from the ubuntu install cd fine.  I also just for the heck of it verified that the primary and secondary ide are enbabled in the BIOS.

help!!

Thanks

Aaron

---

### Post by 11hjpphty76lkjj on 2005-10-14
I tried this as well:


```
aaron@ubuntu:~$ sudo /etc/init.d/udev stop
Password:
 * Unmounting /dev...                                                                              [ ok ]
aaron@ubuntu:~$ mount /media/cdrom
mount: /dev/hdc is not a valid block device
aaron@ubuntu:~$ mount /dev/hdc
mount: /dev/hdc is not a valid block device

```

](*,)

---

### Post by 11hjpphty76lkjj on 2005-10-14
Well I think I got it working. I reinstalled and then  I added

ide-cd
ide-disk
ide-generic

to the /etc/mkinitrd/modules

and remade the boot img. 

It's working from terminal at least..

---

