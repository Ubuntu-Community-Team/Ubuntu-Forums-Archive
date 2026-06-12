---
title: "wireless dongle problems"
date: 2013-02-19
forum: Any Other OS
---

### Post by myklmar on 2013-02-19
Installed Pinguy OS 11.04 on wife's laptop. Wireless connection now no longer working on Packard Bell EasyNote.
Connected by ethernet line to router and working fine.
Purchased Belkin Realtek 802.11n WLAN adapter...cannot get this to connect either.

iwconfig shows:
lo   no wireless extensions.
eth0  no wireless extensions

Any help please.......the wife is looking daggers at me!
:(

---

### Post by kurt18947 on 2013-02-20
A good first step might be to determine the chip set that Belkin uses.  If USB,  could you copy the output of this terminal command?

```
lsusb
```

If the Belkin is an internal card, this command:

```
lspci
```

The output from this command should look something like this:

00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
**03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)**
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b6)

This tells me the wireless adapter uses an Intel 3945 wireless chip.

---

### Post by myklmar on 2013-02-20
Thanks for the reply,

Did both:

lusb

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 050d:1102 Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



lspci

00:00.0 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 CPU Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:06.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN400/PM800/PM880/PN800/PN880 [S3 UniChrome Pro] (rev 02)

):P
Hoping for an easy answer!

---

### Post by kurt18947 on 2013-02-20
Here is your wireless adapter:

00:06.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)

I don't have any Atheros devices so am not well versed.  I did do a search in the networking and wireless forum using ath5k as a search term and looked for posts in the last 6 months.  Quite a few posts came up including some marked 'solved'.  You might try something similar, or perhaps one of the wireless gurus will pick up on this.

---

### Post by kurt18947 on 2013-02-21
> **tomwatson said:**
> realy.....dongle is not a best medium....you can go for broad band connection.....

I think there may be a little imprecision of terms.  "Dongle" is sometimes used to describe a USB cellular data device and sometimes used to describe a USB WiFi adapter.  Myklmar is describing a WiFi adapter.  

To Myklmar:  I did find one easy thing to check.  In a terminal type:

```
rfkill list all
```

If you don't have rfkill, it's in the repositories.  Here is my output:

rfkill list all
1: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

tpacpi _bluetooth shows up as soft blocked.  That's because I turned it off via a software switch.  If I were seeing Hard blocked, that would indicate that it was turned off by a physical switch, either a button, slider or keyboard combination.  phy0 is my wifi adapter and it is unblocked.  If your wifi device shows soft blocked, you can try this:

```
rfkill unblock all  
```

---

### Post by howefield on 2013-02-21
Thread moved to the "*Other OS/Distro Talk*" forum.

---

### Post by varunendra on 2013-02-21
> **kurt18947 said:**
> Here is your wireless adapter:

00:06.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
Actually, the one he is concerned about looks like this one to me-
> **myklmar said:**
> 
lusb
..
Bus 001 Device 002: ID **050d:1102 [COLOR="Red"]Belkin Components[/COLOR]**


> Hoping for an easy answer!
Let's try a wild shot then :)

In a terminal, please try-
```
sudo modprobe -v rtl8192cu
```
wait a few seconds, and see if the wireless gets activated.

If not, I'm afraid a solution may not be an easy one, and we need to dig deeper.

---

### Post by myklmar on 2013-02-21
rfkill showing as already the newest version.

But 'rfkill list all' produces no output.
'rfkill unblock all' produces no output. 
(nothing changes re wireless connection either!)

---

### Post by myklmar on 2013-02-21
Tried 
> 
sudo modprobe -v rtl8192cu

Returns...
'FATAL: Module rtl8192cu not found'

This isn't too easy!

---

### Post by varunendra on 2013-02-22
> **myklmar said:**
> 'FATAL: Module rtl8192cu not found'
O-oh, it is in my Ubuntu 12.04 kernel. You may try backported kernel drivers if your software source supports that.

Alternately, download the proprietary one from Realtek's official website -
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192CU](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192CU)

Copy it to your desktop then open a terminal and run the following (press 'Tab' key wherever I have written [COLOR="Navy"]<tab>[/COLOR] to auto-fill the rest of the path/name) -
```
cd Desktop
unzip RTL81[COLOR="Navy"]<tab>[/COLOR]
cd RTL81[COLOR="Navy"]<tab>[/COLOR]
chmod +x install.sh
sudo ./install.sh
```
..then let it do its job and keep an eye on the process to make sure it completes successfully (in case it returns any errors and fails, post back the screen output).

Once done, plug-in your modem and do-
```
sudo modprobe -v 8192cu
```
And hope for the best!

---

### Post by myklmar on 2013-02-22
**[COLOR="SeaGreen"]Absolutely brilliant![/COLOR]**

Thank you soooooo much.
Really appreciate your knowledge and help. 

Just one small thing......
everytime turn on laptop, I need to re-enter 
> sudo modprobe -v 8192cu
any way around this?  :)

---

### Post by varunendra on 2013-02-22
> **myklmar said:**
> **[COLOR="SeaGreen"]Absolutely brilliant![/COLOR]**

Thank you soooooo much.
Really appreciate your knowledge and help.
You're welcome, I guess I got lucky with the 'wild shot' ;)

> Just one small thing......
everytime turn on laptop, I need to re-enter 
```
sudo modprobe -v 8192cu
```
any way around this?  :)
Let's try my luck once more..
Run the following in a terminal (you may copy-paste) -
```
echo "8192cu" | sudo tee -a /etc/modules
```
Reboot, and see if it loads automatically.

**PS:**
> **myklmar said:**
> Any help please.......the wife is looking daggers at me!
I hope you're safe now..
:lolflag:

---

### Post by myklmar on 2013-02-23
[SIZE="3"][COLOR="SeaGreen"]THANKS![/COLOR][/SIZE]

):P

I thank you!
My wife thanks you!
The dog thanks you!  :lol:

VERY pleased to be part of this group..............you really are a star. :KS

---

### Post by varunendra on 2013-02-23
> **myklmar said:**
> The dog thanks you!  :lol:
Oooh! I'm obliged by this one!

Glad it worked, and thanks for the award winning feedback ;)

Enjoy you Ubuntu!

---

