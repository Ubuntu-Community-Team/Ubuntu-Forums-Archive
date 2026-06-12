---
title: "Wireless Interface Settings"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by Andrew Garn on 2007-05-30
I installed my MA111 v1 wireless usb adapter by using the following guide:
[https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111](https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111)

I couldnt get it to connect to my network so I took off the WEP encryption to test the adapter would work and connect to my network. These were the lines I added to my interfaces file located in: /etc/network/interfaces.

iface wlan0 inet dhcp
wireless_mode managed
wireless_essid SOTON

This worked, my laptop connected to the wireless network and the internet worked. However I needed to put the WEP encryption back on, which I did. This meant that obviously the laptop would no longer connect to the network.

Now I am on my windows pc, trying to get the adapter to work with WEP back on.

My network settings on my router are:

Name: SOTON
Region: Europe
Channel: 11
Mode: g & b
WEP Enabled
Authentication Type: Shared Key
Encryption Strength: 64bit
Key: 1234567891

So I tried to add these settings to my interface file. My interface file now says:

iface wlan0 inet dhcp
wireless_mode managed
wireless_essid SOTON
wireless_enc on
wlan_ng_keyfile /etc/network/wlan
wlan_ng_authtype shared key

with /etc/network/wlan being a text file with just the network key, 1234567891, in it.

The laptop will now NOT connect to the network still

does anyone have advice to what settings changes I need to make to the interface file?

---

### Post by Andrew Garn on 2007-05-30
still can't get it to work

my current services file says:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
ifaceath0 inet dhcp

iface wlan0 inet dhcp
wireless_mode managed
wireless_enc on
wireless-essid SOTON
wireless-key s:1234567891

auto wlan0

```

---

### Post by Mnew2Linux on 2007-05-30
Ok, so I think I got it to work...here's my interface...

```

auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

iface wlan0 inet dhcp
wireless_mode managed
wireless-essid Wireless
wireless-enc on
wlan-ng-key0 zz:zz:zz:zz:zz
wlan-ng-authtype opensystem
wireless-key zzzzzzzzzz

auto wlan0
```

The multiple z's indicate my wep key.  Now, here's the thing, I had to go into my router to ensure that it was open key (opensystem) and I had to configure a network passphrase in order to get my wep key, that's a given.  Now, I'm only open key at 64 bit but I have access with wireless encryption as of right now.  I have not restarted, which will thus be the true test...here goes!

---

### Post by Mnew2Linux on 2007-05-30
Yup, at start up it works..now the only thing is, I'm not sure if I will need the wlan_ng_key0 zz:zz:zz:zz:zz part...but I'll leave it in now, ya know?

---

### Post by Andrew Garn on 2007-05-30
I only have a network key in ASCII form tho ten digits...

how do i convert to ```
xx:xx:xx:xx:xx
``` form?

Cani have an open key system if 6 users use the same key? Because if the router will only let one computer/laptop use the key at a time then that wont work for me...

---

### Post by Mnew2Linux on 2007-05-30
In WEP, the users can only have one key, I tried to give everyone a different key and they weren't able to access the network.  So, if there were other wireless devices they would need the same key...as far as ASCII, I don't know.  I'm a Hexadecimal 10 character WEP...which is really weak and easy to crack.  I'm not too sure on the security of ASCII...so take care on that...but I hope this helps, even a little bit...

---

### Post by Andrew Garn on 2007-05-31
so multiple computers can use the system without a shared key?

---

### Post by Mnew2Linux on 2007-05-31
If there were multiple wireless computers on my network then we'd all have the same key

---

### Post by lazyart on 2007-05-31
> **Mnew2Linux said:**
> So, if there were other wireless devices they would need the same key...as far as ASCII, I don't know.  I'm a Hexadecimal 10 character WEP...which is really weak and easy to crack.  I'm not too sure on the security of ASCII...so take care on that...but I hope this helps, even a little bit...

WEP is easy to crack-- Hex or ASCII doesn't make a difference.  ASCII is offered as a simpler way to remember and enter the key but it is converted to a hex value for transmission.

---

### Post by Mnew2Linux on 2007-05-31
> **lazyart said:**
> WEP is easy to crack-- Hex or ASCII doesn't make a difference.  ASCII is offered as a simpler way to remember and enter the key but it is converted to a hex value for transmission.

Yeah, that's what I was sayin', WEP is really easy to crack, especially at 64 bit

---

### Post by Andrew Garn on 2007-05-31
I dont careabout security, its only got a key to stop someone sitting with their laptop outside the house and wasting my bandwidth.

My router is now set to open system and is not working still..

---

### Post by Andrew Garn on 2007-06-03
still not got it to work, anyone?

---

### Post by northicert on 2007-06-03
I wasn't wild about using a key but my service teck said it protected me if someone was using my site to access x-rated sites.  But you get different storys from different people.

---

### Post by Andrew Garn on 2007-06-04
still not got my settings in my interface file right.

---

