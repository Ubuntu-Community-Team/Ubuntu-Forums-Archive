---
title: "[SOLVED] No Audio: HP dv2550se"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by imaginal on 2008-01-03
From what reading and searching I've done, it is Intel HD ICH8... but I'm really new to linux and don't understand how to troubleshoot my audio problems. Ubuntu 7.1

---

### Post by xeth_delta on 2008-01-03
> **imaginal said:**
> From what reading and searching I've done, it is Intel HD ICH8... but I'm really new to linux and don't understand how to troubleshoot my audio problems. Ubuntu 7.1

Please post the output of
```
lscpi | grep -i audio
```

You type this in a terminal to find out what card you exactly have.

The following resources might be useful:

[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

Let us know if you need more help.

Xeth

---

### Post by imaginal on 2008-01-03
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

aplay -l yields:**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by xeth_delta on 2008-01-03
> **imaginal said:**
> 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

aplay -l yields:**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Indeed you have an intel audio card, you should be using the alsa hda-intel drivers. My suggestion would be to download the alsa drivers source code, compile and install. You will see It is not very difficult. Have a look at the link I gave you. If you want more up to date drivers I guess you could get them from [www.alsa-project.org](www.alsa-project.org).

Just ask if you need any help with that.

---

### Post by imaginal on 2008-01-03
So, I think what ultimately fixed my issue was here [http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

My problem? I worked on this for 6 hours or so, doing multiple things and leaving the room when I was frustrated, then coming back to work on it again... but failing to restart my computer. :P After a restart, I heard noise.

---

### Post by imaginal on 2008-01-06
Well, it worked for about a day... now, without explanation, there is no sound. I compiled alsa 1.0.15 the best of my ability, but there is nothing. What is the troubleshooting process at this point?

---

### Post by xeth_delta on 2008-01-06
> **imaginal said:**
> Well, it worked for about a day... now, without explanation, there is no sound. I compiled alsa 1.0.15 the best of my ability, but there is nothing. What is the troubleshooting process at this point?

Can you check whether you have something called **/etc/init.d/alsasound** or **/etc/init.d/alsa**? If you do, call
```
sudo /etc/init.d/alsasound restart
```
then check the output of "dmesg". Post the last output lines, the ones concerning the sound system.

Xeth

---

### Post by imaginal on 2008-01-06
sudo /etc/init.d/alsasound restart gave me "Shutting down sound driver: !!!alsactl not found!!! done" My guess is that this is because of a poor second shot at installing/compiling alsa.

dmesg gave me too much to post... anything in particular? This feels like a 2-part problem. 1: repair ALSA. 2: Get it to work... 

I just don't know what my next step should be. Thanks in advance!

[edit] I re-read post... dmesg didn't give me anything I could see as relating to sound, but here are the last 20 lines or so.
[   19.916000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   19.920000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   21.024000] Failure registering capabilities with primary security module.
[   21.240000] ppdev: user-space parallel port driver
[   21.372000] audit(1199665977.635:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5300 profile="/usr/sbin/cupsd"
[   21.464000] apm: BIOS not found.
[   21.612000] sky2 eth0: enabling interface
[   21.984000] Bluetooth: Core ver 2.11
[   21.984000] NET: Registered protocol family 31
[   21.984000] Bluetooth: HCI device and connection manager initialized
[   21.984000] Bluetooth: HCI socket layer initialized
[   21.992000] Bluetooth: L2CAP ver 2.8
[   21.992000] Bluetooth: L2CAP socket layer initialized
[   22.060000] Bluetooth: RFCOMM socket layer initialized
[   22.064000] Bluetooth: RFCOMM TTY layer initialized
[   22.064000] Bluetooth: RFCOMM ver 1.8
[   27.036000] [drm] Initialized drm 1.1.0 20060810
[   27.040000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   27.040000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   56.956000] NET: Registered protocol family 17
[   60.128000] ieee80211_crypt: registered algorithm 'WEP'
[   62.704000] NET: Registered protocol family 10
[   62.704000] lo: Disabled Privacy Extensions
[   62.704000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   77.604000] eth1: no IPv6 routers present
[10058.104000] ACPI: PCI interrupt for device 0000:00:1b.0 disabled

---

### Post by xeth_delta on 2008-01-06
> **imaginal said:**
> sudo /etc/init.d/alsasound restart gave me "Shutting down sound driver: !!!alsactl not found!!! done" My guess is that this is because of a poor second shot at installing/compiling alsa.

dmesg gave me too much to post... anything in particular? This feels like a 2-part problem. 1: repair ALSA. 2: Get it to work... 

I just don't know what my next step should be. Thanks in advance!

[edit] I re-read post... dmesg didn't give me anything I could see as relating to sound, but here are the last 20 lines or so.
[   19.916000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   19.920000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   21.024000] Failure registering capabilities with primary security module.
[   21.240000] ppdev: user-space parallel port driver
[   21.372000] audit(1199665977.635:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5300 profile="/usr/sbin/cupsd"
[   21.464000] apm: BIOS not found.
[   21.612000] sky2 eth0: enabling interface
[   21.984000] Bluetooth: Core ver 2.11
[   21.984000] NET: Registered protocol family 31
[   21.984000] Bluetooth: HCI device and connection manager initialized
[   21.984000] Bluetooth: HCI socket layer initialized
[   21.992000] Bluetooth: L2CAP ver 2.8
[   21.992000] Bluetooth: L2CAP socket layer initialized
[   22.060000] Bluetooth: RFCOMM socket layer initialized
[   22.064000] Bluetooth: RFCOMM TTY layer initialized
[   22.064000] Bluetooth: RFCOMM ver 1.8
[   27.036000] [drm] Initialized drm 1.1.0 20060810
[   27.040000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   27.040000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   56.956000] NET: Registered protocol family 17
[   60.128000] ieee80211_crypt: registered algorithm 'WEP'
[   62.704000] NET: Registered protocol family 10
[   62.704000] lo: Disabled Privacy Extensions
[   62.704000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   77.604000] eth1: no IPv6 routers present
[10058.104000] ACPI: PCI interrupt for device 0000:00:1b.0 disabled

Did you run dmesg immediately after restarting alsa?

Here you have a great guide on solving alsa problems: [http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

Concerning the alsactl error, can you find it?
```
whereis alsactl
```
or
```
locate alsactl
```
or you can search for it in /bin, /usr/bin or /sbin? Example:
```
find /bin/* | grep -i alsactl
```

---

### Post by magicman5421 on 2008-01-06
Are you sure that ALSA didn't just get muted?
Type
```

alsamixer

```
in the terminal and make sure none of the channels are muted.

---

### Post by imaginal on 2008-01-06
dmesg was run immediately afterwards... and I can find alsactl using the metioned methods. I've read through the comprehesive guide, and tried the "Getting the ALSA drivers from a *fresh* kernel" portion. Alsamixer will no longer open... alsamixer: function snd_ctl_open failed for default: No such device

---

### Post by imaginal on 2008-01-06
> **magicman5421 said:**
> Are you sure that ALSA didn't just get muted?
Type
```

alsamixer

```
in the terminal and make sure none of the channels are muted.

That was not the problem when alsamixer was working. My problem has evolved... :-/

---

### Post by xeth_delta on 2008-01-06
> **imaginal said:**
> dmesg was run immediately afterwards... and I can find alsactl using the metioned methods. I've read through the comprehesive guide, and tried the "Getting the ALSA drivers from a *fresh* kernel" portion. Alsamixer will no longer open... alsamixer: function snd_ctl_open failed for default: No such device

That sounds like the modules (drivers) are not loaded. Restart alsasound. Post the output of "lsmod" between code tags.

---

### Post by imaginal on 2008-01-06
How would I restart alsasound? My best guess
```
sudo /etc/init.d/alsasound start
```
This doesn't appear to do anything
```
lsmod
Module                  Size  Used by
ipv6                  273892  10 
arc4                    2944  2 
ecb                     4608  2 
blkcipher               7556  1 ecb
ieee80211_crypt_wep     6272  1 
af_packet              24840  4 
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14080  1 
fat                    54300  1 vfat
i915                   25856  2 
drm                    83348  3 i915
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
acpi_cpufreq           10568  1 
cpufreq_conservative     8072  0 
cpufreq_stats           7232  0 
cpufreq_userspace       5280  0 
cpufreq_ondemand        9612  1 
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 
video                  18060  0 
battery                11012  0 
ac                      6148  0 
button                  8976  0 
dock                   10656  0 
sbs                    19592  0 
container               5504  0 
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
snd_page_alloc         11400  0 
xpad                    9988  0 
uvcvideo               48644  0 
compat_ioctl32          2304  1 uvcvideo
joydev                 11328  0 
videodev               29312  1 uvcvideo
v4l1_compat            15364  2 uvcvideo,videodev
v4l2_common            18432  2 uvcvideo,videodev
ipw3945               119840  1 
sky2                   46852  0 
ieee80211              35656  1 ipw3945
sdhci                  18828  0 
ieee80211_crypt         7040  2 ieee80211_crypt_wep,ieee80211
serio_raw               8068  0 
mmc_core               28420  1 sdhci
intel_agp              25620  1 
agpgart                35016  3 drm,intel_agp
psmouse                39952  0 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
evdev                  11136  5 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
usb_storage            73024  1 
ide_core              116804  1 usb_storage
usbhid                 29536  0 
hid                    28928  1 usbhid
libusual               18448  1 usb_storage
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
ata_piix               17540  0 
sd_mod                 30336  5 
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
ata_generic             8452  0 
ahci                   23300  2 
libata                125168  3 ata_piix,ata_generic,ahci
scsi_mod              147084  6 sbp2,sg,usb_storage,sr_mod,sd_mod,libata
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  8 xpad,uvcvideo,usb_storage,usbhid,libusual,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

```

---

### Post by xeth_delta on 2008-01-07
Almost, to restart alsa use restart, that will first stop it, the start it up again.

From your lsmod output, I can see that the modules are, as suspected, not loaded. Try to load them manually, post the eventual errors:

```
sudo modprobe snd-hda-intel
sudo modprobe snd-pcm-oss
sudo modprobe snd-mixer-oss
sudo modprobe snd-seq-oss
```

If after this, sound is still not present, I would suggest following again the steps that gave you good results. Did you perchance install an update recently? If you are using a custom alsa installation (as you were), you need to recompile and reinstall the drivers after a kernel change/update.

I would also suggest having a look at this general alsa page: [http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel]("http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel")

---

### Post by imaginal on 2008-01-07
All posted code went without error, but no sound. I started to recompile, but had problems during utils. (lack of curses library). I'm going to restart my computer, take a deep breath, and reformat. Hopefully it will go back to a state I can work with, but right now I'm over my head.

The original problem still remains, but I need to return to a state that I can work with.

---

### Post by xeth_delta on 2008-01-07
To compile utils, you need to install the following packages:
```
sudo aptitude install libncurses5 libncurses5-dev
```

I don't think you need to reinstall, but it is up to you :)

check if the modules wre loaded with lsmod.
In any case, let us know about your progress.

Xeth

---

### Post by imaginal on 2008-01-07
Curiouser and curiouser...

On my quest to get sound working again, I deleted my installation and booted from the live CD. There was no sound. I restarted and booted again from the live cd. This time, there was sound. After the installation, sound. After system updates, sound. However, I'm still holding my breath.

I also found this [http://ubuntuforums.org/showthread.php?t=507407]("http://ubuntuforums.org/showthread.php?t=507407")
 which is my exact model... also showing erratic sound performance.

> **crex said:**
> Yes i did install all codecs. The laptop stopped producing sound. When first starting up ubuntu it use to have audio but now no audio works. I have to go to work but I'll look around for a fix later. 

Thanks,
Rey 

It is just very strange. I'll post more, depending. :???:

---

### Post by imaginal on 2008-01-07
I've been able to isolate and repeat the strange behavior. :D

I have a dual-boot system, Gusty and Vista. If I boot into Vista, then restart into Ubuntu, I don't have sound. If I shut the computer down, then start Ubuntu, I have sound again. There are no errors, either way. My guess is BIOS related, but I don't know for sure. 

Solution for now: Turn off your laptop. Turn on your laptop.

---

