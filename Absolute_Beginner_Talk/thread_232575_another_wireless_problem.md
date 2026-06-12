---
title: "another wireless problem"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by chopper81 on 2006-08-08
I have finally got to the point to when I put in iwconfig I get the following results:
lo no wireless extensions
etho no wireless extensions
wlano IEEE 802.11g ESSID:off/any
Mode:Managed Frequency 2.412 Ghz Access Point 00:00:00:00:00:00
Bit Rate:54 Mb/s   Tx-Power 25dBm
Power Management:off
Link Quality:100/100  Signal Level:-72 dBm Noise Level:-256 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

Sito no wireless

OK. Does this now mean, since I still can not conect, that I need to reconfigure my wireless router to accept all of this (the laptop), or is there more that I need to do to configure my wireless to work? Any help would be GREAT.
chopper81

---

### Post by jpkotta on 2006-08-08
First, run this command:```
sudo iwlist eth1 scan
```

You should see your access point and a bunch of information about it.  Look for "ESSID".  Take the string there and run
```
sudo iwconfig eth1 essid <essid>
``` where <essid> is whatever the iwlist command gave.

Example:
```

[jpkotta@goedel ~](0)$ sudo iwlist eth1 scan
          Cell 04 - Address: 00:15:05:29:CC:29
                    ESSID:"ACTIONTEC"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:9
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 22 24 36 48 54 
                    Quality=98/100  Signal level=-81 dBm  
                    Extra: Last beacon: 8476ms ago
[jpkotta@goedel ~](0)$ sudo iwconfig eth1 essid ACTIONTEC

```

---

### Post by chopper81 on 2006-08-08
Ok. I did this and nothing really happened. I saw the info that you said to look for and entered the lines as stated.After the sudo iwconfig wlan0 essid <......> nothing happened. The terminal just returned to the next line with no changes in connectivity.
chopper81

---

### Post by jpkotta on 2006-08-09
Is there a reason that you're not using the gui?  That might be easier.  You can get to it with network-admin.  Anyway, after entering the ESSID, the output of iwconfig should have shown the ESSID and said associated.  If it didn't, then that's a problem.

---

