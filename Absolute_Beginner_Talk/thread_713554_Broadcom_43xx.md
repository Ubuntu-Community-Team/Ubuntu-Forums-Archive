---
title: "Broadcom 43xx"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by padamon on 2008-03-02
I installed broadcom 43xx firmware using the restricted driver manager. It now says 'in use' and before I restarted it was detecting networks and everything.

Also, the wireless light is blue now.

I'm wondering if I'm supposed to re-install kubuntu, blacklist  BCM43xx (rmmod) and do the ndiswrapper. I got it working in with ndiswrapper in ubuntu feisty before but I'd rather not use it if there is a better way since I can't go into monitor mode with ndiswrapper also re-installing is annoying.

And my iwconfig
```
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid
          Bit Rate=1 Mb/s   Tx-Power=18 dBm
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by tdrusk on 2008-03-02
> **padamon said:**
> I installed broadcom 43xx firmware using the restricted driver manager. It now says 'in use' and before I restarted it was detecting networks and everything.

Also, the wireless light is blue now.

I'm wondering if I'm supposed to re-install kubuntu, blacklist  BCM43xx (rmmod) and do the ndiswrapper. I got it working in with ndiswrapper in ubuntu feisty before but I'd rather not use it if there is a better way since I can't go into monitor mode with ndiswrapper also re-installing is annoying.

And my iwconfig
```
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid
          Bit Rate=1 Mb/s   Tx-Power=18 dBm
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Ndiswrapper is a good choice because the bcm43xx has a conflict with the synaptic driver. It caused me computer to freeze. This was last year, so I don't know if it is still there or not.

I'm confused by what you want. Do you want to use ndiswrapper with the bcm43xx works?

Also, there is no reason to keep reinstalling. You should learn how to fix what you changed. It will teach you more.

---

