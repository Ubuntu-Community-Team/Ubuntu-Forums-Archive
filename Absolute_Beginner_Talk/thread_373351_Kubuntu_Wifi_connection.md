---
title: "Kubuntu Wifi connection"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by bkthiess on 2007-03-01
I changed from Ubuntu to Kubuntu yesterday.  My wifi card used to work in ubuntu.

When I installed Kubuntu I let it go all night.  My wife wandered in while I was at work and jumped on the internet through Konquerer (she really like it, btw).  When I got home, I opened up the WLAN assistant, picked out my ssid, filled out all the security info, and told it to connect.  It kept returning the error "cannot establish connection" and told me to verify my security settings, which I did.  I checked and double checked all the info, booted into windows to verify the info on my router, and booted back into K.  No luck.  No internet connection at all now.  I don't know how she got on before, but it is gone now.  Any ideas?

K/Ubuntu has been fun and is a good looking system, but these wifi problems have just about vexed me into getting the whole thing off my system.

---

### Post by Kobalt on 2007-03-01
Which version of Kubuntu do you curently run ?
What is the model of your wifi card and optionaly, could you post here the output of the following command line : 
```
iwconfig
```

---

### Post by bkthiess on 2007-03-01
I got home from work and it is picking up a signal, but it's riding on my neighbor's bandwidth.  Not my own network.  I'm afraid to mess with it, or I'll get nothing again.  

So now I know it works on an open connection.

iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"linksys"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:F8:DE:E0:B3
          Bit Rate:5.5 Mb/s   Sensitivity:1/3
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=1/92  Signal level=-88 dBm  Noise level=-89 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:75
          Tx excessive retries:31  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


THanks for the help!

---

