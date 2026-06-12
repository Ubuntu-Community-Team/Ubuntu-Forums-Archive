---
title: "wireless constently at 3 kb/s"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by c0d4041292 on 2008-04-02
my title basically says it, is there a way i can see what is using this bandwidth and if i can possibly stop it

---

### Post by Crafty Kisses on 2008-04-02
> **c0d4041292 said:**
> my title basically says it, is there a way i can see what is using this bandwidth and if i can possibly stop it

Hmmm, do the following ```
netstat
``` See what you're connected to.

---

### Post by c0d4041292 on 2008-04-02
that posted a long list

i am using the beta if that has anything to do with it....should i go to the 8.04 forums for this?

---

### Post by Crafty Kisses on 2008-04-02
> **c0d4041292 said:**
> that posted a long list

i am using the beta if that has anything to do with it....should i go to the 8.04 forums for this?

Possibly, but is this only on Wireless, when you're using eth0 is it the same results?

---

### Post by c0d4041292 on 2008-04-02
i would not know about Ethernet hence i havnt used that since install so yes its on wireless thats its doing this

---

### Post by Crafty Kisses on 2008-04-02
> **c0d4041292 said:**
> i would not know about Ethernet hence i havnt used that since install so yes its on wireless thats its doing this

What kind of Wireless router do you have, and also what is your Wireless card?

---

### Post by c0d4041292 on 2008-04-02
linksys router and i dont know what kinda of wireless card

---

### Post by Crafty Kisses on 2008-04-02
Post the following output:
```
iwconfig
```

---

### Post by c0d4041292 on 2008-04-02
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"redskins"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:10:95:7B:0A   
          Bit Rate:12 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=27/70  Signal level=-67 dBm  Noise level=-94 dBm
          Rx invalid nwid:57896  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by c0d4041292 on 2008-04-02
how do i make it so it dont have smileys in it, like the code button or something

---

### Post by Crafty Kisses on 2008-04-02
> **c0d4041292 said:**
> lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"redskins"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:10:95:7B:0A   
          Bit Rate:12 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=27/70  Signal level=-67 dBm  Noise level=-94 dBm
          Rx invalid nwid:57896  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

It would appear that you're not getting a good signal.

---

### Post by c0d4041292 on 2008-04-02
well i am up a floor and across the house from my router but low sig cant cause constant bandwith usage.....can it???

---

### Post by Crafty Kisses on 2008-04-02
> **c0d4041292 said:**
> well i am up a floor and across the house from my router but low sig cant cause constant bandwith usage.....can it???

Not sure, can you post the following output of ```
netstat
``` Also is your router encrypted?

---

