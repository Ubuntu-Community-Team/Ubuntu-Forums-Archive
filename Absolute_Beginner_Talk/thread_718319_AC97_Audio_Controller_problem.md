---
title: "AC97 Audio Controller problem"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by Wolfan on 2008-03-08
Hello,

I'm having problem with my sound, and after searching for a while it would seem as though I'm not the only one having the problem, but the solution doesn't seem to be posted anywhere so I'm hoping that it's not the case that there is no solution. 

So I just learned that there is a command lspci which I ran and my audio entry says 
> 00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 

Now, the strange thing is that I've had Ubuntu installed for about three days.  The second day I went into alsamixer and unmuted everything and was able to get some sound working.  Then I upgraded from 6.10 to 7.04 and then my sound stopped working, so I went back to alsamixer and unmuted everything again, and still no sound.  I also checked a file (I can't remember it's name right now this was a few solutions ago) which had groups with users assigned to them, and according to that post I was supposed to add my self to the sound group, but I was already there.  So I'm hoping someone can help, or at least tell me that there is no solution yet.

Thanks for reading

---

### Post by Whiffle on 2008-03-08
could you post the output of "lsmod" ?   I have an ICH6 controller that works perfectly...

---

### Post by Wolfan on 2008-03-08
Sure, thanks very much for replying. Here is the output of lsmod
> 
Module                  Size  Used by
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14208  1 
fat                    53916  1 vfat
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
radeon                124576  2 
drm                    81044  3 radeon
speedstep_lib           6148  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7360  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9228  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8200  0 
tc1100_wmi              8068  0 
pcc_acpi               13184  0 
dev_acpi               12292  0 
sony_acpi               6284  0 
video                  16388  0 
sbs                    15652  0 
i2c_ec                  6016  1 sbs
i2c_core               22656  1 i2c_ec
dock                   10268  0 
button                  8720  0 
battery                10756  0 
container               5248  0 
ac                      6020  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
ipv6                  269088  10 
sbp2                   23812  0 
lp                     12452  0 
joydev                 10816  0 
pcmcia                 39212  0 
snd_intel8x0           34332  1 
snd_ac97_codec         98464  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
bcm43xx               126824  0 
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ieee80211softmac       31360  1 bcm43xx
ieee80211              34760  2 bcm43xx,ieee80211softmac
ieee80211_crypt         7040  1 ieee80211
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
psmouse                38920  0 
snd                    54020  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               7940  0 
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
pcspkr                  4224  0 
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
intel_agp              26140  1 
agpgart                35400  2 drm,intel_agp
af_packet              23816  4 
evdev                  11008  5 
tsdev                   8768  0 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sd_mod                 23428  5 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
usb_storage            72256  1 
usbhid                 26592  0 
hid                    27392  1 usbhid
ata_piix               15492  2 
libusual               17936  1 usb_storage
ata_generic             9092  0 
libata                125720  2 ata_piix,ata_generic
scsi_mod              142348  6 sbp2,sg,sd_mod,sr_mod,usb_storage,libata
ohci1394               36528  0 
floppy                 59524  0 
ieee1394              299448  2 sbp2,ohci1394
e1000                 126016  0 
uhci_hcd               25360  0 
generic                 5124  0 [permanent]
ehci_hcd               34188  0 
usbcore               134280  6 usb_storage,usbhid,libusual,uhci_hcd,ehci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

---

### Post by Wolfan on 2008-03-14
bump in the hopes on getting an answer

---

