---
title: "wireless issue some problems pls comment"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by violin on 2008-02-02
hi all 

I decided to install ubuntu edgy on my box which by the way I like the most. Any way I have a problem :Wireless :d

I searched on the forum, google but I couldnt fix the problem. Maybe you guys can give me some tips.


[PHP]iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.[/PHP]

[PHP] sudo modprobe ipw3495
FATAL: Module ipw3495 not found.
[/PHP]


[PHP]Module                  Size  Used by
ipv6                  272544  10 
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
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
hotkey                 11556  0 
dev_acpi               12292  0 
button                  7952  0 
battery                11652  0 
container               5632  0 
ac                      6788  0 
asus_acpi              17688  0 
sbp2                   24584  0 
parport_pc             37796  0 
lp                     12964  0 
parport                39496  2 parport_pc,lp
af_packet              24584  2 
joydev                 11200  0 
tsdev                   9152  0 
pcmcia                 40380  0 
snd_hda_intel          20116  1 
snd_hda_codec         164608  1 snd_hda_intel
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
sg                     37404  0 
sr_mod                 18212  0 
snd_pcm                84612  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
r1000                  17792  0 
cdrom                  38944  1 sr_mod
snd_timer              25348  1 snd_pcm
tifm_7xx1               9472  0 
sdhci                  20108  0 
mmc_core               32136  1 sdhci
yenta_socket           28812  1 
rsrc_nonstatic         15360  1 yenta_socket
pcmcia_core            43924  3 pcmcia,yenta_socket,rsrc_nonstatic
intel_agp              26012  1 
i2c_core               23424  1 i2c_ec
tifm_core              10496  1 tifm_7xx1
psmouse                41352  0 
agpgart                34888  1 intel_agp
snd                    58372  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
serio_raw               8452  0 
hw_random               7320  0 
soundcore              11232  1 snd
evdev                  11392  2 
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
ext3                  142856  1 
jbd                    62228  1 ext3
ehci_hcd               34696  0 
ohci1394               37040  0 
ieee1394              306104  2 sbp2,ohci1394
uhci_hcd               24968  0 
usbcore               134912  3 ehci_hcd,uhci_hcd
ide_generic             2432  0 
sd_mod                 22656  3 
generic                 6276  0 
ata_piix               11780  2 
libata                 74892  1 ata_piix
scsi_mod              144648  5 sbp2,sg,sr_mod,sd_mod,libata
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
[/PHP]


thanks in advance

ps: I also install linux-restricted modules. it  is the newest one. Any suggetions?

---

### Post by violin on 2008-02-02
no suggestion!!!!

---

### Post by mikeyphi on 2008-02-02
Do you know the name and version of your wireless card?

---

### Post by violin on 2008-02-02
Intel(R) Wireless WiFi Link 4965AGN

---

### Post by jan quark on 2008-02-02
try this guide

[https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty?highlight=%28WifiDocs%2FDriver%29](https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty?highlight=%28WifiDocs%2FDriver%29)

---

### Post by OldLinuxGuy on 2008-02-02
With my laptop and card it was a matter of getting the drivers.  Try this link for drivers for your card  [http://support.intel.com/support/notebook/sb/CS-006408.htm](http://support.intel.com/support/notebook/sb/CS-006408.htm)

---

### Post by violin on 2008-02-02
> **jan quark said:**
> try this guide

[https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty?highlight=%28WifiDocs%2FDriver%29](https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty?highlight=%28WifiDocs%2FDriver%29)

Does this completable with egdy?

---

### Post by jan quark on 2008-02-02
perhaps I am telling you complete crap but IMO it is worth a try :)
feel free to correct me

---

### Post by violin on 2008-02-02
ill give it a shot see what happens.

cheers

---

### Post by violin on 2008-02-02
lsmod |grep ipw
ipw3945               124576  0 
ieee80211              35144  1 ipw3945

do you guys know what is the next step now to use wireless

---

### Post by jan quark on 2008-02-02
can you please tell us, if you are following the posted guide, which steps you have already done successfully?

---

### Post by violin on 2008-02-02
I figured out thanks jan quark.

---

### Post by jan quark on 2008-02-02
great to hear violin

if you feel the problem is solved please mark also this thread as solved
using the thread tools at the top of the page

thank you

---

### Post by violin on 2008-02-02
Actually &#305; have bad news after following the guide you gave me everything worked. then i restart the box its sees ipw3495


[PHP]lsmod |grep ipw
ipw3945               120992  0 
ieee80211              33608  1 ipw3945
[/PHP]


but  when I run iwconfig it gives  this: 

[PHP]iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.
[/PHP]

again I stuck and I cant remeber how did I manage to work?  I have to work on that again :(

---

### Post by jan quark on 2008-02-02
was there a time when you could connect to the internet?

try this to refresh the network configuration

```
sudo /etc/init.d/networking restart
```

and run iwconfig after that

---

### Post by violin on 2008-02-02
[PHP] * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 3346
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:16:d4:97:7d:5a
Sending on   LPF/eth0/00:16:d4:97:7d:5a
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:16:d4:97:7d:5a
Sending on   LPF/eth0/00:16:d4:97:7d:5a
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.3 -- renewal in 42433 seconds.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
                                                                         [ ok ][/PHP]
[PHP]iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.[/PHP]

Nothing still same :mad:

---

