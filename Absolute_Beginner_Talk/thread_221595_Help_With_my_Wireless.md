---
title: "Help With my Wireless"
date: 2006-07-23
forum: Absolute Beginner Talk
---

### Post by basherbob on 2006-07-23
I have tried searching various help documents here on the ubunto website, but  being very new to linux, i really dont understand most of it. I am an experienced windows user and use to be ok with dos. Right now I am trying to go through the troublershooting guide at:[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

I will post my steps here:
It tells me to see if my card is recognized. I cope and past the command lines.

basherbob@basherbob-laptop:~$ sudo cardctl ident
sudo: cardctl: command not found
basherbob@basherbob-laptop:~$

Thens it says check for a driver using lshw. I got the folowing:
product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Control ler
                vendor: Broadcom Corporation
                physical id: 7
                bus info: pci@03:07.0
                logical name: eth0
                version: 02
                serial: 00:14:a5:3b:64:95
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master ethernet physical wireless
                configuration: broadcast=yes driver=bcm43xx multicast=yes wirele ss=IEEE 802.11b/g
                resources: iomemory:c0200000-c0201fff irq:185
basherbob@basherbob-laptop:~$ lsmod
Module                  Size  Used by
isofs                  39808  1
udf                    86816  0
rfcomm                 45600  0
l2cap                  30464  5 rfcomm
bluetooth              59268  4 rfcomm,l2cap
ppdev                  11400  0
radeon                124320  1
drm                    96296  2 radeon
powernow_k8            12992  0
cpufreq_userspace       9184  1
cpufreq_stats           8264  0
freq_table              6464  2 powernow_k8,cpufreq_stats
cpufreq_powersave       3328  0
cpufreq_ondemand        9768  0
cpufreq_conservative    10984  0
video                  18824  0
tc1100_wmi              9096  0
sony_acpi               7188  0
pcc_acpi               16128  0
hotkey                 13768  0
dev_acpi               15364  0
container               6272  0
button                  8864  0
acpi_sbs               24600  0
battery                12296  1 acpi_sbs
ac                      7176  1 acpi_sbs
i2c_acpi_ec             7040  1 acpi_sbs
i2c_core               26624  1 i2c_acpi_ec
nls_iso8859_1           6656  1
nls_cp437               8320  2
vfat                   16768  1
fat                    57136  1 vfat
nls_utf8                3584  1
ntfs                  101376  1
ipv6                  300416  10
dm_mod                 63176  1
md_mod                 76792  0
sr_mod                 19748  0
sbp2                   27908  0
scsi_mod              160504  2 sr_mod,sbp2
af_packet              28172  4
parport_pc             40816  0
lp                     15040  0
parport                44172  3 ppdev,parport_pc,lp
joydev                 13184  0
acx                   103568  0
bcm43xx               127244  0
pcmcia                 46368  0
ieee80211softmac       32640  1 bcm43xx
psmouse                40324  0
ieee80211              39240  2 bcm43xx,ieee80211softmac
ieee80211_crypt         8448  1 ieee80211
serio_raw               9732  0
tsdev                  10240  0
yenta_socket           30604  1
rsrc_nonstatic         14592  1 yenta_socket
pcmcia_core            48036  3 pcmcia,yenta_socket,rsrc_nonstatic
usbhid                 43040  0
sky2                   45700  0
snd_atiixp             23704  1
pcspkr                  3592  0
snd_atiixp_modem       19468  0
snd_ac97_codec        110396  2 snd_atiixp,snd_atiixp_modem
snd_ac97_bus            4096  1 snd_ac97_codec
snd_pcm_oss            59424  0
snd_mixer_oss          20608  1 snd_pcm_oss
snd_pcm               104584  4 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss
snd_timer              29064  1 snd_pcm
snd                    68576  9 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              13216  1 snd
snd_page_alloc         13968  3 snd_atiixp,snd_atiixp_modem,snd_pcm
shpchp                 51360  0
pci_hotplug            33168  1 shpchp
evdev                  14464  2
ext3                  145936  1
jbd                    70952  1 ext3
ide_generic             2816  0
ohci1394               37324  0
ieee1394              369048  2 sbp2,ohci1394
ehci_hcd               36232  0
ohci_hcd               23684  0
usbcore               147004  5 acx,usbhid,ehci_hcd,ohci_hcd
ide_cd                 35744  1
cdrom                  41144  2 sr_mod,ide_cd
ide_disk               19456  4
generic                 7300  0
atiixp                  8464  1
thermal                16524  0
processor              29224  2 powernow_k8,thermal
fan                     6408  0
capability              7176  0
commoncap               9728  1 capability
vga16fb                15120  1
cfbcopyarea             5120  1 vga16fb
vgastate               10368  1 vga16fb
cfbimgblt               4224  1 vga16fb
cfbfillrect             5760  1 vga16fb
fbcon                  43136  72
tileblit                4096  1 fbcon
font                    9984  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
basherbob@basherbob-laptop:~$

Then I look for a router connection:

basherbob@basherbob-laptop:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

basherbob@basherbob-laptop:~$


From there in goes into a bunch of different instructions that I simply dont understand. My ethernet card is working fine. My wireless router is open..no wep key.
The wifi light on my laptop is not on. Im hopeing some kind person will walk me through setting it up in a manner i can understand. Thanks in advance.

---

### Post by xXx 0wn3d xXx on 2006-07-23
[ Follow this tutorial. ](http://ubuntuforums.org/showthread.php?t=185174&highlight=bcm43xx)

---

### Post by basherbob on 2006-07-23
Thanks I will give it a try and report back. Thanks!:)

---

### Post by mudguts on 2006-07-23
This might/might not be useful.  I switched from eth1 to ath0
that's where my wifi pcmcia card was.

---

### Post by basherbob on 2006-07-23
I went through the tutorial, and it half worked. The light is now on for my wifi card. I downloaded wifi radar, and it doesnt pick up the signal for my router. I think I am closer, thanks for your help. Any ideas?
Thanks kindly

---

### Post by psycosmyth on 2006-07-23
Ditto, I had that problem with SUSE, just used atho1 instead. Check into MADWIFI. I personaly could not get Linksys cards to work, I just used a D-link.

---

### Post by basherbob on 2006-07-23
More info- I have a newer gateway laptop with a AMD 64 athlon and a built in broadcom 4318 card. Heres a copy and paste from my terminal:

basherbob@basherbob-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:"default"  Nickname:"ssid"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid
          Bit Rate=11 Mb/s   Tx-Power=18 dBm
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

Thanks again

---

### Post by xXx 0wn3d xXx on 2006-07-23
> **basherbob said:**
> More info- I have a newer gateway laptop with a AMD 64 athlon and a built in broadcom 4318 card. Heres a copy and paste from my terminal:

basherbob@basherbob-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:"default"  Nickname:"ssid"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid
          Bit Rate=11 Mb/s   Tx-Power=18 dBm
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

Thanks again

Is it a Gateway MX7118 ? If so I have the same computer. Do you have the dumped broadcom files in /lib/firmware ? If so and it still doesn't work, try: "sudo modprobe bcm43xx" (then add it on a new line in /etc/modules) and then add "blacklist ndiswrapper" in /etc/modprobe.d/blacklist on a new line. If that still doesn't work look at [ this. ](http://ubuntuforums.org/showthread.php?t=197102&highlight=bcm43xx)

---

### Post by basherbob on 2006-07-23
its a mx7515...I will try it ...thanks!

---

### Post by Iandefor on 2006-07-23
You're in luck. There's a howto on the forums specifically about getting your specific wireless chipset working. I've tried it myself, works like a charm :-D.

[http://www.ubuntuforums.org/showthread.php?t=197102](http://www.ubuntuforums.org/showthread.php?t=197102)

---

### Post by basherbob on 2006-07-23
Sorry...Thanks for all your help...didnt work:(

---

### Post by basherbob on 2006-07-23
Sorry...thanks for all your help...didnt work. I guess I will have to use windows when I go mobile. I will use Ubunto at home. Perhaps the next update will support my card.

---

### Post by gear_up on 2007-10-15
The solution proposed by [COLOR="Green"]**landefor**[/COLOR] above DID work for me, on a Gateway Mx7118 laptop.  Thanks!

---

