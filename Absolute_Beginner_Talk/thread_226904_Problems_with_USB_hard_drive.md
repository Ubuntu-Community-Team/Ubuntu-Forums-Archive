---
title: "Problems with USB hard drive"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by 404abc on 2006-07-31
I have an external USB hard drive.  It is formatted FAT32 and
I had no problems using it with the earlier version of Ubuntu,
but with the current version, it no longer works.  When I do
dmesg, I get the following error:


[17181369.792000] usb 4-3: new high speed USB device using ehci_hcd and address 6
[17181381.492000] usb 4-3: device not accepting address 6, error -110
[17181381.604000] usb 4-3: new high speed USB device using ehci_hcd and address 7
[17181393.304000] usb 4-3: device not accepting address 7, error -110
[17181393.416000] usb 4-3: new high speed USB device using ehci_hcd and address 8
[17181403.840000] usb 4-3: device not accepting address 8, error -110
[17181403.952000] usb 4-3: new high speed USB device using ehci_hcd and address 9
[17181414.376000] usb 4-3: device not accepting address 9, error -110


Could somebody clue me in on what I'm doing wrong?

This is the output of "mount":


$ mount
/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-26-386/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)


This is my /etc/fstab:


$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


This is what I get when I do "lsmod":


$ lsmod
Module                  Size  Used by
hostap_cs              64536  0
hostap                119428  1 hostap_cs
ieee80211_crypt         6272  1 hostap
orinoco_cs             17928  1
orinoco                43156  1 orinoco_cs
hermes                  7808  2 orinoco_cs,orinoco
binfmt_misc            12296  1
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ipv6                  265728  8
ppdev                   9220  0
via                    47968  1
drm                    73236  2 via
powernow_k7             8744  0
cpufreq_userspace       4696  1
cpufreq_stats           5636  0
freq_table              4740  2 powernow_k7,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
dm_mod                 58936  1
md_mod                 72532  0
parport_pc             35780  0
lp                     11844  0
parport                36296  3 ppdev,parport_pc,lp
af_packet              22920  4
joydev                 10048  0
tsdev                   8000  0
snd_seq_dummy           3844  0
snd_seq_oss            33536  0
snd_seq_midi            9376  0
snd_seq_midi_event      7552  2 snd_seq_oss,snd_seq_midi
snd_seq                51984  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcmcia                 40508  2 hostap_cs,orinoco_cs
pcspkr                  2180  0
rtc                    13492  0
snd_via82xx_modem      15368  1
snd_via82xx            28824  2
gameport               15496  1 snd_via82xx
snd_ac97_codec         93088  2 snd_via82xx_modem,snd_via82xx
snd_ac97_bus            2304  1 snd_ac97_codec
i2c_viapro              8980  0
snd_pcm_oss            53664  0
snd_mixer_oss          18688  3 snd_pcm_oss
i2c_core               21904  2 i2c_acpi_ec,i2c_viapro
via_rhine              23940  0
mii                     5888  1 via_rhine
via_ircc               26900  0
snd_pcm                89864  4 snd_via82xx_modem,snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  2 snd_seq,snd_pcm
snd_page_alloc         10632  3 snd_via82xx_modem,snd_via82xx,snd_pcm
snd_mpu401_uart         7808  1 snd_via82xx
snd_rawmidi            25504  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          8716  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    55268  14 snd_seq_oss,snd_seq,snd_via82xx_modem,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10208  3 snd
psmouse                36100  0
shpchp                 45632  0
serio_raw               7300  0
pci_hotplug            29236  1 shpchp
irda                  187068  1 via_ircc
crc_ccitt               2304  1 irda
yenta_socket           28428  3
rsrc_nonstatic         13440  1 yenta_socket
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
via_agp                 9856  1
agpgart                34888  2 drm,via_agp
evdev                   9856  1
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
ehci_hcd               34184  0
uhci_hcd               33680  0
usbcore               130692  3 ehci_hcd,uhci_hcd
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
ide_disk               17664  3
via82cxxx               9988  0 [permanent]
generic                 5124  0
thermal                13576  0
processor              23360  2 powernow_k7,thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

---

### Post by 404abc on 2006-07-31
The problem went away when I did: sudo modprobe -r ehci_hcd

---

