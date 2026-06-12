---
title: "Trouble with WiFi"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by sylbaris on 2006-10-01
I'm having an incredibly tough time setting up my wifi card.  I followed all of the steps listed [here]("http://www.ubuntuforums.org/showthread.php?t=200375"), and I ran into trouble when it came to aligning the drivers with any of the devices listed.  When I run iwconfig, I get:

[INDENT]lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"The_Batcave"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:C0:49:E6:8B:5C
          Bit Rate:48 Mb/s   Tx-Power:10 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=44/94  Signal level=-51 dBm  Noise level=-95 dBm
          Rx invalid nwid:24704  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.[/INDENT]

which is funny, because I thought that the steps listed in that tutorial resulted in killing ath0 and activating wifi0.  I tried out ndiswrapper -l, and it claims that the driver is present, as is the hardware, but I'm just not getting anything.

I'm really at a loss.  I had been trying to get wifi working on a laptop, but after trying (and failing) a million different things, I thought I'd build a PC with an atheros chipset card because it's more easily supported, only it didn't work so well....

I have a mac, I have a PC, and I'd love to have a linux box, but I'm just not getting anywhere.  Any help you all can provide, I will greatly appreciate!

---

### Post by sylbaris on 2006-10-01
I suppose it would be helpful to tell you what I'm trying to install....sorry, I'm not thinking straight anymore.

It's a DWL-AG530 in what was once a Dell OptiPlex GX110 (Pentium III 733MHz, 256 MB RAM, an NEC 6X DVD-ROM, and a 60 GB drive).  I installed Ubuntu off of the live DVD, and all I've put on there since then is ndiswrapper and the gui for it.

If I neglected to mention anything else, just let me know.  Again, thank you all for taking the time to help me out!

---

### Post by kent41 on 2006-10-02
I am new to Ubuntu so i can't tell if you tried to set up your card by going to System>Administration>Networking.

I HAVE A D-Link DWL-G630 card and that is how I set up my card.

I did not install ndiswrapper or anything else.

---

### Post by sylbaris on 2006-10-03
I guess I really am clueless - after the nightmare I had with the laptop, I never even tried to see if the built-in support accepted the card.  I suppose I'll re-install and try that later tonight.

The ath0 is what it started at, however, and it's still there.  I'm not getting any sort of connection now through the Networking control panel, but it's certainly worth a shot.

Thanks for the response - I'll let you know how it goes!

---

### Post by sylbaris on 2006-10-07
No dice.  I tried reinstalling (and updating), but when I went to change my networking tool over to the ath0, there was no signal.  I looked in the details, and it showed that I was connected to the router, but that's as far as I could get.

Any thoughts?

---

### Post by motstudios on 2006-10-07
well, if im reading ur post right, ur trying to get ur wifi card working.

from what i seen in ur post it appears ath0 is ur wifi cards interface and ur card is using the madwifi driver. i also assume ur routers essid is The_Batcave

if this is so, then try the following and let me know if it works.

open a terminal

iwlist scan ath0
# this should show something showing ur router info on ath0

iwconfig ath0 essid The_Batcave
# this will set your wifi card to connect to The_Batcave

dhclient ath0
# this should get you connected with ur router

that should connect you to ur router if the info i got from ur post was correct. good luck

---

