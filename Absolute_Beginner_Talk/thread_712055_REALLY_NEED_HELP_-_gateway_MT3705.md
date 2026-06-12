---
title: "REALLY NEED HELP - gateway MT3705"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by thisismalhotra on 2008-03-01
Hi All,

I know there have been a lot of post about MT3705 etc etc but I have some different problems. I have following issues. 

1. My wifi card is eanbled and I can see it working, I have wpa_suplicant installed too but I cannot have WPA Personal option in my network manager.
Pls Help.

2. My sound was not working so I compiled latest version of ALSA mixer now sound is working but it is really low and has a very high bass by default so the sound really BAD and noisy and speaker flats out.

3. THIS IS MAJOR MY UBUNTU INSTALLATION IS REALLY SLOW, it takes good 40 - 50 secs to boot up and EVERYTHING IS REALLY SLOW.

I dont know if this wud help but below is my lspci enteris

```
lspci
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
08:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
```

Also I feel there is something wrong with my interfaces file as I just have these entries in it..

```
auto lo
iface lo inet loopback
wireless mode managed
```

I have tried instructions here but did not work..

[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

---

### Post by mikeyphi on 2008-03-01
A shot in the dark!
Open Networks and post the first two lines under the 'hosts' tab - the ones that start "127"

---

### Post by thisismalhotra on 2008-03-01
IP Address               Aliases
127.0.0.1                  localhost
127.0.1.1                  gaurav-ubuntu

Also, anything below it says IP6, shud that matter

---

### Post by Shoadow56 on 2008-03-01
As for sound, I followed the directions in this post to get my sound working. I'm running Ubuntu 7.10 with standard upgrades on an MT3705 with Amarock player.

[http://ubuntuforums.org/showthread.php?t=710343&highlight=mt3705]("http://ubuntuforums.org/showthread.php?t=710343&highlight=mt3705")

---

### Post by thisismalhotra on 2008-03-01
> **Shoadow56 said:**
> As for sound, I followed the directions in this post to get my sound working. I'm running Ubuntu 7.10 with standard upgrades on an MT3705 with Amarock player.

[http://ubuntuforums.org/showthread.php?t=710343&highlight=mt3705]("http://ubuntuforums.org/showthread.php?t=710343&highlight=mt3705")

Thanks I will try this and let you know ... since you also have MT 3705 is ubuntu really slow on your PC too. I have it dual booted with XP, but I have upgraded RAM to 2 gig. Also, I have 1.0.16 for ALSA....

Did you try enabling WPA personal on you PC for wireless, if no can you try and tell me if it works or not.:KS

---

### Post by thisismalhotra on 2008-03-02
Guys any more help please ... Dont know why my ubuntu is dead slow...

---

### Post by thisismalhotra on 2008-03-03
hey All, 

Any tips are appreciated please I need a good/fast working ubuntu on my laptop ....THANKS

---

