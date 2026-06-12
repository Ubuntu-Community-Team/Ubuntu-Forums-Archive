---
title: "Wireless Networking"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by WolfCarinea on 2007-03-19
hello,
 i have a Compaq Presario R3000, with a Broadcom 4306 820.11b/g WLAN card, using Ubuntu 6.06 Edgy, I have used Ndiswrapper to install both bcmwl5.inf and bcmwl5a.inf, both instances say that the hardware is detected. I cannot figure out how to configure my WLAN connection to get it to work, How do i get it to form a list of available connections?

---

### Post by in_flu_ence on 2007-03-19
try download wifi-radar via synaptic?
It is a good tool for wifi detection

---

### Post by PartisanEntity on 2007-03-19
I would recommend you install network-manager and network-manager-gnome. This app makes life very very easy to find and connect to all kinds of networks.

Are you attempting to connect to an encrypted network?

---

### Post by WolfCarinea on 2007-03-19
No it's not an encrypted network

---

### Post by PartisanEntity on 2007-03-19
Okay, then you don't need to do anything else apart from installing network-manager and network-manager-gnome. Then you restart. If you get an error message mentioning something about 'cache' then type this in the terminal and restart again:

```
sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/
```

Then network manager should appear in your notification bar on the panel.

---

### Post by WolfCarinea on 2007-03-19
I now have Network-Manager, Network-Manager-Gnome, and WiFi-Radar installed and opened, WiFi-Radar says it can't find anything, and the Network-Manager says "check that the settings are correct for this network and that the computer is connected to it"

What do i do?

---

### Post by LanDan on 2007-03-19
wifi?

its bluetooth, and the broadcom driver from HELL looks familiar to me even the make and model of the Laptop you are using was the same.

it took me a lot of sweat and tears to get it up and running, but it certainly is possible.

can you tell me which steps you followed?

p.s.

for me it finally worked out to download the windows 2000 driver from compaq instead of the XP one

---

### Post by WolfCarinea on 2007-03-19
at this point i honestly cannot remember the steps i followed because of how many diffrent ways i've tried to get it to work, but i will see what i can do with the Win 2000 Driver. thanks

---

### Post by WolfCarinea on 2007-03-19
you wouldn't happen to have a link to somewhere i can download the Win 2000 Driver for it would you?

---

### Post by PartisanEntity on 2007-03-19
> **WolfCarinea said:**
> I now have Network-Manager, Network-Manager-Gnome, and WiFi-Radar installed and opened, WiFi-Radar says it can't find anything, and the Network-Manager says "check that the settings are correct for this network and that the computer is connected to it"

What do i do?

what is the output of:
```

ndiswrapper -l
```

---

### Post by WolfCarinea on 2007-03-19
Usage: ndiswrapper OPTION

Manage ndis drivers for ndiswrapper.
-i inffile        Install driver described by 'inffile'
-d devid driver   Use installed 'driver' for 'devid'
-e driver         Remove 'driver'
-l                List installed drivers
-m                Write configuration for modprobe


where 'devid' is either PCIID or USBID of the form XXXX:XXXX
wolfcarinea@wolfcarinea-laptop:~$

---

### Post by LanDan on 2007-03-19
[http://h20180.www2.hp.com/apps/Lookup?h_lang=en&h_cc=us&cc=us&h_page=hpcom&lang=en&h_client=S-A-R163-1&h_pagetype=s-002&h_query=R3000&submit.x=10&submit.y=3](http://h20180.www2.hp.com/apps/Lookup?h_lang=en&h_cc=us&cc=us&h_page=hpcom&lang=en&h_client=S-A-R163-1&h_pagetype=s-002&h_query=R3000&submit.x=10&submit.y=3)

it should be on the top intel or amd?

have fun

---

### Post by PartisanEntity on 2007-03-19
> **WolfCarinea said:**
> Usage: ndiswrapper OPTION

Manage ndis drivers for ndiswrapper.
-i inffile        Install driver described by 'inffile'
-d devid driver   Use installed 'driver' for 'devid'
-e driver         Remove 'driver'
-l                List installed drivers
-m                Write configuration for modprobe


where 'devid' is either PCIID or USBID of the form XXXX:XXXX
wolfcarinea@wolfcarinea-laptop:~$

The output of:

```
ndiswrapper -l
```

should be something like:

```
Installed drivers:
bcmwl5          driver installed, hardware present 
```

---

### Post by WolfCarinea on 2007-03-19
Installed ndis drivers:
bcmwl5          driver present, hardware present
bcmwl5a         driver present, hardware present


Sorry the L's look like 1's to me in that text

---

### Post by LanDan on 2007-03-19
p.s.

there are a lot of other files in folder where the bcmwl came from right?

do not remove that folder or the other files, i found out that they seemed to matter

---

### Post by WolfCarinea on 2007-03-19
it only let me download a .exe program how do i activate that or where do i put it?

---

### Post by LanDan on 2007-03-19
.exe???


just click on it and installs

just kidding, you will need to unpack it using cabextract

probably something like "apt-get cabextract" and then "cabextract /home/wolfie/stupiddriver.exe"

this will give you a folder with a lot of stuff including the bcmlw and then you use ndsiwrapper to install it (remember to delete the old ones first)

---

