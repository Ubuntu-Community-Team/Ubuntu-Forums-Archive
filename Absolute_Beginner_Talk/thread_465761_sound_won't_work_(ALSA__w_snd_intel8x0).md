---
title: "sound won't work (ALSA  w/ snd_intel8x0)"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by Tau_Lepton on 2007-06-06
I just installed Ubuntu 6.06 on a gateway M210 notebook (kind of dumb I know, but I had the 6.06 cd on hand and my internet is slow).  Anyway, everything works great so far except sound, which won't play.  

Here's the relevant part of lspci's output:
```

0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
```
Here's the output of lsmod:
```
Module                  Size  Used by
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              50020  4 rfcomm,l2cap
ppdev                   9220  0
i915                   20608  1
drm                    73236  2 i915
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
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
i2c_core               21904  1 i2c_acpi_ec
ipv6                  265856  6
dm_mod                 58936  1
af_packet              22920  4
md_mod                 72532  0
sr_mod                 16932  0
sbp2                   24196  0
scsi_mod              139496  2 sr_mod,sbp2
parport_pc             35780  0
lp                     11844  0
parport                36296  3 ppdev,parport_pc,lp
joydev                 10048  0
tsdev                   8000  0
pcmcia                 40508  0
snd_intel8x0           33692  3
snd_ac97_codec         93216  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
ipw2200               107308  0
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
ieee80211              37064  1 ipw2200
ieee80211_crypt         6272  1 ieee80211
b44                    25740  0
ieee80211_1_1_13       38216  0
ieee80211_1_1_13_crypt     6784  1 ieee80211_1_1_13
mii                     5888  1 b44
psmouse                36100  0
yenta_socket           28428  1
rsrc_nonstatic         13440  1 yenta_socket
snd_pcm                89864  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  2 snd_pcm
snd                    55268  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
rtc                    13492  0
serio_raw               7300  0
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
intel_agp              22940  1
agpgart                34888  3 drm,intel_agp
evdev                   9856  2
ext3                  135944  1
jbd                    58772  1 ext3
ide_generic             1536  0
ohci1394               35124  0
ieee1394              299832  2 sbp2,ohci1394
ehci_hcd               34184  0
uhci_hcd               33808  0
usbcore               130820  3 ehci_hcd,uhci_hcd
ide_cd                 33028  0
cdrom                  38560  2 sr_mod,ide_cd
ide_disk               17664  3
piix                   11012  1
generic                 5124  0
thermal                13576  0
processor              23360  1 thermal
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

```

It looks to me like everything should be fine...volume controls, alsamixer, etc. all seem to work just fine, except that no sound will play!  I've looked through the forums for a solution and come up with nothing. Please help!

---

### Post by paydaydaddy on 2007-06-06
I have found this thread to be helpful when I've had sound problems
[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound)
good luck

---

### Post by mercals on 2007-06-06
All of my sound problems came from having 3 sound devices listed. I disabled the onboard sound device in BIOS and then the fun begain. I searched high and low for a way to enable sound through my SB Live! card. There was lots of information out there on sound problems in Ubuntu. I finally found the answer deep in the replies to a post on the Ubuntu forums. A simple fix compared to all the othere information I had encountered. In terminal simply do the following.

asoundconf - This will list commands to use with asoundconf.

asoundconf list - This will list your cards by name.
                  (my output was)
		  Names of available sound cards:
		  rev20
                  Live
                  
asoundconf set-default-card CARD - Card being the name of the sound card      you wish to use. In my case it was Live.

I then right clicked on the volume controller and selected prefrences. Then I selected the correct card for ALSA and Master to control the volume. Haven't had a problem since.

I apologize for not linking to the thread. I forgot to bookmark it (thank you who ever posted this advice).

---

### Post by Tau_Lepton on 2007-06-07
Thanks for the help.  After reading through the comprehensive sound guide, I was able to finally set the mixer settings correctly.  (I thought I had tried everything I could with alsamixer... embarassing. :oops: )

---

