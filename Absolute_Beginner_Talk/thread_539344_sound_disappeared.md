---
title: "sound disappeared"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by Arndt on 2007-08-31
I have previously been able to listen to CD's (using Sound Juicer) and web radio (using VLC). Yesterday I wanted to try out the sound messages from a game server client (cgoban for KGS, in case anyone is familiar with it). The sound messages for the client worked as they should, but when I turned its sound off again, Sound Juicer and VLC had stopped working. When I now press play in Sound Juicer for a CD, it seemingly starts playing, but there is no sound, and also it plays at a much higher rate than 1 second per second. As for VLC, it also has no sound, and when I press the stop button, it crashes. (Turning on the sound in the game client doesn't help.)

The beep sound in the editor Emacs still works. As far as I can see with alsamixer, no channel is muted.

Here's the output from a couple of diagnostic programs:
```

$ lspci | grep -i audio
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)


$ lsmod
Module                  Size  Used by
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
speedstep_lib           4228  0
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
i915                   17920  1
drm                    58004  2 i915
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
i2c_core               19728  1 i2c_acpi_ec
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
ipv6                  217408  12
nfs                   178120  1
lockd                  55848  2 nfs
sunrpc                125124  3 nfs,lockd
af_packet              20232  2
tsdev                   7616  0
floppy                 52692  0
rtc                    11832  0
pcspkr                  3652  0
snd_intel8x0           30144  3
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  1
snd_mixer_oss          16128  2 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  3 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
tpm_atmel               5504  0
tpm_nsc                 6528  0
tpm                     9504  2 tpm_atmel,tpm_nsc
pci_hotplug            24628  0
intel_agp              21276  1
agpgart                32328  3 drm,intel_agp
nls_iso8859_1           4224  2
nls_cp437               5888  2
vfat                   12288  2
fat                    46492  1 vfat
dm_mod                 50364  1
evdev                   9088  0
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  116232  5
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
usbhid                 30688  0
e1000                  89780  0
ehci_hcd               29448  0
uhci_hcd               28048  0
usbcore               104316  4 usbhid,ehci_hcd,uhci_hcd
ide_cd                 36996  0
cdrom                  33952  1 ide_cd
ide_disk               16128  9
ide_generic             1664  0
ata_piix                9476  0
libata                 47876  1 ata_piix
scsi_mod              124872  1 libata
piix                    9476  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,piix
unix                   24624  613
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

### Post by Arndt on 2007-08-31
I got help locally, so I have the sound working again. The problem seemed to be that the Java client I ran uses older sound software called OSS, and it ruined things for the more modern ALSA programs. So killing my game client fixed the problem. Maybe more modern Java runtime code than the one I have do use ALSA, I don't know.

He also said that to run OSS programs together with ALSA ones without problems, the OSS ones can be started via a program 'aoss', which emulates OSS.

---

