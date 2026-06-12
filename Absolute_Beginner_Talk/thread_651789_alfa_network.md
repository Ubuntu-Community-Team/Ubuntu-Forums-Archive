---
title: "alfa network"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by ralphz on 2007-12-27
HI

I recently bought Alfa Detwork wireless card (awus036h) mainly to do some wardriveing in my neighborhood. I went to aircrack-ng wiki and downloaded the [driver]("http://www.aircrack-ng.org/doku.php?id=r8187") and installed successfully.  

I configured successfully kismet and aircrack-ng works fine with the card (after killing NetworkManager) but i can't associate to any network with this card!

When i use:

iwconfig wlan1 essid YYYY key XXXXXXXXXXXXXXXXXXXXXXXXXX

i always get

wlan1     802.11b/g link..  ESSID:"YYYY"  
          Mode:Managed  Channel=6  Access Point: Not-Associated   
          Bit Rate=11 Mb/s   Tx-Power=5 dBm   
          Retry:on   Fragment thr:off
          Encryption key:XXXX-XXXX-XXXX-XXXX-XXXX-XXXX-XX   Security mode:open
          Link Quality=89/100  Signal level=-212 dBm  Noise level=-245 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

same command for my laptop's internal wireless card associates me to the access point without problem. Does anyone know what i have missed?

Thanks
Ralph

---

