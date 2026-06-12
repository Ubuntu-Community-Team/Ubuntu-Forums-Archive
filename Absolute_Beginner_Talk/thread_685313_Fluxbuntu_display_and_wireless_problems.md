---
title: "Fluxbuntu display and wireless problems"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by huzzak on 2008-02-02
I am installing fluxbuntu on an older laptop (Dell Latitude CPi) and am having two principle problems.  The first is that the display is not smooth.  It is jagged and pixelated.  When I had DSL on the laptop I had to use frame buffering to fix that, but I can't figure out how to do the same in fluxbuntu.  Any ideas or suggestions?

The second issue is that I can't get the wireless to work.  I have a Netgear WG511T wireless pci card that *seems* to be detected but is listed when I run lshw as being disabled.  Let me see if I can quickly recreate the display:

```
*-network DISABLED
   description: Wireless interface
   product: AR5212/AR5213 Multiprotocol MAC/baseband processor
   vendor: Atheros Communications, Inc.
   physical id: 0
   bus info: pci@0000:01:00.0
   logical name: wifi0
   version: 01
   serial: 00:18:4d:80:d4:af
   width: 32 bits
   clock: 33MHz
   capabilities: bus_master cap_list logical ethernet physical wireless
   configuration: broadcast=yes driver=ath_pci latency=169 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11b
```

So, that seems to be the relevant results of the lshw command.  What ought I do to get this device functioning and connecting to my router?  My router is set to WEP encryption right now, which seems easier to configure than WPA.  Ideally once I get it going I'd like to make it WPA, perhaps with wif-radar?  Thanks for any help you guys can give.

---

### Post by huzzak on 2008-02-02
Okay!  I fixed the problem with the screen being all jagged and pixelated.  I edited the /etc/X11/xorg.conf file so that the Depth under the Screen section was set to 16 instead of 24.  Good times!

I am still hoping for help with getting the wireless card set up and configured to work with WPA encryption.  Thanks dudes!

---

### Post by huzzak on 2008-02-02
Alright!  I installed madwifi and wifi-radar and am so close that I can almost taste it.  Wireless networks are detected and I can see how strong the signal strength is and everything.  Unfortunately I can't manage to connect to my WPA router.  Any suggestions from anybody on how, maybe, I could get that going?

---

