---
title: "Connecting to the internet using LG350T USB Modem"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by nyn2000 on 2007-04-26
Hi everybody

I installed Ubuntu 7.04 recently. How do I connect to the internet using  LG350T USB modem. I have done ppp config and when i connect using pon, the connection lasts for 2-3 seconds and exits. When connecting in windows, the modem displays "Packet Data (H)" and then shows Tx,RX data. In Linux the modem displays  "Async Data"  and then disconnects.

can anybody help.

tks

*
I managed to do it using wvdial.

If the device is detected, run wvdialconf to create a wvdail.conf file

edit the wvdail.conf file as folows: make  Init2=AT=CRM=1, then enter phone no as #777, give username and password as 'internet', save wvdial.conf file

run wvdial to connect to internet.

---

