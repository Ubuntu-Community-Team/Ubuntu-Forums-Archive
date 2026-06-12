---
title: "Problems with Airmon-ng..."
date: 2014-10-06
forum: Any Other OS
---

### Post by Ikkuh on 2014-10-06
Hi all,

I'm pretty new with linux but I came pretty far as I may speak. I have just one problem...
I want to put my usb wifi adapter (a TL-WN822N v3 with Realtek 8192cu chipset) in monitor mode with Airmon-ng. I want to do that so I can use Airodump-ng and Aircrack-ng.

So far I'm using Ubuntu 14.04 LTS in a virtual machine on Win7. I plugged in my wlan adapter, connected it to my VM and updated the driver.

Now my adapter works fine and I can use it with the NetworkManager to hook it up to my network.
When I tried to start Arimon-ng I first got some messages that there where other processes who uses my wlan. I Googled and got rid of them all.

The problem is as follows:
```

root@ubuntu:~# iwconfig
wlan1     unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


eth0      no wireless extensions.


lo        no wireless extensions.

```

Then I tried:
```

root@ubuntu:~# airmon-ng start wlan1 7

Interface    Chipset        Driver


root@ubuntu:~# 

```

So it seems that my wlan1 will not start, also when I trie iwconfig again, no changes where shown...

Can anyone help me with this? I search the net for some hours but can't find anything...

Kind Regards.

---

### Post by QIII on 2014-10-06
We do not allow discussion of airmon-ng, aircrack-ng or any related software.

Closed.

---

