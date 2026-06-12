---
title: "Zyxel M-302 (AR5005VL) Wireless PCI support"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by prashaanth_r on 2007-05-22
Hi there,

I bought this wireless card coz it has an Atheros chipset and since I figured that Atheros is well supported in Ubuntu than any other chipsets. Well, to my luck it seems that one of the chipsets that madwifi does not have HAL support is AR5005VL = AR5513 chipset. I tried looking around but could not find a solution. I tried ndiswrapper but it does not work. 

I compiled the madwifi drivers and $lspci gives:
02:08.0 Ethernet controller: Atheros Communications, Inc. AR5005VL 802.11bg Wireless NIC (rev 01)

But iwconfig does not list my wireless extensions at all. Can somebody help me to find a way to make this card work in Ubuntu? I have lost all hope :(

Thanks
Prashaanth

---

### Post by dstew on 2007-05-22
Looking around, I think that ndiswrapper is your only hope. Are you sure you did everything correctly when you tried it? Did you use the correct ndiswrapper version, and the correct windows driver? What Ubuntu version are you running?

---

### Post by prashaanth_r on 2007-05-22
I am running Ubuntu Edgy Eft. When I installed the driver with ndiswrapper, there were no problems. But when I do iwconfig I cannot find an assigned ath0 for wireless card.

Can anybody send a link for using ndiswrapper, as I can verify whether I did everything right? 

Thanks,
Prashaanth

---

### Post by dstew on 2007-05-23
On the command line, enter```
ndiswrapper -l
```If it is installed correctly, you should get an output like "driver present, hardware present". If you get something else, post it. If your response is ok, do```
modprobe ndiswrapper
```After that, you should get a configurable device in iwconfig, but it might be wlan0, not ath0. Here is an [ndiswrapper link]("http://packages.ubuntu.com/edgy/misc/ndiswrapper-utils-1.8") for the edgy package. You have to install this, and probably ndiswrapper-common. The libc6 and perl packages may already be installed, but if you need to the links for them are there. The README in the installed package will give good instructions. You can also see the ndiswrapper man page```
man ndiswrapper
```

---

### Post by bxb400 on 2007-05-28
Got this card really cheap online and it works great in Feisty Fawn. I did these steps:
- updated to the latest versions of software all around, just in case
- got NDisWrapper using Automatix2, then used it to install the driver (.inf) from the CD that came with the card
- mounted the card in the computer (do not install it before the driver is loaded!)
- opened Network Manager and seen there the card already
- put the card on roaming and did not fill anything in that screen
- the NetworkManager just got active on the top bar, and showed all the networks around (the card is very sensitive, I see twice the number of network vs my laptop!)
- selected my own router and filled-in the "Properties" for my wireless router (I'm using WPA2, if it matters)
No code, no manual edits of files... worked just fine.

---

### Post by ericdfields on 2007-06-17
got pretty close to getting this working, but alas... 32-bit driver only. will not work w/ 64-bit kernel.

---

