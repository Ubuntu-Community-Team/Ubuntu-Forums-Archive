---
title: "Have I installed my wireless driver correctly?"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by nirpius on 2007-07-13
Here is what I got when I ran iwconfig:

```
nirpius@ACER2200:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated
          Bit Rate=1 Mb/s
          RTS thr=2347 B   Fragment thr=2346 B
          Power Management:off
          Link Quality:0/100  Signal level:56/154  Noise level:160/154
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

nirpius@ACER2200:~$


```

---

### Post by wildseven on 2007-07-13
This doesn't show anything really. It shows you have a wifi card that is recognized but you aren't associated with any APs. Why don't you try your wireless card to see if it works. And if it doesn't...well then there is a problem with the installation.

---

### Post by nirpius on 2007-07-13
I tried scanning for networks using KWiFiManager and it said that my connection strength was 0 and that there were no networks nearby even though I'm sitting right next to my Wireless hub and my brother is smugly using the internet wrielessly on his Windows laptop. I assume this means that I've done somewthing wrong with the install. Should I try again with ndiswrapper or try to find a new driver?

---

### Post by annda on 2007-07-13
what is your card (PCI or PCMCIA, what brand and model)? what have you tried? ndiswrapper? which guide?

what does this say:

```
sudo lshw -class network
```

---

