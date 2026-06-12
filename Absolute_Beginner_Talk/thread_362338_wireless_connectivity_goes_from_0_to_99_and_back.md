---
title: "wireless connectivity goes from 0 to 99 and back"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by charles.g.moore on 2007-02-15
My wireless connection keeps going from 0-99 connected and back
The network uses 128 WEP
if I ping anything I lose 50% of the packets

any ideas?

---

### Post by ukripper on 2007-02-16
> **charles.g.moore said:**
> My wireless connection keeps going from 0-99 connected and back
The network uses 128 WEP
if I ping anything I lose 50% of the packets

any ideas?

Are you using static ip address or auto DHCP?

---

### Post by charles.g.moore on 2007-02-16
Auto DHCP

---

### Post by ukripper on 2007-02-19
> **charles.g.moore said:**
> Auto DHCP

paste iwconfig here

---

### Post by charles.g.moore on 2007-02-19
charles@charles-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:16 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:549   Missed beacon:0

sit0      no wireless extensions.

vmnet8    no wireless extensions.

vmnet1    no wireless extensions.

I have had to plug straight into the wireless router in order to get a reliable connection.
If wired in I have no problems with connectivity.

I know that here at work they use a 128 bit WEP encryption in ASCII mode.  I dont know if that matters.

---

### Post by ukripper on 2007-02-19
> **charles.g.moore said:**
> charles@charles-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:16 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:549   Missed beacon:0

sit0      no wireless extensions.

vmnet8    no wireless extensions.




vmnet1    no wireless extensions.

I have had to plug straight into the wireless router in order to get a reliable connection.
If wired in I have no problems with connectivity.

I know that here at work they use a 128 bit WEP encryption in ASCII mode.  I dont know if that matters.







install wlassistant and configure your wireless using that. It is a KDE package you can use it by issuing sudo wlassistant after installation. Dont forget to tick on ASCII while configuring in wlassistant.

---

