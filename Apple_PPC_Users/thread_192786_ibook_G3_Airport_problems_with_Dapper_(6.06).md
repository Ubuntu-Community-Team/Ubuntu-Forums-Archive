---
title: "ibook G3 Airport problems with Dapper (6.06)"
date: 2006-06-09
forum: Apple PPC Users
---

### Post by larseko on 2006-06-09
Hi,

I have a problem getting airport to work properly on my G3 iBook with Airport (NOT Extreme). I think I had it working at some stage, with WEP disabled, but now I don't get it to work. 

The Airport card shows as a wireless connection (eth1) in network admin tool (GNOME), but I cannot make it connect to any network. When I look at the list of available networks, it only shows 2 (sometimes just 1) which I know are some neighbours, but I know there are several others in addition to my own (airport express basestation), as these are visible when running MOSX. 

Do you have any suggestions for what I might be doing wrong, or what I might be missing? As far as I have understood, I do not need fwcutter or anything like that when configuring an ordinary Airport card (remember, not extreme ;))

Here is some useful info (I have tried to arrange it as neatly as possible):
```

$ lsmod
Module                  Size  Used by
ipv6                  323492  6
radeon                136968  1
drm                    90744  2 radeon
rfcomm                 48216  0
l2cap                  28484  5 rfcomm
bluetooth              62148  4 rfcomm,l2cap
ppdev                  11748  0
lp                     13804  0
parport                45936  2 ppdev,lp
cpufreq_userspace       5640  1
cpufreq_stats           6276  0
cpufreq_powersave       1920  0
cpufreq_ondemand        8284  0
cpufreq_conservative     9764  0
md_mod                 89336  0
dm_mod                 69808  1
ieee80211              39784  0
ieee80211_crypt         7136  1 ieee80211
sr_mod                 20100  0
snd_powermac           57920  1
snd_pcm_oss            68480  0
snd_mixer_oss          23072  1 snd_pcm_oss
snd_pcm               109892  2 snd_powermac,snd_pcm_oss
snd_timer              29156  1 snd_pcm
snd                    72532  7 snd_powermac,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11716  1 snd
snd_page_alloc         12424  1 snd_pcm
sbp2                   28068  0
scsi_mod              179588  2 sr_mod,sbp2
apm_emu                 8364  0
af_packet              27080  8
airport                 7808  0
orinoco                47348  1 airport
hermes                  9024  2 airport,orinoco
yenta_socket           33228  0
rsrc_nonstatic         14368  1 yenta_socket
pcmcia_core            51384  2 yenta_socket,rsrc_nonstatic
sungem                 38948  0
sungem_phy             10432  1 sungem
uninorth_agp           11432  1
agpgart                39900  2 drm,uninorth_agp
evdev                  12608  7
tsdev                   9440  0
ext3                  166824  1
jbd                    72436  1 ext3
ohci1394               42868  0
ieee1394              436560  2 sbp2,ohci1394
ohci_hcd               25732  0
usbcore               155136  2 ohci_hcd
ide_cd                 38372  0
cdrom                  49468  2 sr_mod,ide_cd
ide_disk               20800  3
i2c_keywest            11936  0
capability              5352  0
commoncap               8256  1 capability

###############################
ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:0A:95:8F:CF:E6
          inet addr:80.111.12.79  Bcast:255.255.255.255  Mask:255.255.252.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:41 Base address:0xa800

eth1      Link encap:Ethernet  HWaddr 00:10:C6:74:4B:EA
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:57

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1392 (1.3 KiB)  TX bytes:1392 (1.3 KiB)

################################

iwconfig:
:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"Her"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.422 GHz  Access Point: None
          Bit Rate:2 Mb/s   Sensitivity:1/3
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/92  Signal level=134/153  Noise level=134/153
          Rx invalid nwid:0  Rx invalid crypt:114  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


####################################
Some relevant lines from dmesg:


[12320.223524] eth1: no IPv6 routers present
[12726.169286] eth1: New link status: AP Out of Range (0004)
[12730.963972] eth1: New link status: AP In Range (0005)
[12738.970070] eth1: New link status: AP Out of Range (0004)
[12752.263902] eth1: New link status: AP In Range (0005)
[13084.356246] ADDRCONF(NETDEV_UP): eth1: link is not ready
[13465.226714] ADDRCONF(NETDEV_UP): eth1: link is not ready
[13473.987343] ADDRCONF(NETDEV_UP): eth1: link is not ready

####################################
larseko@ubuntulars:~$ iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:03:2F:30:4E:9C
                    ESSID:"TOPCOM"
                    Mode:Master
                    Frequency=2.437 GHz (Channel 6)
                    Signal level:-89 dBm  Noise level:-98 dBm
                    Encryption key:on
          Cell 02 - Address: 00:06:25:5D:CB:DD
                    ESSID:"BAJAN"
                    Mode:Master
                    Frequency=2.462 GHz (Channel 11)
                    Signal level:-87 dBm  Noise level:-94 dBm
                    Encryption key:on



#####################################

```
Thanks in advance for any suggestion.****

---

### Post by talkeetnik on 2006-06-09
My Pismo worked seemlessly with the Dapper install cd.
The Airport (old one) was seen and configured at startup.....
This is the G3 with 500mgz and ATI.....

Have you tried both cd's to test? Some have had varied results.
My initial test was Xubuntu live....It failed to do the job....but then
the Xubuntu install disk saw the Airport and configured it easily....

I realized I have not offered much help but I would try both or disable and reenable the configuration profiles.
Is the built-in NIC card disabled? (I once had trouble with that in an earlier release of Ubuntu PPC)

Good Luck and let us PB users know how it goes....


WHB
Alaska

---

### Post by larseko on 2006-06-09
[QUOTE=talkeetnik]My Pismo worked seemlessly with the Dapper install cd.
The Airport (old one) was seen and configured at startup.....
This is the G3 with 500mgz and ATI.....

Have you tried both cd's to test? Some have had varied results.
My initial test was Xubuntu live....It failed to do the job....but then
the Xubuntu install disk saw the Airport and configured it easily....

I realized I have not offered much help but I would try both or disable and reenable the configuration profiles.
Is the built-in NIC card disabled? (I once had trouble with that in an earlier release of Ubuntu PPC)

Good Luck and let us PB users know how it goes....


WHB
Alaska[/QUOTE]

Hi, thanks for your help. I actually didn't install from the Dapper CD, as that wouldn't work with my partitions (refused to install bootstrap partition), but from an earlier release. 5.10 or something. Then I upgraded. That might bloody well be the problem, as there could be malfunctioning configuration files lying around from the first install.

So I shouldn't expect Airport to work from the live CD without installing?

I have tried disabling/re-enabling eth1 a number of times, and also tried disabling eth0 (onboard ethernet) first etc. (in linux that is), but to no effect.

---

