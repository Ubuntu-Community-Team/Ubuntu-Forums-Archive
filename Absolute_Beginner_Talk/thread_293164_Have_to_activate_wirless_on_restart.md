---
title: "Have to activate wirless on restart"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by Mr. Matt on 2006-11-04
Hey everyone,

This is my first time installing a Linux OS on my personal computer and I'm very excited so far!

One of the initial annoyances I'm seeing is that I have to deactivate and then re-activate my wireless connection from "Networking" when I restart my computer.  What can I do to set it so that it connects automatically?

Note: when I go to "Networking" it says that the "interface wlan0 is active" but I can't connect to the Internet until I deactive and reactive.

I'm using a Netgear MA101 USB adapter if that matters.

Thanks for your help

---

### Post by ReaderRat on 2006-11-04
You might give this a look:
**[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)**

---

### Post by Mr. Matt on 2006-11-04
Yeah I had skimmed through that document but there was no section specifically related to the problem that I have.  Perhaps the solution is in there but I'm not advanced enough to pick it out.

---

### Post by Dual Cortex on 2006-11-04
Hi, right after you restart and log in, go to the command line and type sudo iwconfig, copy and paste the output here... You might be having the same problem I'm having which I still haven't been able to  fix (essid setting not loading up)

---

### Post by Mr. Matt on 2006-11-04
This is what I get:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11-DS  ESSID:"matt"  Nickname:"okuwlan"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:39:49:53:C8
          Bit Rate:11 Mb/s   Tx-Power=15 dBm
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B
          Encryption key:XXXX-XXXX-XXXX-XXXX-XX   Security mode:open
          Power Management:off
          Link Quality=0/0  Signal level=47/255  Noise level=0/0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

---

### Post by Dual Cortex on 2006-11-04
Does everything there seem right to you?
i.e. frequency...


The following seem abnormal:
```
Link Quality=0/0  Signal level=47/255
```

---

### Post by Mr. Matt on 2006-11-04
Yeah I think everything looks alright.  In fact, after I deactivate it and re-activatve and run that command again everything is the same (except the signal level is slightly different).  Perhaps the problem could be that since it's a USB adapter it is not being recognized right away?

---

