---
title: "Strange Wireless Connect Behaviour in Fiesty"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by stevehc on 2007-04-21
Hi,

Totally new to Ubuntu.

Downloaded Fiesty - cannot get wireless to work.

Installed on desktop, wired ethernet connection works fine, wireless fails.
Tried desktop PC and Laptop.
Both see the wireless connections, when chosen it wont connect.
Obviously entered wep keys.
Tried disabling WEP at router but still same.
On laptop, power light on on wireless pcmcia card.
Green light flashes as if tx/rx.
No connect though.
Tried different channels at router config and ssid's.

[COLOR="Red"]Dont know what to [/COLOR]do.
Router = Linksys WRT55AG firmware 1.3
Desktop wireless = Asus A8V motherboard with built in wireless.
Laptop = Fairly elderlyToshiba 8110 satellite and US Robotics card.

Please Help as 2 more PC's are close to dropping nasty Micro$oft into the bin.

---

### Post by stevehc on 2007-04-22
I finally got it going by editing /etc/network/interfaces and adding

auto ra0
iface ra0 inet dhcp
wireless-essid MyESSID
wireless-key 12345678

as suggested by [http://ubuntuforums.org/showthread.php?t=404286](http://ubuntuforums.org/showthread.php?t=404286)

Steve

---

