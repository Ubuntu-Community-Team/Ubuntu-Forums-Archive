---
title: "WPA and WPA2"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by bigdave216 on 2006-11-09
Hi there,
I am a new ubuntu user and have managed with some problems to connect wirelessly to my home network using a dlink 510 PCI wireless card.  This is all well and good, but the card only connects/works if WEP hex 64bit is used on the router when using ubuntu.  I have xp installed and use WPA2 with this.  I would like to use ubuntu 6.06 with WPA 2.  
Like I said I am a new user of linux.  If anyone can tell me how I could get ubuntu to connect using WPA2 then that would be great.  At the moment I am having to connect to my router settings in xp and switch encrytion mode to WEP before I can wirelessly access the internet using ubuntu.  Please be slow as I really have very little knowledge of linux at all!
Thanks.

---

### Post by wieman01 on 2006-11-10
I am not sure what chipset this card has but I reckon it's Atheror, am I right? There is help for you: [http://www.ubuntuforums.org/showthread.php?t=202834]("http://www.ubuntuforums.org/showthread.php?t=202834")

Post your problem there if you need help. 

_**ATTENTION:**_
> wpa-driver = madwifi
You'll see what I mean with that. Also you'll have to replace "wlan0" with "ath0" if you don't use "ndiswrapper"...

Let me know what chipset you exactly have...

---

### Post by bigdave216 on 2006-11-10
My chipset is Realtek rtl8180

---

### Post by wieman01 on 2006-11-10
Then try this:
> auto [COLOR="DarkGreen"]ra0[/COLOR]
iface [COLOR="DarkGreen"]ra0[/COLOR] inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid [COLOR="Red"]<your_essid>[/COLOR]
[COLOR="Blue"]wpa-ap-scan 1[/COLOR]
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk [COLOR="Red"]<your_hex_key>[/COLOR] [COLOR="Blue"][IMPORTANT: See "WPA-PSK key generation"][/COLOR]
Not sure what your wireless interfaces is called ("ra0"?)... Please also see the section on PSK key generation.

---

