---
title: "Stupidly lost internet connection help!"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by calvinthomas on 2006-10-05
Hi, I've just done a stupid thing and lost my internet connection, instead of sensibly checking what I was installing I accidently installed eagle-usb and eagle-usb utils thinking they were part of eagle pcb software, then even more stupidly didn't pay any attention and kept hitting enter on these blue screens.... Now i've lost my internet connection! I have tried resetting up my internet (wireless broadcom 4318) as I do always and it seems set up fine but I can't access the internet. I have deleted the eagle usb & eagle usb utils but it has retained the silly settings I put in! Is there a way I can fix this? (and I promise i'll try not to be as stupid again!)

Calv

---

### Post by calvinthomas on 2006-10-05
Some extra info, it seems I have a loopback device installed, how can I remove this or at least tell it not to use it? My machine still finds the ip address correctly of my wireless card, just I can't use it

Calv

---

### Post by calvinthomas on 2006-10-05
Sorry,I don't think the loopback device is the problem, as a solution that would probably work, is there any way I can completely remove everything relating to the internet so it removes all settings and then I could start again? (Without formatting that is, I only did that a few days ago!)

Calv

---

### Post by calvinthomas on 2006-10-05
Sorry, just trying to give as much information as possible, I get an inet, a Bcast and a Mask from ifconfig for my wireless connection.

I also have link quaity 100/100, a signal level: -51dBm and a noise level: -256dBm from my wireless connection

So i'm certain that is setup correctly! 

Also if I try ping to my router that works! I just have no connection

Calv

---

### Post by calvinthomas on 2006-10-05
Can nobody solve my problem? :'(

I have another update that may help, in /etc I found a folder called eagle-usb that contains several text files, a conf file and soe script typ files. I think what is happening is that my iternet is pointed at these, i.e. from here, I don't think just deleting these will fix it because then it will point nowhere and don't want to do that unless its going to help, is there a way I can get it back to pointing at my wireless connection i.e. eth1?

Calv

---

### Post by shanix on 2006-10-05
hi, it might be useful if you post the config file from /etc/networking/ and the lsmod -l. which will tell us what do u load to the kernal.

- I am a beginner too, I hope that's the right suggestion.

---

### Post by calvinthomas on 2006-10-05
I'm so pleased to get a response! I'll do that right now! I'm going out of my mind, I had my machine perfect finally and then I made that stupid mistake and thought i'm gonna have to format again (that'd be the fifth time!)

Config file (or interfaces thats all I have in there) except for four folders if-down.d, if-post-down.d, if-pre-up.d, if-up.d:


```
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0
auto lo

iface eth1 inet dhcp
wireless-essid linksys

auto eth1

iface eth0 inet dhcp
```

I know for certain my wireless is eth1.

I'm not 100% sure I did the second command right, I think it was LSMOD -L (not in caps) that you wanted me to do, the straight line could be a capital I, I thought:

When I do lsmod -l I get:

```
Usage: lsmod
```

Calv

---

### Post by calvinthomas on 2006-10-05
Just lsmod instead of lsmod -l gives:

```
Module                  Size  Used by
fglrx                 399916  69
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              50020  4 rfcomm,l2cap
ppdev                   9220  0
powernow_k8            12680  0
cpufreq_userspace       4696  1
cpufreq_stats           5636  0
freq_table              4740  2 powernow_k8,cpufreq_stats
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
ipv6                  265728  14
sg                     37920  0
sd_mod                 19984  1
af_packet              22920  4
dm_mod                 58936  1
md_mod                 72532  0
cdemu                  10764  0
ndiswrapper           177364  0
sr_mod                 16932  0
sbp2                   24196  0
lp                     11844  0
joydev                 10048  0
parport_pc             35780  1
pcmcia                 40508  0
parport                36296  3 ppdev,lp,parport_pc
tsdev                   8000  0
irda                  187068  0
psmouse                36100  0
crc_ccitt               2304  1 irda
pcspkr                  2180  0
serio_raw               7300  0
rtc                    13492  0
snd_atiixp             19724  0
snd_atiixp_modem       16136  0
snd_ac97_codec         93216  2 snd_atiixp,snd_atiixp_modem
snd_ac97_bus            2304  1 snd_ac97_codec
usb_storage            74304  1
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
usbhid                 39904  0
snd_pcm                89864  4 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
scsi_mod              139496  5 sg,sd_mod,sr_mod,sbp2,usb_storage
yenta_socket           28428  1
rsrc_nonstatic         13440  1 yenta_socket
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
tg3                   101764  0
snd                    55268  7 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  3 snd_atiixp,snd_atiixp_modem,snd_pcm
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
ati_agp                 9100  0
agpgart                34888  2 fglrx,ati_agp
evdev                   9856  2
ext3                  135816  1
jbd                    58772  1 ext3
ide_generic             1536  0
ehci_hcd               34184  0
ohci_hcd               21892  0
ohci1394               35124  0
ieee1394              299832  2 sbp2,ohci1394
usbcore               130820  6 ndiswrapper,usb_storage,usbhid,ehci_hcd,ohci_hcd
ide_cd                 33028  0
cdrom                  38560  3 cdemu,sr_mod,ide_cd
ide_disk               17664  3
generic                 5124  0
atiixp                  6800  1
thermal                13576  3
processor              23360  2 powernow_k8,thermal
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

I'm a bit concerned about ndswrapper in usb as I connect via a wireless connection to a router! I don't really know if thats a problem, actually I just don't really know much at all!

---

### Post by calvinthomas on 2006-10-05
As some extra information again: I can also not connect via a wired connection. This is annoying.

Calv

---

### Post by calvinthomas on 2006-10-05
Final information I can think of to give and I think may possibly be important:

When I run sudo /etc/init.d/networking restart I get this (i've highlighted the bit I think might be important)

```
 * Reconfiguring network interfaces...                                          /etc/resolvconf/update.d/libc: Warning: /etc/resolv.conf is not a symbolic link to /etc/resolvconf/run/resolv.conf
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:14:a4:5d:3f:67
Sending on   LPF/eth1/00:14:a4:5d:3f:67
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.1 port 67
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:14:a4:5d:3f:67
Sending on   LPF/eth1/00:14:a4:5d:3f:67
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
**/etc/resolvconf/update.d/libc: Warning: /etc/resolv.conf is not a symbolic link to /etc/resolvconf/run/resolv.conf**
bound to 192.168.1.105 -- renewal in 41329 seconds.
```

Calv

---

### Post by Frak on 2006-10-05
Change lo to wlan0.

---

### Post by calvinthomas on 2006-10-05
Doing that gives me this:

```
*configuring nework interfaces
SIOCSIFADDR: No such devices
wlan0: ERROR while getting interace flag: No such device
wlan0: ERROR while getting interace flag: No such device
Failed to bring up wlan0
```

Any more ideas?

---

### Post by 3rr0r on 2006-10-05
it might be listed as wlan1 or wlan2 now.  Check your wireless settings and configurations to see what exactly your pc sees

---

### Post by xpod on 2006-10-05
You would probably have had it all set up again by now if you had just started from scratch..;) 

I too have re-installed numerous times just cause i did`nt know enough to overcome the mess i no doubt created....
Ive got the whole install procedure including all personal preferences,app`s,extensions etc down to just over an hour..
Sure beats banging the head when you dont get no joy elsewhere...

Of course it`s better to persist but sometimes it`s just easier to take the "easy" option:mrgreen: 

Good luck

---

### Post by calvinthomas on 2006-10-05
Yea, I know what you mean. I could of done it probably by now, but its getting rediculous reformatting every 5minutes because of doing something stupid, this is where a rollback function would be useful (my backup errored out aswell to make thing even worse!)

BTW to set-up I reckon would take me about 8hrs still. I have created no scripts to help though (which I should) and also I tweak the interface a fair amount and spend ages getting it just right! Thats why i'm so peeved about the thought of reformatting again.

I don't really understand how on an OS as stable and configurable as Ubuntu, installing one wrong modem and blindly pressing enter for its settings can't be reversed! (I know it was an idiotic thing to do but still!) It is one of the reasons to switch from windows that things can be fixed without needing to reformat. Grrrrr!!

Calv

---

### Post by calvinthomas on 2006-10-05
> **3rr0r said:**
> it might be listed as wlan1 or wlan2 now.  Check your wireless settings and configurations to see what exactly your pc sees

My PC says my wireless is on eth1, I don't know how to check anyting else other than ifconfig, iwconfig etc they both put my wireless on eth1, is that what you mean?

Secondly, wlan1 & wlan2 both fail

Calv

---

### Post by calvinthomas on 2006-10-05
Seriously now, would it be quicker and easier for me to format or is this solvable?

Calv

---

### Post by calvinthomas on 2006-10-05
OK final thing I can give then i'm going to go to bed and pray a solution has arrived when I next come to my computer, I feel this could be useful info:

I typed dmesg | tail -n 6

and got this output:

```
17180046.312000] ndiswrapper: using irq 177
[17180047.476000] wlan0: vendor: ''
[17180047.476000] wlan0: ndiswrapper ethernet device 00:14:a4:5d:3f:67 using driver bcmwl5, 14E4:4318.5.conf
[17180047.476000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[17180051.308000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17180058.812000] eth1: no IPv6 routers present
```

and also I figured i'd try once more to reinstall my wireless the way I normally do i.e. via the brodco 4318 guide on here and now my /etc/network/interfaces file only says this:

```
iface lo inet loopback
auto lo
```

I don't know if that is right but I didn't get any errors on the install.

Sorry for being such a nightmare over this.

Calv

Calv

---

