---
title: "please help with wireless"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by cupid2k7 on 2007-01-19
Hi,
    I just finished installing the Ubuntu 6.10 on my laptop, but i can't connect to the internet. I have a wireless intel Pro 3945 ABG. Does anyone know where to get the driver and also the step of installing it.
thanks

---

### Post by lukew on 2007-01-19
> **cupid2k7 said:**
> Hi,
    I just finished installing the Ubuntu 6.10 on my laptop, but i can't connect to the internet. I have a wireless intel Pro 3945 ABG. Does anyone know where to get the driver and also the step of installing it.
thanks

The best thing to do is check out your card and find out the specific instructions for that card:

[HTML]https://help.ubuntu.com/community/WifiDocs[/HTML]

Some of them require the use of ndswrapper as they don't user native linux drivers and require the windows drivers. Some cards work natively in Linux and only require things like firmware.

Luke

---

### Post by Atomic Dog on 2007-01-19
The 3945 should work out of the box.  You have enabled the card in Networking (system-->administration-->Networking)?  On my laptop (with intel proc, intel graphics, and intel 3945 woreless) has it listed as eth1.  You can connect to open and WEP protected wireless networks.  If you want to use WPA then network Manager might be worth a download.  Otherwise if WEP is fine you might want to get Wifi-Radar which will connect to WEP protected wireless and is easy to use.

---

### Post by Domie on 2007-01-19
Maybe a stupid remark, but is your wifi network protected?

I used to have problems with this. First I forgot to enter a WEP key, then I placed it hexadecimal and finally I got it right with plain ASCII...

---

### Post by mikewhatever on 2007-01-19
I have 3945ABG on HP Pavilion DV5000 laptop. It didn't work out of the box, though the card and the driver were recognized. There wasn't even an option for Wireless in Networking tools. If that's your case, check this thread:[http://ubuntuforums.org/showthread.php?t=321045](http://ubuntuforums.org/showthread.php?t=321045).
It more or less outlines the way of having Gnome Network Manager and kernel restricted modules installed.

---

### Post by darwin_te on 2007-05-27
Kubuntu 7.04 (Feisty)
ASUS G1

Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

WEP 104-bit (128-bit) setting connecting to Windows AP:

/etc/network/interfaces:

########################
#home - wifi
########################

auto eth1
iface eth1 inet static
address 192.168.1.106
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid youressidhere

# passphrase is test
# see [http://www.powerdog.com/wepkey.cgi](http://www.powerdog.com/wepkey.cgi) (Passphrase To Hexadecimal WEP Keys)
wireless-key1 9FDF3BFDFB10AFEB0925EF9605

wireless-defaultkey 1
wireless-keymode open

command line to bring wireless network up:

>ifup eth1

---

