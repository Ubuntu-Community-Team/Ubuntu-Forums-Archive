---
title: "where is my ethernet connection??"
date: 2005-07-28
forum: Absolute Beginner Talk
---

### Post by x1c0 on 2005-07-28
Hi, i'm a beginner, i install Ubuntu today  :) 

I need help because i think that Ubuntu does not recognize my network card

when i go to Network settings only shows Modem connection and wireless connection

what can i do to install ethernet connection??

please, help :(

---

### Post by pestilence4hr on 2005-07-29
[QUOTE=x1c0]
what can i do to install ethernet connection??

please, help :([/QUOTE]

Open up a terminal, and type "lspci".  Paste that here.  Also, "lsmod".  Paste that here too.  This will give more info about your situation to us.

---

### Post by x1c0 on 2005-07-29
ok here goes:

-------------------- lspci -----------------------

0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. Mobile Memory Controller Hub PCI Express Port (rev 03)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
0000:00:1e.3 Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.2 IDE interface: Intel Corp. 82801FBM (ICH6M) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0148 (rev a2)
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4362 (rev 15)
0000:06:02.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)
0000:06:04.0 CardBus bridge: Texas Instruments: Unknown device 8031
0000:06:04.1 CardBus bridge: Texas Instruments: Unknown device 8031
0000:06:04.2 FireWire (IEEE 1394): Texas Instruments: Unknown device 8032
0000:06:04.3 Unknown mass storage controller: Texas Instruments: Unknown device 8033
0000:06:04.4 0805: Texas Instruments: Unknown device 8034

------------------- lsmod ----------------------

Module                  Size  Used by
ipv6                  229504  6
speedstep_centrino      7892  1
proc_intf               4100  0
freq_table              4100  1 speedstep_centrino
cpufreq_userspace       4572  1
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0
video                  16260  0
sony_acpi               6280  0
pcc_acpi               11264  0
button                  6800  0
battery                10244  0
container               4608  0
ac                      4996  0
af_packet              20744  2
ohci1394               31876  0
yenta_socket           19584  0
pcmcia_core            53568  1 yenta_socket
ipw2200                66156  0
firmware_class          9728  1 ipw2200
ieee80211              21252  1 ipw2200
ieee80211_crypt         5832  1 ieee80211
sk98lin               149216  0
i2c_i801                8076  0
i2c_core               21264  1 i2c_i801
ahci                   10500  0
snd_intel8x0           29984  2
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  3 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm
ehci_hcd               29444  0
usbhid                 29376  0
uhci_hcd               30224  0
usbcore               107384  4 ehci_hcd,usbhid,uhci_hcd
shpchp                 86116  0
pci_hotplug            30512  1 shpchp
intel_agp              20636  1
agpgart                31784  1 intel_agp
rtc                    12216  0
md                     43856  0
evdev                   9088  0
dm_mod                 53116  1
tsdev                   7488  0
capability              5000  0
commoncap               7808  1 capability
sbp2                   22408  0
ieee1394              100408  2 ohci1394,sbp2
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  1
lp                     10792  0
parport                33480  2 parport_pc,lp
ext3                  120968  1
jbd                    54168  1 ext3
sr_mod                 16036  0
cdrom                  36508  1 sr_mod
sd_mod                 16784  2
sg                     35360  0
ata_piix                8836  4
libata                 44548  2 ahci,ata_piix
scsi_mod              119936  6 ahci,sbp2,sr_mod,sd_mod,sg,libata
unix                   26164  806
thermal                13576  0
processor              22708  2 speedstep_centrino,thermal
fan                     4612  0
fbcon                  34048  0
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb

-------------------------------

thanks for reply ;-)  please help

---

### Post by pestilence4hr on 2005-07-29
[QUOTE=x1c0]
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4362 (rev 15)
0000:06:02.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)
[/QUOTE]

Hrmm...looks like some unsupported hardware.  From some googling I found [this](http://www.syskonnect.de/syskonnect/support/driver/htm/sk9elin.htm), but I'm not entirely sure that's the card that you have.   Worth a shot.  On the other hand, I'm sure you can get your wireless card working.  See [the ipw2200 sourceforge project](http://ipw2200.sourceforge.net/) for those drivers.

---

