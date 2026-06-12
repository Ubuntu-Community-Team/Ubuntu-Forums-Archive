---
title: "sidewinder joystick not working...."
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by stonerrob420 on 2007-05-17
Hello:) I have been using ubuntu dapper for about 4 or 5 monthes and have not been able to get my joystick to work. I have followed the instructions in this forum post [http://ubuntuforums.org/showthread.php?t=330607](http://ubuntuforums.org/showthread.php?t=330607) but nothing works..... 
here is the output for lsmod in teminal it shows that the gameport and sidewinder driver are loaded but jscalbrator cant open the file ...
Module                  Size  Used by
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              50020  4 rfcomm,l2cap
vboxdrv                31364  0
ppdev                   9220  0
ipt_limit               2432  6
iptable_mangle          2944  0
ipt_LOG                 6912  8
ipt_MASQUERADE          3456  0
ip_nat                 19628  1 ipt_MASQUERADE
ipt_TOS                 2560  0
ipt_REJECT              5632  1
ip_conntrack_irc        6768  0
ip_conntrack_ftp        7792  0
ipt_state               2048  6
ip_conntrack           51500  5 ipt_MASQUERADE,ip_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
nfnetlink               6552  2 ip_nat,ip_conntrack
iptable_filter          3072  1
ip_tables              22400  8 ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
ppp_deflate             6272  0
zlib_deflate           24344  1 ppp_deflate
bsd_comp                6272  0
ppp_async              11904  1
crc_ccitt               2304  1 ppp_async
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
ipv6                  265856  14
ppp_generic            30100  7 ppp_deflate,bsd_comp,ppp_async
slhc                    7424  1 ppp_generic
af_packet              22920  0
dm_mod                 58936  1
md_mod                 72532  0
sidewinder             12032  0
joydev                 10048  0
lp                     11844  0
snd_ens1370            19552  1
gameport               15496  2 sidewinder,snd_ens1370
snd_rawmidi            25504  1 snd_ens1370
snd_seq_device          8716  1 snd_rawmidi
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  2 snd_ens1370,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd_page_alloc         10632  2 snd_ens1370,snd_pcm
snd_ak4531_codec        7936  1 snd_ens1370
pcspkr                  2180  0
psmouse                36100  0
3c59x                  45608  0
snd                    55268  10 snd_ens1370,snd_rawmidi,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_ak4531_codec
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
mii                     5888  1 3c59x
nvidia               4551028  12
soundcore              10208  1 snd
serio_raw               7300  0
hw_random               5652  0
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
intel_agp              22940  1
agpgart                34888  2 nvidia,intel_agp
rtc                    13492  0
i2c_i810                5252  0
i2c_algo_bit            9608  1 i2c_i810
i2c_core               21904  3 i2c_acpi_ec,nvidia,i2c_algo_bit
tsdev                   8000  0
evdev                   9856  1
ext3                  135944  1
jbd                    58772  1 ext3
usbhid                 39904  0
ide_generic             1536  0
uhci_hcd               33808  0
usbcore               130820  3 usbhid,uhci_hcd
ide_disk               17664  3
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
piix                   11012  1
generic                 5124  0
pdc202xx_old           11392  1
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

 im lost..... any help would be much apperciated :( :confused:

---

### Post by alienexplorers on 2007-05-18
I followed the direction is the link in your post and now my joystick works.  I had some problems, but after trying it and making sure I was using the correct data especially in section 4.

---

### Post by stonerrob420 on 2007-05-18
Thanks for the help but this is what i dont understand clearly. Should the /etc/modules look like this? 

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
#
#joystick gameport
gameport               15496  2 snd_ens1370
joydev                 10048  0
sidewinder             12032  0

OR

like this?# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
#
#joystick gameport
gameport               15496  2 snd_ens1370
joydev 
sidewinder 

But now since I changed it to the first option lsmod looks like this?

rob@rob-desktop:~$ lsmod
Module                  Size  Used by
joydev                 10048  0
sidewinder             12032  0
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              50020  4 rfcomm,l2cap
vboxdrv                31364  0
ppdev                   9220  0
ipt_limit               2432  6
iptable_mangle          2944  0
ipt_LOG                 6912  8
ipt_MASQUERADE          3456  0
ip_nat                 19628  1 ipt_MASQUERADE
ipt_TOS                 2560  0
ipt_REJECT              5632  1
ip_conntrack_irc        6768  0
ip_conntrack_ftp        7792  0
ipt_state               2048  6
ip_conntrack           51500  5 ipt_MASQUERADE,ip_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
nfnetlink               6552  2 ip_nat,ip_conntrack
iptable_filter          3072  1
ip_tables              22400  8 ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
ppp_deflate             6272  0
zlib_deflate           24344  1 ppp_deflate
bsd_comp                6272  0
ppp_async              11904  1
crc_ccitt               2304  1 ppp_async
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
ipv6                  265856  10
ppp_generic            30100  7 ppp_deflate,bsd_comp,ppp_async
slhc                    7424  1 ppp_generic
af_packet              22920  0
dm_mod                 58936  1
md_mod                 72532  0
lp                     11844  0
snd_ens1370            19552  3
gameport               15496  2 sidewinder,snd_ens1370
snd_rawmidi            25504  1 snd_ens1370
snd_seq_device          8716  1 snd_rawmidi
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_ens1370,snd_pcm_oss
snd_timer              25220  2 snd_pcm
snd_page_alloc         10632  2 snd_ens1370,snd_pcm
snd_ak4531_codec        7936  1 snd_ens1370
pcspkr                  2180  0
3c59x                  45608  0
mii                     5888  1 3c59x
psmouse                36100  0
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
snd                    55268  12 snd_ens1370,snd_rawmidi,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_ak4531_codec
i2c_i810                5252  0
i2c_algo_bit            9608  1 i2c_i810
soundcore              10208  1 snd
serio_raw               7300  0
nvidia               4551028  12
i2c_core               21904  3 i2c_acpi_ec,i2c_algo_bit,nvidia
intel_agp              22940  1
agpgart                34888  2 nvidia,intel_agp
hw_random               5652  0
rtc                    13492  0
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
tsdev                   8000  0
evdev                   9856  1
ext3                  135944  1
jbd                    58772  1 ext3
usbhid                 39904  0
ide_generic             1536  0
uhci_hcd               33808  0
usbcore               130820  3 usbhid,uhci_hcd
ide_disk               17664  3
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
piix                   11012  1
generic                 5124  0
pdc202xx_old           11392  1
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
rob@rob-desktop:~$

What have I done wrong? they both dont work

---

