---
title: "IBM T30 Wireless - Fiesty Fawn"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by cboebel on 2007-04-20
Greetings -

I am an absolute beginner to Linux. I started with Ubuntu on an IBM T30 laptop with Edgy. Under Edgy, the system recognized the built-in wireless functionality. After updating to FF, the system no longer lists a wireless network controller. Instead, it lists a controller called 'wlan' which does not seem to be what I want.

The wireless controller, eth1, is still listed up top with a warning on it. Double-clicking on the icon gives me an error: SIOCGIFFLAGS error: No such device.

In another thread, someone had asked for output from a couple of commands. I have included the results from lspci, lsmod, and iwconfig.

Any help that someone knowledgeable about the system could give would be much appreciated.

Thank you,
Chris

chris@chris-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #2) (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #3) (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:00.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:02.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
chris@chris-laptop:~$ 


chris@chris-laptop:~$ lsmod
Module                  Size  Used by
ipv6                  268704  8 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
nvram                   9992  1 
uinput                 10240  1 
ppdev                  10116  0 
radeon                124576  0 
drm                    81044  1 radeon
speedstep_ich           6288  0 
speedstep_lib           6148  1 speedstep_ich
cpufreq_userspace       5408  0 
cpufreq_stats           7360  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9228  1 
freq_table              5792  3 speedstep_ich,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8200  0 
tc1100_wmi              8068  0 
pcc_acpi               13184  0 
dev_acpi               12292  0 
sony_acpi               6284  0 
video                  16388  0 
sbs                    15652  0 
ibm_acpi               31512  0 
i2c_ec                  5888  1 sbs
i2c_core               22784  1 i2c_ec
dock                   10268  0 
button                  8720  0 
battery                10756  0 
container               5248  0 
ac                      6020  0 
asus_acpi              17308  0 
backlight               7040  2 ibm_acpi,asus_acpi
lp                     12452  0 
joydev                 10816  0 
snd_intel8x0           34204  1 
snd_ac97_codec         98336  1 snd_intel8x0
hostap_pci             56848  0 
hostap                113924  1 hostap_pci
ieee80211_crypt         7040  1 hostap
orinoco_pci             8064  0 
orinoco                43028  1 orinoco_pci
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
hermes                  8448  2 orinoco_pci,orinoco
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
irtty_sir               9600  0 
sir_dev                17156  1 irtty_sir
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
pcmcia                 39212  0 
nsc_ircc               24208  0 
prism2_pci             70784  0 
p80211                 31884  1 prism2_pci
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
irda                  201276  3 irtty_sir,sir_dev,nsc_ircc
crc_ccitt               3072  1 irda
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
psmouse                38920  0 
pcspkr                  4224  0 
serio_raw               7940  0 
snd                    54020  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
yenta_socket           27532  2 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
intel_agp              25116  1 
agpgart                35400  2 drm,intel_agp
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
af_packet              23816  4 
tsdev                   8768  0 
evdev                  11008  5 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
sd_mod                 23428  3 
ata_piix               15492  2 
ata_generic             9092  0 
libata                125720  2 ata_piix,ata_generic
scsi_mod              142348  4 sg,sr_mod,sd_mod,libata
floppy                 59524  0 
e100                   36232  0 
mii                     6528  1 e100
generic                 5124  0 [permanent]
uhci_hcd               25360  0 
usbcore               134280  2 uhci_hcd
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
chris@chris-laptop:~$ 

chris@chris-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     no wireless extensions.

irda0     no wireless extensions.

---

### Post by chamberlain2006 on 2007-04-20
wlan0 should be what you want, but it's weird that there are no extensions.

---

### Post by cboebel on 2007-04-21
I saw that. Is there a way to add them or update my driver in some way?

Thanks
Chris

---

### Post by cboebel on 2007-04-21
... also, it shows my wlan controller as being a wired connection.

Thanks again.

---

### Post by cboebel on 2007-04-21
All -

In case anyone else has this problem, I found the answer in the Networking and Wireless section.

[Here]("http://ubuntuforums.org/showthread.php?p=2499761#post2499761")

---

