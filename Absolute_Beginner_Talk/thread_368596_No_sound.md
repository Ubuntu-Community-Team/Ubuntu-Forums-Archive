---
title: "No sound"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by e^(i*pi) on 2007-02-23
I usually use my computer with the sound turned down, so I didn't notice this until today, but it doesn't seem as though my computer has any sound when I'm using ubuntu.  I've tried turning the volume up everywhere I can think of and I also checked out System > Preferences > sound and everything looked good there.  Any suggestions?

---

### Post by taurus on 2007-02-23
What about 

```
alsamixer
```

---

### Post by rsambuca on 2007-02-23
Are they plugged in?;)

---

### Post by e^(i*pi) on 2007-02-23
What is it that I should be looking for in alsamixer?  And it's on a laptop, so I'm sure the speakers are plugged in:)

---

### Post by taurus on 2007-02-24
The volumes.  The best way is to open xmms (or whatever media player you use) and have it play your mp3 files.  Then, try to turn on the volumes by using the up arrow to see if you get any sound.

---

### Post by e^(i*pi) on 2007-02-24
Ok, I tried listening to the Mandela ubuntu speech in the examples directory and I tried playing a cd with sound juicer while adjusting all of the different volumes in alsamixer, still no luck so far.

---

### Post by e^(i*pi) on 2007-02-24
could it be an issue with my ubuntu and my sound card not playing well together?

---

### Post by taurus on 2007-02-24
Well, what kind of sound card do you have then?

```
lspci
lsmod
```

---

### Post by e^(i*pi) on 2007-02-24
under sound preferences it says my default card is: intel 82801DB-ICH4

and when I ran the lspci command it said that my multimedia audo controller is:
 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH 4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)


If you need to know anything else just let me know, and thanks for trying to help.

---

### Post by taurus on 2007-02-24
Let's see if there is any module loaded for your soundcard.

```
lsmod
```

---

### Post by e^(i*pi) on 2007-02-24
here is the output, it's a bit lengthy, but I wanted to make sure it would have what you are looking for

Module                  Size  Used by
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              50020  4 rfcomm,l2cap
ppdev                   9220  0
i915                   20608  1
drm                    73236  2 i915
speedstep_centrino      8400  1
cpufreq_userspace       4696  1
cpufreq_stats           5636  0
freq_table              4740  2 speedstep_centrino,cpufreq_stats
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
nls_iso8859_1           4224  1
nls_cp437               5888  1
vfat                   13440  1
fat                    53020  1 vfat
nls_utf8                2176  1
ntfs                  103536  1
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
ipw2200               107308  0
ieee80211              37064  1 ipw2200
ieee80211_crypt         6272  1 ieee80211
ieee80211_1_1_13       38216  0
ieee80211_1_1_13_crypt     6784  1 ieee80211_1_1_13
psmouse                36100  0
b44                    25740  0
mii                     5888  1 b44
yenta_socket           28428  1
rsrc_nonstatic         13440  1 yenta_socket
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
serio_raw               7300  0
snd_intel8x0           33692  3
snd_ac97_codec         93216  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  2 snd_pcm
snd                    55268  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
rtc                    13492  0
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
ide_disk               17664  5
piix                   11012  1
generic                 5124  0
thermal                13576  0
processor              23360  2 speedstep_centrino,thermal
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
bill@bill-laptop:~$

---

### Post by taurus on 2007-02-24
Have a look in 

System -> Preferences -> Sound

and make sure you see your soundcard (and pick it as default) from the drop down menu at the bottom of that window.

p.s.  And I assume you have the volume on your laptop on loud too...

---

### Post by e^(i*pi) on 2007-02-24
Ok, System -> Preferences -> Sound shows that my default soundcard is Intel 82801DB-ICH4

my sound is turned up on my laptop as well as in every place in the system I can find to turn it up.

---

### Post by taurus on 2007-02-24
Are you able to hear any sound when Gnome starts up from the LiveCD?

---

### Post by e^(i*pi) on 2007-02-24
I'm going to dig up my liveCD here and try it

---

### Post by e^(i*pi) on 2007-02-24
I just booted from the liveCD that I used to install ubuntu on computer, no sound there either.

---

### Post by taurus on 2007-02-24
Is Ubuntu the only OS on that laptop?

---

### Post by e^(i*pi) on 2007-02-24
no, dual-boot with windows xp, volume works fine on windows

---

### Post by e^(i*pi) on 2007-02-24
could that be having an adverse effect?

---

### Post by leondu on 2007-02-24
wow,I have exactly the same problem as yours. So let me know if you solved it.

I am using a song laptop (tr5zc).

---

### Post by e^(i*pi) on 2007-02-24
I was told that if I ran this script that I found that the output would help someone figure out what my problem is, so here is the output.  I hope it helps.

bill@bill-laptop:~/programs$ ./aadebug
ALSA Audio Debug v0.1.0 - Sat Feb 24 21:59:14 EST 2007
[http://alsa.opensrc.org/aadebug](http://alsa.opensrc.org/aadebug)
[http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Kernel ----------------------------------------------------
Linux bill-laptop 2.6.15-28-386 #1 PREEMPT Thu Feb 1 15:51:56 UTC 2007 i686 GNU/Linux

Loaded Modules --------------------------------------------
snd_intel8x0           33692  4
snd_ac97_codec         93216  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  2 snd_pcm
snd                    55268  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm

Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
Advanced Linux Sound Architecture Driver Version 1.0.10rc3 (Mon Nov 07 13:30:21 2005 UTC).
0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                     Intel 82801DB-ICH4 with AD1981B at 0xe0100c00, irq 177
 20: [0- 4]: digital audio playback
 27: [0- 3]: digital audio capture
 26: [0- 2]: digital audio capture
 25: [0- 1]: digital audio capture
 16: [0- 0]: digital audio playback
 24: [0- 0]: digital audio capture
  0: [0- 0]: ctl
 33:       : timer
cat: /proc/asound/hwdep: No such file or directory
00-00: Intel ICH : Intel 82801DB-ICH4 : playback 1 : capture 1
00-01: Intel ICH - MIC ADC : Intel 82801DB-ICH4 - MIC ADC : capture 1
00-02: Intel ICH - MIC2 ADC : Intel 82801DB-ICH4 - MIC2 ADC : capture 1
00-03: Intel ICH - ADC2 : Intel 82801DB-ICH4 - ADC2 : capture 1
00-04: Intel ICH - IEC958 : Intel 82801DB-ICH4 - IEC958 : playback 1
cat: /proc/asound/seq/clients: No such file or directory

Dev Snd ---------------------------------------------------
controlC0  pcmC0D0c  pcmC0D0p  pcmC0D1c  pcmC0D2c  pcmC0D3c  pcmC0D4p  timer

CPU -------------------------------------------------------
model name      : Intel(R) Pentium(R) M processor 1.70GHz
cpu MHz         : 598.150

RAM -------------------------------------------------------
MemTotal:      1002504 kB
SwapTotal:     3582484 kB

Hardware --------------------------------------------------
0000:00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)

---

### Post by e^(i*pi) on 2007-02-24
bump

---

### Post by AstarothCY on 2007-09-14
bump, did you ever fix this?

---

