---
title: "[Backtrack 5 r3 Gnome] Problems with installing TP-Link TL-WN727N V4"
date: 2014-07-19
forum: Any Other OS
---

### Post by Ngokkutai on 2014-07-19
I have bought a new USB Wireless device: TP-Link TL-WN727N for my Back Track 5 r3
Device information:
[CENTER][COLOR=#000000][FONT=sans-serif]**TP-LINK** TL-WN727N** v4 (CN?)**
**Availability:** only in China ATM
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]**(Est.) release date: **2013
**Country of manuf.: **China
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]**Interface: USB**
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]**USB 2.0**
**Connector: **Male A
**Form factor tags: **dongle
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]**ID: **[0bda:8179]("http://usb-ids.gowdy.us/read/UD/0bda/8179") ([[COLOR=red]2 addl. devices[/COLOR]]("http://wikidevi.com/wiki/Special:Ask?title=Special%3AAsk&q=%5B%5BVendor+ID::0bda%5D%5D+%5B%5BDevice+ID::8179%5D%5D&po=%3FInterface%0D%0A%3FForm+factor=FF%0D%0A%3FInterface+connector+type=USB+conn.%0D%0A%3FFCC+ID%0D%0A%3FManuf%0D%0A%3FManuf+product+model=Manuf.+mdl%0D%0A%3FVendor+ID%0D%0A%3FDevice+ID%0D%0A%3FChip1+model%0D%0A%3FChip2+model%0D%0A%3FChip3+model%0D%0A%3FSupported+802dot11+protocols=PHY+modes%0D%0A%3FMIMO+config%0D%0A%3FOUI%0D%0A%3FEstimated+year+of+release=Est.+year&eq=yes&p%5Bformat%5D=broadtable&order%5B0%5D=ASC&sort_num=&order_num=ASC&p%5Blimit%5D=500&p%5Boffset%5D=&p%5Blink%5D=all&p%5Bsort%5D=&p%5Bheaders%5D=show&p%5Bmainlabel%5D=&p%5Bintro%5D=&p%5Boutro%5D=&p%5Bsearchlabel%5D=%E2%80%A6+further+results&p%5Bdefault%5D=&p%5Bclass%5D=sortable+wikitable+smwtable"))
Windows: **USB\VID_0BDA&PID_8179**
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]**FCC ID:** none available

[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]**WI1 chip1:** **Realtek** RTL8188EUS
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]**Probable Linux driver**
[**[COLOR=brown]8188eu[/COLOR]**]("https://github.com/lwfinger/rtl8188eu") (vendor driver)
**[precompiled binary driver for the RPi (Raspbian)]("http://www.raspberrypi.org/phpBB3/viewtopic.php?f=26&t=29752&p=342506")**
**[USB ID not yet observed in any mainline kernel / this list]("https://wikidevi.com/wiki/List_of_Wi-Fi_Device_IDs_in_Linux")**
**(see also [passys]("http://linux-wless.passys.nl/"))**
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]**Windows driver**
see **[Realtek's website]("http://www.realtek.com.tw/DOWNLOADS/downloadsView.aspx?Langid=1&PNid=13&PFid=21&Level=4&Conn=3")**
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]**Antenna connect:none**
[/FONT][/COLOR][/CENTER]

From this site: [https://wikidevi.com/wiki/TP-LINK_TL-WN727N_v4_%28CN%3F%29](https://wikidevi.com/wiki/TP-LINK_TL-WN727N_v4_%28CN%3F%29)
I try everything but nothing happen. How can i get this device work on backtrack 5 r3 Gnome? (Backtrack is no longer being maintained). Thanks.

---

### Post by coffeecat on 2014-07-19
*Thread moved to **Other OS/Distro Support**.*

Backtrack is a discontinued OS. You would be better off working with Ubuntu, or if you want the same sort of functionality that Backtrack provided then use Kali Linux, its successor.

---

### Post by chili555 on 2014-07-19
In case anyone else stumbles across this, here is what you do in Ubuntu. With a temporary working internet connection:```
sudo apt-get install linux-headers-generic build-essential git
git clone https://github.com/lwfinger/rtl8188eu.git
cd rtl8188eu
make
sudo make install
sudo modprobe 8188eu
```When a later kernel is installed, recompile:```
cd rtl8188eu
make clean
make
sudo make install
sudo modprobe 8188eu
```The answer was actually in the information provided in that this:> Probable Linux driver
8188eu (vendor driver)Includes a link to the github driver.

What exactly you do in BT or Kali or Suse or Fedora is unknown to me.

---

