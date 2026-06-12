---
title: "Wifi Problems - Tried old advice still unstuck!"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by Kouros on 2006-09-06
Hi guys,

I've been playing with the idea of Ubuntu for a few months, and finally got around to installing it on my old X20 - it's painfully slow, and I'll probably switch to Xubuntu, but that's another issue for another day.

Today I've been trying to get my wifi network up and running, but for the life of me can't work it out. I've read through some old posts, as I recognise other people have had similar issues, but to no avail. Here's the setup:

Airplus Xtreme G+ DWL-G650+ Cardbus adapter

I ran iwconfig:

> kouros@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"Bancroft"  Nickname:"Bancroft"
          Mode:Auto  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality:52/100  Signal level:33/100  Noise level:0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


And I've set the eth0 connection (and others) to disabled, and wlan0 as the default. Still no joy, it just won't see it. My network is not encrypted at the moment, so should be no problem there.

I grabbed Wifi Radar from Apt-Get, but I can't get it to scan for my router.

Any hints?

---

### Post by Blairboy on 2006-09-06
Does 'lspci | grep Broadcom' yield anything?

---

### Post by Kouros on 2006-09-06
> **Blairboy said:**
> Does 'lspci | grep Broadcom' yield anything?

Thanks, but unfortunately not. I don't know if I'm doing anything wrong here, but this command just enters through to the next terminal line.

Any other suggestions?

---

