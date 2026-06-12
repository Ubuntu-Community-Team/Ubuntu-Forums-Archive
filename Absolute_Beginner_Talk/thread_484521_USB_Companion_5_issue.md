---
title: "USB Companion 5 issue"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by Fico23 on 2007-06-25
I've had Ubuntu Feisty Fawn, the latest one. There's a weird issue going on with the sound. I own a Bose Companion 5 speaker set which works perfectly fine with Windows XP and when I mp3s and play CDs on my PC on Ubuntu. But for some reason, any system sound won't work, no site plays sounds, I have tried testing the speakers and work. It doesn't seem to make any sounds, the volume is at max, the system volume is set on max, and the drivers that should be in there, such as the GStreamer drivers, are in fact there. But no sound yet; these are connected to USB, so am I missing some important drivers for Ubuntu to run speakers plugged in USB.

---

### Post by DBStevens on 2007-06-26
"no site plays sounds"

Ar you saying that when you visit a web site that you know makes noises you can't hear any or are you saying    that you have no sound at all on your system?

If it is web sites you are talking about, it sounds like you need third party plugins or helper programs.

What is your sound card?

---

### Post by Fico23 on 2007-06-27
No system sound. Except when you play CDs and I run MP3 files saved from my other hard drive. My sound device is built-in audio from my Giga-byte GA-7N400-L. But the speakers are connected and selected to USB, and when I got to Sound Options, I chose the speakers and tested them, they produced sound. I just doesn't work when I'm in Web sites or when using Ubuntu apps that use sound.

---

### Post by DBStevens on 2007-06-27
Would you please run:

lsmod 

and post the output here.

---

### Post by Fico23 on 2007-06-28
Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7360  0 
cpufreq_conservative     8200  0 
cpufreq_userspace       5408  0 
cpufreq_ondemand        9228  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
dev_acpi               12292  0 
tc1100_wmi              8068  0 
pcc_acpi               13184  0 
sony_acpi               6284  0 
container               5248  0 
sbs                    15652  0 
video                  16388  0 
button                  8720  0 
dock                   10268  0 
ac                      6020  0 
i2c_ec                  6016  1 sbs
battery                10756  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
ipv6                  268960  8 
lp                     12452  0 
fuse                   46612  0 
joydev                 10816  0 
snd_intel8x0           34332  0 
snd_ac97_codec         98464  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
bcm43xx               126824  0 
ieee80211softmac       31360  1 bcm43xx
snd_seq_midi            9600  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
ieee80211              34760  2 bcm43xx,ieee80211softmac
ieee80211_crypt         7040  1 ieee80211
nvidia               6837140  32 
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
analog                 12832  0 
wacom                  17024  0 
snd_usb_audio          79744  0 
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  4 snd_intel8x0,snd_ac97_codec,snd_usb_audio,snd_pcm_oss
snd_timer              23684  2 snd_seq,snd_pcm
snd_usb_lib            17280  1 snd_usb_audio
snd_rawmidi            25472  2 snd_seq_midi,snd_usb_lib
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd_hwdep               9988  1 snd_usb_audio
xpad                    9988  0 
gameport               16520  1 analog
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
serio_raw               7940  0 
pcspkr                  4224  0 
snd                    54020  12 snd_intel8x0,snd_ac97_codec,snd_seq_oss,snd_seq,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_rawmidi,snd_seq_device,snd_hwdep
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
nvidia_agp              9500  1 
psmouse                38920  0 
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
i2c_nforce2             6784  0 
i2c_core               22656  3 i2c_ec,nvidia,i2c_nforce2
agpgart                35400  2 nvidia,nvidia_agp
af_packet              23816  4 
tsdev                   8768  0 
evdev                  11008  4 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
ide_disk               17024  3 
8139too                27648  0 
sata_nv                20868  0 
ata_generic             9092  0 
libata                125720  2 sata_nv,ata_generic
scsi_mod              142348  1 libata
generic                 5124  0 [permanent]
usbhid                 26592  0 
hid                    27392  1 usbhid
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp
amd74xx                15260  0 [permanent]
ehci_hcd               34188  0 
ohci_hcd               22532  0 
usbcore               134280  8 wacom,snd_usb_audio,snd_usb_lib,xpad,usbhid,ehci_hcd,ohci_hcd
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
federico@federico-desktop:~$ usbcore

---

### Post by mang on 2007-07-01
I'm having the same problem. It's kinda odd. If anyone figures this out before I do please post the answer here.

---

### Post by ljoslin on 2007-09-22
I have sort of solved the problem I will post what I have figured out, and then hopefully someone can push it further and fix my next issues!

go to a terminal window

Code :
asoundconf list


You should see 2 cards listed....in my case I get

NVidia
Audio

next Code :
asoundconf set-default-card Audio

this should set the default to Audio (Don't ask why it's not named Bose something...I got nothing for you on that)

For some unknown reason changing the Audio settings for system->Preferences->Sound doesn't actually change everything?!

now the only problem I have is if I'm listening to MP3s in the background, and a system noise comes up, all hell breaks lose.  It appears that the built in sound card in the bose system can't handle 2 things at once?!  Not sure...maybe I'm just missing something stupid...

-Ljoslin

---

### Post by ljoslin on 2007-09-25
Maybe a bump w/ a little more info might help....

everytime I get a crash (and I'm assuming the crashes are related to the sound issues because when I use the onboard sound card the issue goes away) I get these errors in my kern.log

Sep 25 15:11:54 larry-desktop kernel: [ 2481.168023] 2:1:1: cannot get freq at e
p 0x1
Sep 25 15:11:55 larry-desktop kernel: [ 2482.366672] cdrom: hda: mrw address spa
ce DMA selected
Sep 25 15:11:55 larry-desktop kernel: [ 2482.451159] cdrom: hda: mrw address spa
ce DMA selected



I don't think the cdrom ones matter but hey....who knows.  The other seems to be related to USB audio!  Thanks for any help!

-=ljoslin=-

---

