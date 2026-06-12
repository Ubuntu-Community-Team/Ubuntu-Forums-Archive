---
title: "No wireless in Edgy"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by meat on 2007-02-04
I just installed Ubuntu 6.10 on my T21 thinkpad with a Orinoco Gold PCMCIA wireless card and although I get a signal, it says the wireless is disconnected.  The wireless is enabled and I have entered the correct ESSID and key, but it will not work.  When I type iwconfig, I get the following:

```
eth1      IEEE 802.11b  ESSID:"mlb_wireless"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:16:B6:B8:E1:0D   
          Bit Rate:11 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=62/92  Signal level=-32 dBm  Noise level=-94 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

I got this card, because they were supposed to work out of the box, yet it does not.

Thanks

---

### Post by rogue302 on 2007-02-04
have you tried using a linux driver?

---

### Post by meat on 2007-02-04
no, i have not.  how do i do that?  If i have a signal, isn't it being reognized though?

---

### Post by Sugar on 2007-02-04
I would install network manager, run synaptic and search for network manager, that did the trick for me. Log out and in again, and you will have a new icon next to the clock

Good luck
/Sugar

---

### Post by meat on 2007-02-04
I installed Network manager and now I have 2 icons next to my clock.  One is the wired network and one is the wireless.  The wireless one did work after I installed network manager, but after I rebooted, it says disconnected again.

---

### Post by al7kz on 2007-02-22
edit

---

