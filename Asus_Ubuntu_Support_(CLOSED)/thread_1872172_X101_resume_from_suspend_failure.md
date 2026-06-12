---
title: "X101 resume from suspend failure"
date: 2011-10-30
forum: Asus Ubuntu Support (CLOSED)
---

### Post by G1sbert on 2011-10-30
Hi Folks,

i have this problem since i bought my eee pc X101. Always when i suspend my netbook everything works fine, but when i try to resume it wakes up like after a normal shutdown. Ive already tried the uswsup tools but also here the same problem :(

In the log file from var/log/pm-suspend.log it seems that the suspend hook is running fine, but after this there is never the resume hook in the log.

> Initial commandline parameters: 
Sun Oct 23 11:57:36 CEST 2011: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux Netbook 2.6.35.10-1-jolicloud-atom #64 SMP Fri Mar 4 04:39:01 MST 2011 i686 GNU/Linux
Module                  Size  Used by
joydev                  7469  0 
snd_hda_codec_realtek   197416  1 
snd_hda_intel          18859  2 
ath9k                  60408  0 
snd_hda_codec          71028  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               4496  1 snd_hda_codec
snd_pcm_oss            28725  0 
ath9k_common            5094  1 ath9k
snd_mixer_oss          10783  1 snd_pcm_oss
eeepc_wmi               2663  0 
snd_pcm                58904  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
sparse_keymap           2753  1 eeepc_wmi
uvcvideo               46443  0 
psmouse                52052  0 
ath9k_hw              266301  2 ath9k,ath9k_common
snd_timer              15323  1 snd_pcm
lp                      6452  0 
snd_page_alloc          6328  2 snd_hda_intel,snd_pcm
parport                27135  1 lp
fbcon                  29091  71 
tileblit                1687  1 fbcon
font                    7461  1 fbcon
bitblit                 3527  1 fbcon
softcursor              1001  1 bitblit
i915                  241970  3 
drm_kms_helper         24176  1 i915
drm                   146763  3 i915,drm_kms_helper
intel_agp              21761  2 i915
i2c_algo_bit            4214  1 i915
agpgart                27601  2 drm,intel_agp
video                  18579  1 i915
output                  1671  1 video
             total       used       free     shared    buffers     cached
Mem:       1016468     886404     130064          0      19860     511180
-/+ buffers/cache:     355364     661104
Swap:      1520636          0    1520636
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend:success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/95packagekit suspend suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
Sun Oct 23 11:57:37 CEST 2011: performing suspend
Initial commandline parameters: 
Sun Oct 23 12:39:20 CEST 2011: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux Netbook 2.6.35.10-1-jolicloud-atom #64 SMP Fri Mar 4 04:39:01 MST 2011 i686 GNU/Linux
Module                  Size  Used by
joydev                  7469  0 
snd_hda_codec_realtek   197416  1 
ath9k                  60408  0 
snd_hda_intel          18859  2 
snd_hda_codec          71028  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               4496  1 snd_hda_codec
snd_pcm_oss            28725  0 
ath9k_common            5094  1 ath9k
eeepc_wmi               2663  0 
snd_mixer_oss          10783  1 snd_pcm_oss
sparse_keymap           2753  1 eeepc_wmi
psmouse                52052  0 
snd_pcm                58904  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
uvcvideo               46443  0 
ath9k_hw              266301  2 ath9k,ath9k_common
lp                      6452  0 
snd_timer              15323  1 snd_pcm
snd_page_alloc          6328  2 snd_hda_intel,snd_pcm
parport                27135  1 lp
fbcon                  29091  71 
tileblit                1687  1 fbcon
font                    7461  1 fbcon
bitblit                 3527  1 fbcon
softcursor              1001  1 bitblit
i915                  241970  3 
drm_kms_helper         24176  1 i915
drm                   146763  3 i915,drm_kms_helper
intel_agp              21761  2 i915
i2c_algo_bit            4214  1 i915
agpgart                27601  2 drm,intel_agp
video                  18579  1 i915
output                  1671  1 video
             total       used       free     shared    buffers     cached
Mem:       1016468     884576     131892          0      32848     485648
-/+ buffers/cache:     366080     650388
Swap:      1520636          0    1520636
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend:success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/95packagekit suspend suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
Sun Oct 23 12:39:21 CEST 2011: performing suspend
Initial commandline parameters: 
Sun Oct 23 14:40:57 CEST 2011: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.

Im currently running JoliOs 1.2 based on Ubuntu 10.04 but i also have the same problem with all other ubuntu versions.

Anyone able to help me?

greets
G1sbert

---

### Post by Toz on 2011-10-30
I believe the problem is that when you are trying to resume, the storage card isn't powered up and the root filesystem can't be found, so it restarts. One potential solution would be to retain power for the usb port that holds the card through the suspend cycle. Have a look at: [http://www.mjmwired.net/kernel/Documentation/usb/persist.txt]("http://www.mjmwired.net/kernel/Documentation/usb/persist.txt") for some information about usb persistence (including some warnings).

This link from the Arch wiki ([https://wiki.archlinux.org/index.php/Asus_Eee_PC_701#Sleeping_and_waking_system_on_a_card]("https://wiki.archlinux.org/index.php/Asus_Eee_PC_701#Sleeping_and_waking_system_on_a_card")) details a procedure where this can be done. It involves echoing the value of 1 to the cards power/persist setting. The only issue here is determining which usb port the card is plugged into. Since I don't have one of these devices, I'm flying blind. 

What does the following command return:
```
lsusb
```

Also, what are the contents of your **/var/log/dmesg** file?

EDIT: A link for adding persist info at startup ([http://www.gentoo-wiki.info/Asus_EEE_PC_901#local.start]("http://www.gentoo-wiki.info/Asus_EEE_PC_901#local.start")):

---

### Post by G1sbert on 2011-10-30
The output for lsusb:

```
lschristoph@Netbook:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 13d3:5711 IMC Networks 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
christoph@Netbook:~$ 

```

I also attached the dmesg log file.

Thanks for your help.

G1sbert

---

### Post by Toz on 2011-10-30
I'm not seeing it. Can you post back the contents of:
```
sudo lspci -vnn
```
```
lsmod
```
```
cat /etc/fstab
```
```
mount
```
```
ls /sys/bus/usb/devices
```
```
ls /sys/bus/mmc/devices
```

---

### Post by G1sbert on 2011-10-31
Hi,

here is the output of my system:

```
root@Netbook:~# sudo lspci -vnn
00:00.0 Host bridge [0600]: Intel Corporation N10 Family DMI Bridge [8086:a010]
	Subsystem: ASUSTeK Computer Inc. Device [1043:83ac]
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011]
	Subsystem: ASUSTeK Computer Inc. Device [1043:83ac]
	Flags: bus master, fast devsel, latency 0, IRQ 42
	Memory at f7f00000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at ec00 [size=8]
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Memory at f7e00000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [d0] Power Management version 2
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller [0380]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a012]
	Subsystem: ASUSTeK Computer Inc. Device [1043:83ac]
	Flags: bus master, fast devsel, latency 0
	Memory at f7f80000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: [d0] Power Management version 2

00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device [1043:84d3]
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at f7df8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: 3f700000-3f8fffff
	Prefetchable memory behind bridge: 000000003f900000-000000003fafffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device [1043:83ad]
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=02, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: f8000000-fbffffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f6ffffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device [1043:83ad]
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device [1043:83ad]
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at e400 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device [1043:83ad]
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at e480 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device [1043:83ad]
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at e800 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device [1043:83ad]
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at e880 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02) (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device [1043:83ad]
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f7df7c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
	Capabilities: [50] Subsystem: ASUSTeK Computer Inc. Device [1043:83ad]

00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device [1043:83ad]
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>

00:1f.2 IDE interface [0101]: Intel Corporation N10/ICH7 Family SATA IDE Controller [8086:27c0] (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: ASUSTeK Computer Inc. Device [1043:83ad]
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 21
	I/O ports at e080 [size=8]
	I/O ports at e000 [size=4]
	I/O ports at dc00 [size=8]
	I/O ports at d880 [size=4]
	I/O ports at d800 [size=16]
	Memory at f7df7800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [70] Power Management version 2
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device [1043:83ad]
	Flags: medium devsel, IRQ 4
	I/O ports at 0400 [size=32]
	Kernel modules: i2c-i801

01:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: Device [1a3b:1089]
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fbff0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [60] Express Legacy Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 12-14-24-ff-ff-17-15-00
	Capabilities: [170] Power Budgeting <?>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

root@Netbook:~# lsmod
Module                  Size  Used by
joydev                  7469  0 
snd_hda_codec_realtek   197416  1 
snd_hda_intel          18859  2 
snd_hda_codec          71028  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               4496  1 snd_hda_codec
ath9k                  60408  0 
snd_pcm_oss            28725  0 
snd_mixer_oss          10783  1 snd_pcm_oss
eeepc_wmi               2663  0 
snd_pcm                58904  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
ath9k_common            5094  1 ath9k
sparse_keymap           2753  1 eeepc_wmi
lp                      6452  0 
uvcvideo               46443  0 
psmouse                52052  0 
ath9k_hw              266301  2 ath9k,ath9k_common
snd_timer              15323  1 snd_pcm
snd_page_alloc          6328  2 snd_hda_intel,snd_pcm
parport                27135  1 lp
fbcon                  29091  71 
tileblit                1687  1 fbcon
font                    7461  1 fbcon
bitblit                 3527  1 fbcon
softcursor              1001  1 bitblit
i915                  241970  3 
drm_kms_helper         24176  1 i915
drm                   146763  3 i915,drm_kms_helper
i2c_algo_bit            4214  1 i915
intel_agp              21761  2 i915
ata_piix               18770  2 
video                  18579  1 i915
ide_pci_generic         2306  0 
output                  1671  1 video
agpgart                27601  2 drm,intel_agp
root@Netbook:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=79f6b008-cafa-4d39-bfe4-f1f63027b6bd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=86d89425-bfb2-4118-a663-1530af7b208f none            swap    sw              0       0
root@Netbook:~# mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
gvfs-fuse-daemon on /home/christoph/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=christoph)
root@Netbook:~# ls /sys/bus/usb/devices
1-0:1.0  1-6  1-6:1.0  1-6:1.1  2-0:1.0  3-0:1.0  4-0:1.0  5-0:1.0  usb1  usb2  usb3  usb4  usb5
root@Netbook:~# ls /sys/bus/mmc/devices
root@Netbook:~# 

```

Thanks for your help mate!

---

### Post by Toz on 2011-10-31
I'm sorry but I'm not just seeing the active usb port. Perhaps the X101 is significantly different from the 901.

Can you try booting temporarily with the **acpi_sleep=nonvs** kernel paramter to see if that helps? (Reference link: [https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot]("https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot"))

---

### Post by G1sbert on 2011-11-06
I just tried to change to acpi_sleep=nonvs but nothing changed - still the same problem :(
Have you got another idea how to solve this problem

Thanks G1sbert

---

### Post by Toz on 2011-11-06
A couple of more suggestions:

1. Try with the **mmc_core.removable=0** kernel parameter. Reference link: [https://bbs.archlinux.org/viewtopic.php?id=91807]("https://bbs.archlinux.org/viewtopic.php?id=91807").

2. If that doesn't work, does the following return anything?
```
ls /dev/mmcblk?p*
```

---

