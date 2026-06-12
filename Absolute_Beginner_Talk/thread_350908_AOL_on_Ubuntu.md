---
title: "AOL on Ubuntu?"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by Devilled on 2007-02-01
My current ISP is AOL (I know, I know - but I don't use their 'My First Internet' software, just the unlimited broadband connection which is the best available in my area of the UK).

When I installed Ubuntu, Edgy quickly found and accepted my connection, and I've been online without problem since the first boot.  However, I have a technical question for AOL about their wireless set-up which I can only ask from *within* the AOL software (i.e. keyword: Help)  

Is there a version of AOL for Ubuntu?  A Google search found PengAOL, but it appeared to be RPM based.

AND/OR does anyone know of a good independent AOL help forum or group on which I could ask my tech question?

Many thanks

Devilled

---

### Post by Brunellus on 2007-02-01
you're asking the wrong question.  Why not ask a technical question about wireless set-up here? 

Or is your connection to AOL wireless in the first place--that, is not over a phone cable or CATV or fiber optics?

---

### Post by Devilled on 2007-02-01
OK - here's my question:

I have AOL Platinum, which came with the Netgear DG834G wireless router.  Everything is set up and running fine on my computer (the main PC in the house, connected to DSL via the phone cable), but now I want to enable wireless networking so that I can connect a computer in another room.

However, when I run the wireless set-up program from the AOL disc, I can only get as far as trying to find the other PC.  Because the other PC has a wireless adapter that isn't listed in the AOL set-up (Belkin F5D7050, which has worked wonderfully with previous wireless connections), the set-up process ends.

I'm pretty sure that, if I can simply switch on the wireless signal from the router, I can play with the settings on the Belkin adapter on the other PC and find the signal - but I can't start broadcasting the signal as set-up will not complete.

Is there a way to switch on the wireless signal to enable me to do this?

Any help would be greatly appreciated.

Devilled

---

### Post by Brunellus on 2007-02-01
> **Devilled said:**
> OK - here's my question:

I have AOL Platinum, which came with the Netgear DG834G wireless router.  Everything is set up and running fine on my computer (the main PC in the house, connected to DSL via the phone cable), but now I want to enable wireless networking so that I can connect a computer in another room.

However, when I run the wireless set-up program from the AOL disc, I can only get as far as trying to find the other PC.  Because the other PC has a wireless adapter that isn't listed in the AOL set-up (Belkin F5D7050, which has worked wonderfully with previous wireless connections), the set-up process ends.

I'm pretty sure that, if I can simply switch on the wireless signal from the router, I can play with the settings on the Belkin adapter on the other PC and find the signal - but I can't start broadcasting the signal as set-up will not complete.

Is there a way to switch on the wireless signal to enable me to do this?

Any help would be greatly appreciated.

Devilled
"wireless set up program"?  in what operating system?

If your wlan card is supported by Ubuntu, you should be able to find the wireless network in your house from within Ubuntu without recourse to any AOL cds.  80211.x wireless networking is an industry standard (and one of the few that's actually standard!).  Unless AOL is doing some freaky proprietary voodoo with their routers, I don't see why you *have* to use their setup cd.

---

### Post by TrendyDark on 2007-02-01
If your other computer is running windows, you're in luck. Just hard wire your ubuntu computer into the wireless router, then the router to your modem.

Following me so far?

Okay. Hit the reset button on your modem (very tiny in most cases). Once it reboots, make sure you can get online on your hard-wired machine. Then open Firefox and goto 192.168.0.1 and you should be able to edit the settings there (I.E. Turning on the wireless features, naming the wireless network, etc.). Then goto your other machine and goto Network Connections, find your wireless connection (should be disabled). Then, if in windows, try to use the windows utility to find wireless networks (can't remember where to find it, but it's simple and straight forward). Find the network o nthe list with the name you have given it and there you go.

---

### Post by HomerSimpson748 on 2007-02-01
I would recommend bypassing any software that was included for setup. If you know the IP address, username & password of the router you can administer it via your web browser by typing the IP address in the location bar. Networking is a lot to take in at first, but its actually really easy.

---

