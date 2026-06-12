---
title: "can't get it to work DWL G650!"
date: 2006-07-01
forum: Absolute Beginner Talk
---

### Post by dawandeh on 2006-07-01
hey guys!

this is driving me nuts! i'm a complete linux newbie, ubuntu seems to me pretty awesome, but this wireless thing is really a pain...
my notebook has a broadcom 4306 wireless card....i tried for a week to get it working...searching the user forum...etc, etc...
so i thought browsing the forum the dwl 650 would maybe work out of the box...
..but one more time i was not lucky:-(
....as i am a complete beginner i can't really tell whats wrong...
ifconfig tells me:
ath0      IEEE 802.11g  ESSID:"tha baba net"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:7C:41:27:00
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:40  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

question:is my card working?
question: no WPA support??? not possible to connect to WPA networks in linux?
this is my friends network(WPA)...he turned WPA off to give me a try.however i could not connect...
any information is appreciated
tnx
dawandeh

---

### Post by vierranet on 2006-07-01
[QUOTE=dawandeh]hey guys!

this is driving me nuts! i'm a complete linux newbie, ubuntu seems to me pretty awesome, but this wireless thing is really a pain...
my notebook has a broadcom 4306 wireless card....i tried for a week to get it working...searching the user forum...etc, etc...
so i thought browsing the forum the dwl 650 would maybe work out of the box...
..but one more time i was not lucky:-(
....as i am a complete beginner i can't really tell whats wrong...
ifconfig tells me:
ath0      IEEE 802.11g  ESSID:"tha baba net"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:7C:41:27:00
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:40  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

question:is my card working?
question: no WPA support??? not possible to connect to WPA networks in linux?
this is my friends network(WPA)...he turned WPA off to give me a try.however i could not connect...
any information is appreciated
tnx
dawandeh[/QUOTE]

Check out: 

[https://www.fsf.org/resources/hw/net/wireless/cards.html](https://www.fsf.org/resources/hw/net/wireless/cards.html)
or [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)
or [http://users.linpro.no/janl/hardware/wifi.html](http://users.linpro.no/janl/hardware/wifi.html)

Hope it helps.

---

### Post by vierranet on 2006-07-01
The GPL Driver for the broadcom 43XX wireless card is at:

[http://bcm43xx.berlios.de/?go=Home](http://bcm43xx.berlios.de/?go=Home)

---

