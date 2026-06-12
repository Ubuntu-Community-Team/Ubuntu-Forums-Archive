---
title: "sound quality"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by sauravbhaumik on 2007-03-06
I am using Ubuntu Edgy 6.10. My sound card is Intel AC'97.  I am using
Volume Applet 2.16.1.

The problems are:

1. With PCM 100% :  I get the sound with master volume 70% as loud as
I get it in Windows with master volume 8%

2. mov files are showing very very bad sound quality.

3. MP3's are not as sweet as they are in Windows.

I give you the output of lsmod command:
```

Module                  Size  Used by
usblp                  15488  0
binfmt_misc            13448  1
rfcomm                 42260  0
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
i915                   21632  2
drm                    74644  3 i915
speedstep_lib           5764  0
cpufreq_userspace       5408  0
cpufreq_stats           7744  0
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0
cpufreq_ondemand        8876  0
cpufreq_conservative     8712  0
video                  17540  0
tc1100_wmi              8324  0
sony_acpi               6412  0
sbs                    16804  0
pcc_acpi               14080  0
i2c_ec                  6272  1 sbs
hotkey                 11556  0
dev_acpi               12292  0
container               5632  0
button                  7952  0
battery                11652  0
asus_acpi              17688  0
ac                      6788  0
ieee80211              35272  0
ieee80211_crypt         7552  1 ieee80211
af_packet              24584  0
nls_iso8859_1           5248  2
nls_cp437               6912  2
vfat                   14720  2
fat                    56348  1 vfat
lp                     12964  0
tsdev                   9152  0
8139cp                 24832  0
8139too                29056  0
mii                     6912  2 8139cp,8139too
snd_intel8x0           36252  1
snd_ac97_codec        106404  1 snd_intel8x0
psmouse                41352  0
evdev                  11392  1
ac97_bus                3456  1 snd_ac97_codec
serio_raw               8452  0
hw_random               7320  0
shpchp                 42144  0
pci_hotplug            32828  1 shpchp
snd_pcm_oss            47616  0
snd_mixer_oss          19584  1 snd_pcm_oss
parport_pc             37796  1
parport                39496  2 lp,parport_pc
snd_pcm                85764  3
snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
floppy                 63044  0
snd                    62856  8
snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
pcspkr                  4352  0
snd_page_alloc         11656  2 snd_intel8x0,snd_pcm
i2c_i810                6276  0
intel_agp              26012  1
agpgart                34888  3 drm,intel_agp
i2c_algo_bit           10376  1 i2c_i810
i2c_core               23424  2 i2c_ec,i2c_algo_bit
ext3                  142728  1
jbd                    62228  1 ext3
ehci_hcd               34696  0
uhci_hcd               24968  0
usbcore               134912  4 usblp,ehci_hcd,uhci_hcd
ide_generic             2432  0
ide_cd                 33696  0
cdrom                  38944  1 ide_cd
ide_disk               18560  5
piix                   11780  1
generic                 5764  0
thermal                15624  0
processor              31560  1 thermal
fan                     6020  0
fbcon                  41504  0
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0
capability              5896  0
commoncap               8704  1 capability
```

I tried alsamixer, no help.
What can be done?
Thanks

---

