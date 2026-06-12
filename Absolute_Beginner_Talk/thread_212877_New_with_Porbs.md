---
title: "New with Porbs"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by erbag on 2006-07-10
Hey! I'm fairly new to Linux and I jus installed Ubuntu on my PC for the 3rd time (from 5.1 - 6).

I installed Ubuntu Dapper Drake on a PC that has a Ralink 2500 - to connect to the net. I found a tut online here but something's wrong.

Here is my prob...I managed to activate the wireless device and deactivated the ethernet connection. Howerver on boot up. The wireless devices is not initalized. How do I rectify this?

The [Tutorial](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500?highlight=%282500%29%7C%28Ralink%29) said:
```

2. Type:
sudo gedit /etc/network/interfaces 

3. In the text editor window that opened search for a stanza beginning with "iface ra0".

4. Add the following line to the beginning of the stanza:

auto ra0 

5. Save the file and close the editor.
```

NB. I did all this and the wireless device is not initialized whern pc boots.

---

### Post by diepruis on 2006-07-10
Please post your entire /etc/network/interfaces, no one will be able to see any errors you may have made without it.

---

### Post by erbag on 2006-07-10
I will as soon as i get access to the pc again. Thought I had saved it to my flash drive...my bad!

---

### Post by erbag on 2006-07-10
Here you go:
```

auto lo
iface lo inet loopback


auto eth1
iface eth1 inet dhcp
auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp
auto wlan0
iface wlan0 inet dhcp


auto ra0
iface ra0 inet dhcp
wireless-essid myWiFi

auto ra0

```

---

### Post by diepruis on 2006-07-11
Mmmm... Okay first off, you need to comment (prepend them with a #) all the eths and aths, lets try to get the ra0 up first, 'k?  Then you need to remove the extraneous "auto ra0" at the bottom of the file. Does your network use WEP? If it does you need to put that in as well. The file should now look like this:

NOTE: **Don't comment lo**, thats a loopback to your PC, I don't know exactly what it does but its important.

```

auto lo
iface lo inet loopback

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

auto ra0
iface ra0 inet dhcp
wireless-essid myWiFi

```

Restart and try again, if it works, great, if it doesn't please post this file again as some apps change it.

---

### Post by erbag on 2006-07-11
I figured something like that was the case. Thanx! Will try it and keep you posted...;)

---

### Post by infoseeker on 2006-07-11
EDITED....oops..dual post :(

---

### Post by erbag on 2006-07-16
It worked fine...

---

### Post by diepruis on 2006-07-16
Lucky &*!&#$*&$. I had so much more difficulty! :)

---

