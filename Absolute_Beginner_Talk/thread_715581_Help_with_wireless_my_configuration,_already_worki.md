---
title: "Help with wireless my configuration, already working but with issues..."
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by darkservlist on 2008-03-05
I would really appreciate any help with this issue i have, my wireless adapter is a wusb54g v4. I've already installed and seems to be working fine, but there must be something wrong with it, since this is what i get from my ifconfig command


```
lo Link encap:Local Loopback
inet addr x.x.x.x Mask x.x.x.x
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:24 errors:0 dropped:0 overruns:0 frame:0
TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:2665 (2.6 KB) TX bytes:2665 (2.6 KB)

rausb0 Link encap:Ethernet HWaddr xx. xx . xx
inet addr x.x.x.x Bcast x.x.x.x Mask x.x.x.x
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:143279 errors:0 dropped:0 overruns:0 frame:0
TX packets:122278 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:146725379 (139.9 MB) TX bytes:27314976 (26.0 MB)
```


as you can see the wireless is identified as Ethernet and the name given is rausb0 also this is how my interfaces file looks like


```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
iface rausb0 inet dhcp
wireless-key xxxxxxxxxx
wireless-essid xxxxxxxxxx

auto rausb0

```

I'm not really sure what to add, or what to remove, I would like to be able to setup a static ip address but with this configuration I don't think that would be likely, also my connection drops from time to time and I have to get it started with **sudo /etc/init.d/networking restart** it's really becoming annoying since I'm always using the internet.

Thanks in advance.

---

### Post by dstew on 2008-03-05
Your wireless connection is using the rausb0 device, and that device uses ethernet encapsulation. That is all correct. The interface is connected, and uses DHCP to get an IP address from your local DHCP server.

If the connection drops from time to time, you might be able to change some of the settings to improve it. We can look at the wireless interface connections by the command **iwconfig rausb0**. Post the output to the forum.

---

### Post by darkservlist on 2008-03-05
Hi, here's what I get from the command iwconfig rausb0:

```
rausb0    RT2500USB WLAN  ESSID:"xxxxx"  Nickname:""
          Mode:Managed  Frequency=2.452 GHz  Access Point: xx. xx. xx. xx  
          Bit Rate=54 Mb/s   
          RTS thr: off   Fragment thr: off
          Link Quality=84/100  Signal level:-53 dBm  Noise level:-82 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by dstew on 2008-03-06
That seems normal. Maybe your dropped connections have something to do with your wireless access point, or even your service provider. You might try to play with the sensitivity settings. Look at the [iwconfig man page]("http://linux.die.net/man/8/iwconfig") for advice on setting the txpower and sens. I don't know much about that, you might have to dig a little for more information.

But, basically, your wireless seems to be configured correctly.

---

### Post by darkservlist on 2008-03-06
Thanks dstew, I''ll look at it.

---

