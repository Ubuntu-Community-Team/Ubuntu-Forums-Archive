---
title: "wg311v2 gutsy"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by sc30317 on 2007-11-01
Has anyone gotten WPA working in gutsy with this card?  If so, how?  There are some posts on it, but none of their solutions work, some just crash the system!

Please! :guitar:

---

### Post by haldean on 2007-11-01
Sorry, probably being dumb, but which card?
Also, a ```
lspci | grep Wireless
``` would probably be helpful.
And if it's a Broadcom 4318, mine works perfectly with WPA2 :)

---

### Post by sc30317 on 2007-11-01
This Card:
[http://kbserver.netgear.com/products/WG311v2.asp](http://kbserver.netgear.com/products/WG311v2.asp)

Can anyone give me step by step instructions to set it up with WPA?  That would be AMAZING!

---

### Post by sc30317 on 2007-11-01
shameless please help?

---

### Post by sc30317 on 2007-11-02
pretty please?  My desktop is useless without this!

---

### Post by sc30317 on 2007-11-03
Last Call?

---

### Post by RLovelett on 2007-11-10
This now makes two of us!?

---

### Post by ksonic1055 on 2007-12-15
How did you get this card to work? I cant get it to work natively, and with ndiswrapper and the 2.0.0.7 driver, I get the same result. Please help.

---

### Post by RLovelett on 2007-12-27
I got this working eventually by conglomerating two or three forum posts together to get a working setup.  I can tell you though the basic steps I used to get it working.

Most of this comes from this [HOWTO]("http://ubuntuforums.org/showpost.php?p=3568030&postcount=6") and this one too [HOWTO]("http://ubuntuforums.org/showpost.php?p=1532000&postcount=1"):
First make sure that ndiswrapper is installed.
```
sudo apt-get install ndiswrapper-common
```

Then copy the 2.0.0.7 inf file to your desktop and then
```

cd ~/Desktop/
sudo ndiswrapper -i wg311v2.inf
sudo ndiswrapper -m
sudo modprobe ndiswrapper

```

Now we need to blacklist the current driver:
```
sudo gedit /etc/modprobe.d/blacklist
```

Add the line ```
blacklist acx
``` at the end of the document.

Now we need to use wpa_supplicant so make sure it's installed.
```
sudo apt-get install wpasupplicant
```

then
```
wpa_passphrase your_ssid your_psk
```
Note: your_ssid is the name of your wireless network (a.k.a. SSID) and your_psk is the password you want to use to protect your network.

Now copy the psk string you got as output.

```
sudo gedit /etc/wpa_supplicant.conf
```

Now paste as follows:
```
ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
       ssid="your_ssid"
       scan_ssid=1
       proto=WPA RSN
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk=[COLOR="Red"]your_psk[/COLOR]
}
```

It's been awhile since I got mine working.  But I'm pretty sure that did the trick.  You can also think about installing [Wicd]("http://wicd.sourceforge.net").

---

