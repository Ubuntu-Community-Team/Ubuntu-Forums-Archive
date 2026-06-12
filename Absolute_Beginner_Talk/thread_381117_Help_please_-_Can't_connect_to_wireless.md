---
title: "Help please - Can't connect to wireless"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by Griffiss on 2007-03-10
When i go to System > Administration > Networking, my wireless connection is recognised. I put in the ssid name and password, but I still can't connect to the network.

Any help please?

Griff

---

### Post by Crooksey on 2007-03-10
Open a terminal.. then type

```

iwconfig
```

Do you get an output?

---

### Post by Griffiss on 2007-03-10
> **Crooksey said:**
> Open a terminal.. then type

```

iwconfig
```

Do you get an output?
Hi Crooksey

I think what you're looking for is this (the rest just said 'no wireless extensions')
```

wlan0         IEEE 802.11b  ESSID:"MY NETWORK NAME"
                 Mode:Managed  Frequency:2.462GHz  Access Point: 00:0f:B5:18:D7:4a
                 Bit Rate:54 Mb/s   Sensitivity=-200dBm
                 RTS thr:2346 B     Fragment thr:2346 B
                 Power Managment:off
                 Link Quality:100/100    Signal level:-44dBm   Noise level:-256 dBm
                 Rx invalid nwid:0   Rx invalid crypt:0   Rx invalid frag:0
                 Tx excessive retries:0   Invalid misc:0   Missed beacon:0
```

---

### Post by Crooksey on 2007-03-10
```

sudo iwconfig wlan0 essid "youressid"
sudo iwconfig wlan0 key YOURWIFIKEY
sudo dhclient wlan0

```

---

### Post by Griffiss on 2007-03-10
```
sudo iwconfig wlan0 key YOURWIFIKEY
```
gave```
Error for wireless request "Set Encode" (8B2A) :
Invalid argument "YOURWIFIKEY".
```

---

### Post by Crooksey on 2007-03-10
did I put quotes in mine?

And you have to add in your own network key and essid

---

### Post by Griffiss on 2007-03-10
You didn't put quotes in yours, but the terminal used quotation marks in the output.

I used my own ssid name and network key. i.e. where is says youressid above, i put my ssid name, and where it says YOURWIFIKEY, I put in my wifi key. Should I input quotes?

---

### Post by Griffiss on 2007-03-10
bumping for extreme need!! please help!

---

### Post by Super_6_4 on 2007-04-24
Have you successfully connected to your network before?

---

