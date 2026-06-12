---
title: "Atheros and Madwifi"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by silentsoul on 2007-02-07
I have an atheros Ar5006eg, this card is a PAIN in The Arse! I finally got the mad-wifi drivers working and now I am trying to get kismet to work. I have finally got it configure right but the problem comes with this I get an error.

computer@Xerses:~$ sudo kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
Source 0 (AtherosG): Enabling monitor mode for madwifi_ag source interface wifi0 channel 6...
FATAL: channel get ioctl failed 22:Invalid argument
 
I have googled it but no one's answer works, these 5006eg cards are different than other atheros cards, also in trying to get it to work I found out I have not 1 but TWO wireless connections!

wifi0     no wireless extensions.

ath0      IEEE 802.11b  ESSID:"linksys"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:10:3E:6D:0B
          Bit Rate:11 Mb/s   Tx-Power:17 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=15/94  Signal level=-82 dBm  Noise level=-97 dBm
          Rx invalid nwid:3628  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

ath1      IEEE 802.11b  ESSID:""
          Mode:Monitor  Frequency:2.437 GHz  Access Point: 0A:16:E3:B2:6B:F5
          Bit Rate:0 kb/s   Tx-Power:17 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=15/94  Signal level=-82 dBm  Noise level=-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I have No idea how this happened except for when I was putting in the monitor mode command if anyone has any idea what is going on pleae help. Thank you.

---

### Post by sven_henson on 2007-02-16
Hey...i have the same card, How did u get madwifi working. Can u give me a step by step...i am new to linux and some of this stuff can be a little confusing.

SVEN

---

### Post by athleticbum32 on 2007-04-18
[http://ubuntuforums.org/showpost.php?p=1679885&postcount=2](http://ubuntuforums.org/showpost.php?p=1679885&postcount=2)

---

### Post by joenjeru on 2007-09-11
Got my Atheros AR5006EG on my Toshiba A200 to work by following the instructions on [http://madwifi.org/wiki/UserDocs/kismet](http://madwifi.org/wiki/UserDocs/kismet)

Ensure you use the latest svn version.

---

