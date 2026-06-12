---
title: "linux image generic causes wireless problem"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by oLdsk3wL on 2006-10-06
Hi,

I have a DELL Inspiron 1505 Laptop. Since this one has the Core 2 Duo, I wanted to switch to the linux generic image. I used the 386 for nearly 4 weeks now (I ha6vent realized that this one only use one processor) and everything works fine with this kernel. I installed the generic with synaptic When I boot with the generic, Ubuntu cannot login to my wireless network. I use the NetworkManager Applet 0.6.3 to connect and find networks. With the generic no Wireless Connection or Network is shown, the applet runs. I really want to use the generic because of my 2 processors. My ubuntu version is Edgy Eft beta.

If you need more information, pls let me know which one.

A side question, with the distribution upgrade it is possible to upgrade to the final release of edgy, isnt it?

I'm grateful for any help I can get. Thanks!

---

### Post by Fass on 2006-10-06
What card do you have and what driver are you using for it? If it is a driver that falls under the "restricted" modules package, did you install the restricted-modules package for the generic kernel?

If you are using ndiswrapper, you may have to compile if from source. I use ndiswrapper and the one that comes with edgy doesn't seem to work. Also, I have never been able to get networkmanager to connect to my wireless network in edgy for some reason. I just configured wpa_supplicant manually though /etc/network/interfaces.

But, first, again, what driver does your card use? Have you installed it? Is it loaded (can you see it when you do lsmod? Can you modprobe it?)?

---

### Post by oLdsk3wL on 2006-10-07
*What card do you have and what driver are you using for it? If it is a driver that falls under the "restricted" modules package, did you install the restricted-modules package for the generic kernel?*

I did not install a restricted package. For the card details:

I took the pictures from the device manager, I hope it is what u asked for.

82801G PCI Express Port 1:
attached pic 1

Pro/Wireless 3945ABG Network Connection
attached pic 2

WLAN Interface
attached pic 3


*If you are using ndiswrapper, you may have to compile if from source. I use ndiswrapper and the one that comes with edgy doesn't seem to work. Also, I have never been able to get networkmanager to connect to my wireless network in edgy for some reason. I just configured wpa_supplicant manually though /etc/network/interfaces.*

As far as I can tell I dont use ndiswrapper

[I]
But, first, again, what driver does your card use? Have you installed it? Is it loaded (can you see it when you do lsmod? Can you modprobe it?)?[/I]

For the driver I hope the pictures help. I only installed the nm applet for security, but the wlan device was found by ubuntu. Didnt have much to do.
Here is what ls shows me. I found the ipw3945 driver, but when I modprobe the driver nothing happens.

Module                  Size  Used by
ipv6                  272160  10 
binfmt_misc            13448  1 
rfcomm                 42260  0 
hidp                   34176  2 
l2cap                  27136  10 rfcomm,hidp
speedstep_centrino      9760  1 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  2 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sbs                    16804  0 
sony_acpi               6412  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
i2c_core               23424  1 i2c_ec
hotkey                 11556  0 
dev_acpi               12292  0 
button                  7952  0 
battery                11652  0 
container               5632  0 
ac                      6788  0 
asus_acpi              17688  0 
nls_utf8                3200  1 
ntfs                  112116  1 
dm_mod                 62232  1 
af_packet              24584  2 
md_mod                 82836  0 
fuse                   43912  0 
sbp2                   24584  0 
parport_pc             37796  0 
lp                     12964  0 
parport                39496  2 parport_pc,lp
joydev                 11200  0 
hci_usb                18068  2 
b44                    26764  0
HERE IS THE DRIVER
ipw3945               124576  0 
sdhci                  20108  0 
snd_hda_intel          20116  1 
snd_hda_codec         164608  1 snd_hda_intel
sr_mod                 18212  0 
tsdev                   9152  0 
mmc_core               32392  1 sdhci
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
sg                     37404  0 
mii                     6912  1 b44
bluetooth              53476  8 rfcomm,hidp,l2cap,hci_usb
cdrom                  38944  1 sr_mod
usbhid                 45152  0 
snd_pcm                84612  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
ieee80211              35272  1 ipw3945
ieee80211_crypt         7552  1 ieee80211
hw_random               7320  0 
evdev                  11392  2 
snd                    58372  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
pcspkr                  4352  0 
psmouse                41352  0 
serio_raw               8452  0 
intel_agp              24860  1 
agpgart                34888  1 intel_agp
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
ext3                  142728  1 
jbd                    62228  1 ext3
ohci1394               37040  0 
ieee1394              306104  2 sbp2,ohci1394
uhci_hcd               24968  0 
ehci_hcd               34696  0 
usbcore               134912  5 hci_usb,usbhid,uhci_hcd,ehci_hcd
ide_generic             2432  0 
sd_mod                 22656  4 
generic                 5764  0 
ata_piix               14084  8 
libata                 74892  1 ata_piix
scsi_mod              144648  5 sbp2,sr_mod,sg,sd_mod,libata
thermal                15624  0 
processor              31560  2 speedstep_centrino,thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability

---

### Post by oLdsk3wL on 2006-10-07
Here is the lsmod when I start with the 386 kernel

Module                  Size  Used by
michael_mic             2816  4 
arc4                    2304  4 
ieee80211_crypt_tkip    11520  2 
ipv6                  257632  8 
binfmt_misc            11784  1 
rfcomm                 38936  0 
hidp                   32000  2 
l2cap                  23300  10 rfcomm,hidp
speedstep_centrino      8576  1 
cpufreq_userspace       4372  0 
cpufreq_stats           5892  0 
freq_table              4996  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       2048  0 
cpufreq_ondemand        6944  1 
cpufreq_conservative     7200  0 
video                  16644  0 
tc1100_wmi              7428  0 
sbs                    15776  0 
sony_acpi               5516  0 
pcc_acpi               13184  0 
i2c_ec                  5376  1 sbs
hotkey                 10660  0 
dev_acpi               11140  0 
button                  7056  0 
battery                10756  0 
container               4736  0 
ac                      5892  0 
asus_acpi              16792  0 
nls_utf8                2304  1 
ntfs                  108148  1 
af_packet              21768  8 
dm_mod                 59832  1 
md_mod                 78740  0 
fuse                   41864  0 
sbp2                   23304  0 
parport_pc             36132  0 
lp                     11972  0 
parport                37320  2 parport_pc,lp
usbhid                 42464  0 
sg                     35356  0 
sr_mod                 17060  0 
cdrom                  37792  1 sr_mod
hci_usb                15892  2 
joydev                 10304  0 
tsdev                   8256  0 
bluetooth              48996  8 rfcomm,hidp,l2cap,hci_usb
b44                    24972  0 
sdhci                  18316  0 
mmc_core               30488  1 sdhci
ipw3945               120992  1 
mii                     6016  1 b44
snd_hda_intel          18580  1 
snd_hda_codec         163712  1 snd_hda_intel
snd_pcm_oss            46080  0 
snd_mixer_oss          18560  1 snd_pcm_oss
snd_pcm                80520  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              23172  1 snd_pcm
snd                    55428  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
ieee80211              33608  1 ipw3945
ieee80211_crypt         6016  2 ieee80211_crypt_tkip,ieee80211
i2c_core               22288  1 i2c_ec
serio_raw               7300  0 
hw_random               6168  0 
pcspkr                  3072  0 
soundcore               9952  1 snd
evdev                  10496  2 
rtc                    12596  0 
intel_agp              23964  1 
agpgart                33456  1 intel_agp
psmouse                40072  0 
snd_page_alloc         10504  2 snd_hda_intel,snd_pcm
shpchp                 40856  0 
pci_hotplug            31284  1 shpchp
ext3                  138632  1 
jbd                    55700  1 ext3
ohci1394               35248  0 
ieee1394              302904  2 sbp2,ohci1394
ehci_hcd               32520  0 
uhci_hcd               23176  0 
usbcore               130304  5 usbhid,hci_usb,ehci_hcd,uhci_hcd
ide_generic             1536  0 
sd_mod                 21648  4 
generic                 4868  0 
ata_piix               13188  8 
libata                 73228  1 ata_piix
scsi_mod              141320  5 sbp2,sg,sr_mod,sd_mod,libata
thermal                14600  0 
processor              26028  2 speedstep_centrino,thermal
fan                     5124  0 
fbcon                  40480  0 
tileblit                2944  1 fbcon
font                    8448  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2432  1 bitblit
vesafb                  8348  0 
capability              5000  0 
commoncap               7808  1 capability

---

### Post by oLdsk3wL on 2006-10-08
ok i only had to install the restricted module for the generic kernel.

---

