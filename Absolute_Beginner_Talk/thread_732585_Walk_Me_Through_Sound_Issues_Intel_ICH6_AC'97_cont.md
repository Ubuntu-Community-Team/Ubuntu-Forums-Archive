---
title: "Walk Me Through Sound Issues? Intel ICH6 AC'97 controller"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by tajmahall on 2008-03-23
I've seen quite a few posts about problems with ICH6 AC'97 sound cards. I remember when I first installed Gutsy the sound worked fine. After a while I began to have problems, and it's been gone for several months, as I've had no time to tinker. I have some suspicion that the problem is related with video problems I've never resolved:

[http://ubuntuforums.org/showthread.php?t=647188&highlight=youtube+freezing](http://ubuntuforums.org/showthread.php?t=647188&highlight=youtube+freezing)

IIRC correctly, at the time I lost sound I was trying to get flash/video working. In tinkering I may have done something that killed the sound. I seem to remember that for a time I was repeatedly losing sound, then (somehow) restoring it, and losing it again each time I tried to watch a YouTube video or something. Now sound is completely gone. I haven't been bothering with the video issues, but it would be nice to find a fix for those as well.

Recently I've been trying to fix the sound issues directly. I can post any code you like, but briefly, what I've played with is:

[LIST=1]
[*] **Alsamixer** Opening alsamixer and cranking up the volume on everything. (no effect)
[*] **Sound Preferences** Under System > Preferences > Sound, under the devices Tab, I've tried setting the various devices to Autodetect, ALSA, or a specific device. One odd behavior is that when I test any of them, I get a window saying "Testing pipeline" (but no sound), and when I click "OK" to close the window it freezes. I've been using xkill to kill sound preferences at that point. Other methods of testing sound (e.g. playing a file, speaker-test -twav -Ddefault) get nothing either. 
[*] **Identifying my sound card** lspci tells me that my soundcard is 
```

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)

```
which is what everyone has issues with. Everyone seems to find some particular solution. I've tried to duplicate all of them but none has worked out for me. 
[*] **alsa-base** Editing my alsa-base file. (I added a line setting the index for snd-intel8x0 to 0. Now that I try to look back at it I can't find where this file is. Also, I was never clear on whether I needed to recompile something once I edited the file.) 
[*] **External amplifier** Disabling the "external amplifier" option under volume control
[*] **Other driver: snd-intel8x0m** moving every instance of snd-intel8x0m.ko to snd-intel8x0m.ko.original (someone suggested that the regular and modem parts of the sound card were causing issues)
[*] **Backports** installing the "backports" (everything seems to be up to date)
[/LIST]

Sorry if this is a convoluted explanation. I've tried to go through as many posts on the topic as possible but I think I could use some help starting fresh, as by now I'm unsure how I may have further messed things up.

If anyone could walk me through a personalized round of troubleshooting (or any sort of fresh reinstall of whatever's appropriate), I'd really appreciate it.

:)

---

### Post by skrimpy on 2008-03-23
I'm not sure if this will help, but I just resolved the sound issues on my husband's Feisty install.  I did quite a few things, including removing alsa and installing it fresh from the command line and from Synaptic.  What finally ended up working was adding the card as 0 in alsa-base (I see you already did that), and also adding this line:

```
"options snd-intel8x0 ac97_quirk=3"
```

I added the quotes in there too.  I found this at the end of the first post in this thread: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

After adding that I rebooted and it booted back up with sound.  Not sure if you've tried it or not yet, give it a shot if you haven't.  It seems to help with the AC'97 architecture.

---

### Post by tajmahall on 2008-03-26
> **skrimpy said:**
> I'm not sure if this will help, but I just resolved the sound issues on my husband's Feisty install.  I did quite a few things, including removing alsa and installing it fresh from the command line and from Synaptic.  What finally ended up working was adding the card as 0 in alsa-base (I see you already did that), and also adding this line:

```
"options snd-intel8x0 ac97_quirk=3"
```

I added the quotes in there too.  I found this at the end of the first post in this thread: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

After adding that I rebooted and it booted back up with sound.  Not sure if you've tried it or not yet, give it a shot if you haven't.  It seems to help with the AC'97 architecture.

Yeah, I also gave that a try, though I hadn't tried it with the quotation marks. (Still didn't work. :( )

---

### Post by Whiffle on 2008-03-26
Oddly enough, I've never had a single issue with this one in my thinkpad.  Hmm.
I attached a screenshot of my alsamixer settings.  Could you post up the output of "lsmod".  

I think if I were in your situation I would remove everything you can find thats alsa related, and reinstall it (and the configuration files).  Theres always the chance that a fix we did a while ago and forgot about is killing us now.

---

### Post by tajmahall on 2008-03-31
Oops, forgot to check the thread for a while. Anyway, here is lsmod (text file also attached):

```

Module                  Size  Used by
ipv6                  273892  8 
af_packet              24840  2 
i915                   25856  2 
drm                    83348  3 i915
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
acpi_cpufreq           10568  0 
cpufreq_conservative     8072  0 
cpufreq_stats           7232  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5280  0 
cpufreq_ondemand        9612  1 
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
container               5504  0 
sbs                    19592  0 
dock                   10656  0 
button                  8976  0 
video                  18060  0 
battery                11012  0 
ac                      6148  0 
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
joydev                 11328  0 
snd_intel8x0           34972  9 
snd_ac97_codec        101284  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            43008  0 
snd_pcm                80004  7 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_mixer_oss          17664  1 snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53360  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  6 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 41388  0 
ipw2200               149320  0 
ieee80211              35656  1 ipw2200
snd                    54788  20 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
psmouse                39952  0 
serio_raw               8068  0 
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
ieee80211_crypt         7040  1 ieee80211
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
sky2                   46852  0 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
intel_agp              25620  1 
agpgart                35016  3 drm,intel_agp
evdev                  11136  5 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
sd_mod                 30336  3 
ahci                   23300  0 
ata_piix               17540  2 
ata_generic             8452  0 
libata                125168  3 ahci,ata_piix,ata_generic
scsi_mod              147084  5 sbp2,sg,sr_mod,sd_mod,libata
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  3 ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

```

---

