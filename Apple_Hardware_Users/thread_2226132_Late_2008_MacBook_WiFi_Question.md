---
title: "Late 2008 MacBook WiFi Question"
date: 2014-05-25
forum: Apple Hardware Users
---

### Post by peter_hinkle on 2014-05-25
Installed onto late 2008 macbook5,1 with no problems. The only caveat is that I have no wifi. Since it is my only source for internet, it's pretty important. Is there an accepted procedure for getting wifi up and running on this machine?

---

### Post by varunendra on 2014-05-28
Welcome to the forums Peter!

Please open a terminal (Ctrl-Alt-T) and post back the output of the following commands -
```
uname -mr
lsb_release -d
lspci -nnk | grep -iA2 net
lsusb
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by dylanc on 2015-01-31
[COLOR=#000000]I have a macbook5,2 when i start ubuntu a notification pops up saying airport is disabled. when i go to networks under settings it only gives me the option to connect to LAN, there is no WIFI setting. here is the first part,[/COLOR][COLOR=#ff0000]

```
uname -mr
```[/COLOR]```

[COLOR=#0000ff]3.13.0-32-generic x86_64[/COLOR]
[COLOR=#ff0000]lsp_release -d[/COLOR]
[COLOR=#0000ff]ubuntu 14.04.1 lts[/COLOR]
[COLOR=#ff0000]lspci -nnk | grep -ia2 net[/COLOR]
kernal driver in use: snd_hda_intel
00:09.0 pci bridge [0604]: NVIDA Corporation MCP79 pci bridge [10de:0aab] (revb1)
00:0a:0 ether[COLOR=#ff0000]net [/COLOR]controller [0200]:NVIDA Corporation MCP79 ether[COLOR=#ff0000]net[/COLOR] [10de:0ab0] (rev b1)[CENTER]subsystem: NVIDIA corporation Apple imac 9,1 [10de:cb79]
kernel driver in use: forcedeth
subsystem:Apple Inc. GeForce 9400m [106b:00b1]
kernel driver in use: nouveau[/CENTER]
03:00.0 [COLOR=#ff0000]net[/COLOR]work controller [0280]: broadcom corporation BCM4322 802.11a/b/g/n wireless LAN controller [14e4:432b] (rev 01)
[CENTER]subsystem:apple inc. Airport Extreme [106b:008e]
kernel driver in use: b43-pci-bridge[/CENTER]

```[CENTER]

lsusb coming soon, just have to finish copying it from the picture i took

also not sure if you might know but my trackpad is not functioning, the single click button works when i go under settings and test test it but i get not movement from the trackpad
[/CENTER]
```
lsusb
Bus 002 Device 001: ID 1d6b:0002 linux Foundation 2.0 root hub
Bus 004 Device 003: ID 05ac:8215 Apple, Inc. built-in  bluetooth 2.0+EDR HCI 
Bus 004 Device 002: ID  0a5c:4500 Broadcom corp. BCM2046B1 USB 2.0 hub (part of BCM2046 Bluetooth)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05ac:8300 Apple, Inc. Built-in iSight (no firmware loaded)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 05ac:0229 Apple, Inc. Internal Keyboard/trackpad (MacbookPro) (ANSI)
Bus 003 Device 002: ID 05ac:8242 Apple, Inc. Built-in IR Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
```

---

### Post by rican-linux on 2015-01-31
> **dylanc said:**
> [COLOR=#000000]I have a macbook5,2 when i start ubuntu a notification pops up saying airport is disabled. when i go to networks under settings it only gives me the option to connect to LAN, there is no WIFI setting. here is the first part,[/COLOR][COLOR=#ff0000]

```
uname -mr
```[/COLOR]```

[COLOR=#0000ff]3.13.0-32-generic x86_64[/COLOR]
[COLOR=#ff0000]lsp_release -d[/COLOR]
[COLOR=#0000ff]ubuntu 14.04.1 lts[/COLOR]
[COLOR=#ff0000]lspci -nnk | grep -ia2 net[/COLOR]
kernal driver in use: snd_hda_intel
00:09.0 pci bridge [0604]: NVIDA Corporation MCP79 pci bridge [10de:0aab] (revb1)
00:0a:0 ether[COLOR=#ff0000]net [/COLOR]controller [0200]:NVIDA Corporation MCP79 ether[COLOR=#ff0000]net[/COLOR] [10de:0ab0] (rev b1)[CENTER]subsystem: NVIDIA corporation Apple imac 9,1 [10de:cb79]
kernel driver in use: forcedeth
subsystem:Apple Inc. GeForce 9400m [106b:00b1]
kernel driver in use: nouveau[/CENTER]
03:00.0 [COLOR=#ff0000]net[/COLOR]work controller [0280]: broadcom corporation BCM4322 802.11a/b/g/n wireless LAN controller [14e4:432b] (rev 01)
[CENTER]subsystem:apple inc. Airport Extreme [106b:008e]
kernel driver in use: b43-pci-bridge[/CENTER]

```[CENTER]

lsusb coming soon, just have to finish copying it from the picture i took

also not sure if you might know but my trackpad is not functioning, the single click button works when i go under settings and test test it but i get not movement from the trackpad
[/CENTER]
```
lsusb
Bus 002 Device 001: ID 1d6b:0002 linux Foundation 2.0 root hub
Bus 004 Device 003: ID 05ac:8215 Apple, Inc. built-in  bluetooth 2.0+EDR HCI 
Bus 004 Device 002: ID  0a5c:4500 Broadcom corp. BCM2046B1 USB 2.0 hub (part of BCM2046 Bluetooth)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05ac:8300 Apple, Inc. Built-in iSight (no firmware loaded)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 05ac:0229 Apple, Inc. Internal Keyboard/trackpad (MacbookPro) (ANSI)
Bus 003 Device 002: ID 05ac:8242 Apple, Inc. Built-in IR Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
```

Here is your wireless card "broadcom corporation BCM4322 802.11a/b/g/n wireless LAN". You will need the b43 driver installed. You take can find instructions **[here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")**.

---

