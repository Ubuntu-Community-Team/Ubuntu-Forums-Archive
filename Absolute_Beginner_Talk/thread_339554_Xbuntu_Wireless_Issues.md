---
title: "Xbuntu Wireless Issues"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by Real Newbie on 2007-01-15
Greetings All,

I am setting up an old laptop that I used in Grad school for my 13 year old. He needs to browse the internet and do light word processing for school.

The laptop is an old Gateway Solo 2300, 150 Pentium MMX, 160 MB RAM, 20 GB HD. The wireless card is a Proxim 8480-WD. I  loaded Ubuntu and it was just too much for the old machine. I tried DSL and I couldn't get my USB or wireless to work. Puppy warned that they did not do wireless well and that turned out to be true. I tried MEPIS and that auto detected everything well except for the wireless card. I tried for several weeks to get it to work and have officially given up. I have Ubuntu on an old Intel Nightshade server and am having fun playing with it so I decided to try Xbuntu on the old laptop. It took 4 install attempts to get it right. I had to fiddle with it awhile to get the screen setting close to right. Now it is time to tackle the wireless card. I have the following info.

```
kelly@xbuntu:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 430TX - 82439TX MTXC (rev 01)
0000:00:01.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 01)
0000:00:01.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:01.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:01.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 01)
0000:00:02.0 VGA compatible controller: Neomagic Corporation NM2093 [MagicGraph 128ZV] (rev 02)
0000:00:0a.0 CardBus bridge: Cirrus Logic PD 6832 PCMCIA/CardBus Ctrlr (rev c1)
0000:00:0a.1 CardBus bridge: Cirrus Logic PD 6832 PCMCIA/CardBus Ctrlr (rev c1)
0000:01:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
kelly@xbuntu:~$ iwconfig
lo        no wireless extensions.

ath0      IEEE 802.11  ESSID:"linksys"
          Mode:Managed  Frequency:2.452 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

kelly@xbuntu:~$ ifup ath0
ifup: failed to open statefile /var/run/network/ifstate: Permission denied
kelly@xbuntu:~$
```

I see one problem right off the bat. I have a Linksys B wireless router. It is on channel 6 which is 2.442 GHz not 2.452. This was all of the same "stuff" that I was getting with MEPIS. Even after I changed the frequency, I still could not connect.

Questions
1)How do I change the frequency in Xbuntu?
2)Does anything stand out as wrong except for the frequency?

I am a real noob and am just having a little fun learning LINUX, so please make any suggestions as basic and step by step and complete as possible.

Thanks in advance for any and all help.

Noob

---

### Post by teitunge on 2007-01-21
As my English is crap, and I really want to help I will just give it a shot.

iwlist <device> frequency will give you a list over the different channels and frequencies...
maybe that could point in the right direction?

you could also try to use sudo in front of your commends, since you got permission denied on one of them?

sudo will make you superuser.

Sorry if this doesnt help you.

---

