---
title: "Problems with wierless internet  card"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by flyturkish on 2008-04-21
Hello I installed Ubuntu 8.04 using Wubi witch works quiet well on my Fujitsu Siemens Esprimo Mobile (EM V5535) laptop for the first time ever I have never used Linux before .

First Some hardware is not recognized I can not connect to the Internet
 had a look in the Hardware Drivers application and it says

theros hardware access layer (HAL) 

and the

Atheros 802.11 wireless lan cards 

are not supported or so .


I would be cool if some one could help me to fix this ! 

hanks flyturkish

---

### Post by skymera on 2008-04-21
Type iwconfig in the terminal.
It should show some information on wireless.
Typically wlan0

---

### Post by flyturkish on 2008-04-21
Hello I've tried it and I get 

lo            no wireless extensions

etho       no wireless extensions

not really sure what I can do :confused:

---

### Post by Michael.Godawski on 2008-04-21
It would be good to know what your wireless device actually is. Please post the output of the terminal command::

```
sudo lshw -C network
```

---

### Post by flyturkish on 2008-04-21
Hello mate done it see below 



ogical name: eth0

       version: 02

       serial: 00:1e:33:03:31:0f

       size: 10MB/s

       capacity: 100MB/s

       width: 32 bits

       clock: 33MHz

       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.2 duplex=half latency=0 link=no module=sis190 multicast=yes port=MII speed=10MB/s

  *-network UNCLAIMED

       description: Ethernet controller

       product: AR242x 802.11abg Wireless PCI Express Adapter

       vendor: Atheros Communications Inc.

       physical id: 0

       bus info: pci@0000:02:00.0

       version: 01

       width: 64 bits

       clock: 33MHz

       capabilities: pm msi pciexpress msix cap_list

       configuration: latency=0

---

### Post by thatsPipe on 2008-04-22
I just got a new laptop the other day (Toshiba Satellite A215-S5837) and I'm encountering the same problem. The Restricted Driver Manager shows:

[INDENT][LIST]
[*]Atheros Hardware Access Layer (HAL)
[*]Support for Atheros 802.11 wireless LAN cards
[/LIST][/INDENT]

Both are checked, so they should be enabled. However, doing 'sudo lshw -C network' outputs: 

  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:14:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0

So, I'm in the same corner as flyturkish. I'm about to try the ndiswrapper but does anyone have any idea what might be going on? bug in the driver or something else?

---

### Post by linuxmad on 2008-04-28
> I just got a new laptop the other day (Toshiba Satellite A215-S5837) and I'm encountering the same problem. The Restricted Driver Manager shows:

        * Atheros Hardware Access Layer (HAL)
        * Support for Atheros 802.11 wireless LAN cards

Both are checked, so they should be
Same thing here with a  Fujitsu-Siemens Esprimo Mobile v5535. I have ethernet  card working, I am able to fn+f1 to activate the wireless conection (the light turns on) but still net manager is not able to find any network.. NO WIRELESS :( Any solution??
Thanks

ps: I forget to mention.. this is an wubi installation. Not sure if it matters?

---

### Post by flyturkish on 2008-04-28
Hello I downloaded ubuntu 8.04 and burned the ISO file and used it as a live CD and there are still all the problems I had when I did it the first time with wubi . No wifi and I can not change the resolution .


[http://gentoo-wiki.com/HARDWARE_Fujitsu-Siemens_Esprimo_Mobile_V5535](http://gentoo-wiki.com/HARDWARE_Fujitsu-Siemens_Esprimo_Mobile_V5535)

---

### Post by lemming465 on 2008-04-28
The AR2425 chipset isn't supported very well yet; see the [official ubuntu bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/182489").

---

### Post by picbits on 2008-04-29
I have exactly the same laptop and its working perfectly on Wireless.

Have a look here:

[http://ubuntuforums.org/showthread.php?t=766529&highlight=atheros](http://ubuntuforums.org/showthread.php?t=766529&highlight=atheros)

---

### Post by rossjp on 2008-06-08
@thatsPipe

I was trying for about a week to get wireless installed on the exact same Toshiba A215-S5837 you are using.  I tried about 10 different driver/OS setups and none of them fully worked.  I would be able to attach the driver to the wifi card but could never see any networks in my Network Manager, nor could I connect to any network I tried to manually configure.....

And then I found the switch.  There is a little wireless on/off switch on the bottom of the front of the exterior of the computer, in a not-so-intuitive spot.  I flipped that little switch and now the native linux drivers (from madwifi) work perfectly on 32-bit 8.04 Hardy. 

You will have to update the drivers though.  I used the guide here:

[URL="http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html"]http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html
[/URL]

But I used this driver snapshot instead of the one used in the guide.
[http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz]("http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz")

Good luck.

---

### Post by rossjp on 2008-06-09
Should mention that I also had to add ath_hal to modprobe in order for the wireless to work after reboot.  

```
sudo modprobe ath_hal
```

---

