---
title: "keep losing my network connection"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by greggfathead on 2006-10-05
Hello:

I keep losing my wireless network connection, sporadically when my computer either goes to sleep or on restart - the only way I can regain my wireless connection is if i restart the entire system, and even then it's 50-50 whether the connection will be restored.  When I click on the network icon, the attached warning window pops up.

Any ideas?

---

### Post by Jorge on 2006-10-06
I have a laptop and I lost the wifi connection every time I suspend or hibernate the computer. The solution for me was to install the Network Manager applet: on resume, I use one of this tiny program features: right-click the icon, select "activate network" (to uncheck it) and back again. 

I hope it helps,

---

### Post by linuxguiri on 2006-11-22
> **Jorge said:**
> I have a laptop and I lost the wifi connection every time I suspend or hibernate the computer. The solution for me was to install the Network Manager applet: on resume, I use one of this tiny program features: right-click the icon, select "activate network" (to uncheck it) and back again. 

I hope it helps,

I started using Network Manager to solve this problem too, but sometimes Network Manager (nm-applet) doesn't reconnect after resume from suspend. When this happens, I've tried unchecking and checking the "enable networking" option, but it doesn't fix it. And there is no "enable wireless" option shown when this happens. Anyone else have the same problem?

---

### Post by bionnaki on 2006-11-23
no idea why this is happening. perhaps it's a router configuration problem.

but in order to start/restart your connection, open up the terminal and enter

to stop
> 
sudo ifdown ra0


and then to restart

> 
sudo ifup ra0

you must subsitute ra0 with eth0 or whatever your net connection is called.

---

### Post by snowpalmer on 2006-11-23
I have the same problem.  I was wondering if it was happening to anyone else.  Although it doesn't seem to correspond with a hibernate or sleep.  It just loses connection after a while.  I wrote a script to reload it everytime this happens.

```

sudo ifconfig eth1 down
sudo ifconfig eth1 up
sudo route add default gw mygateway

```

---

### Post by linuxguiri on 2006-11-23
just found a bug in launchpad that seems to be related here:
[https://launchpad.net/distros/ubuntu/+source/network-manager/+bug/40125](https://launchpad.net/distros/ubuntu/+source/network-manager/+bug/40125)

i'm sifting through it trying to make sense of which workaround works best.

---

### Post by linuxguiri on 2006-11-23
> **linuxguiri said:**
> just found a bug in launchpad that seems to be related here:
[https://launchpad.net/distros/ubuntu/+source/network-manager/+bug/40125](https://launchpad.net/distros/ubuntu/+source/network-manager/+bug/40125)

i'm sifting through it trying to make sense of which workaround works best.

creating two scripts seems to do the trick (so far):

/etc/acpi/suspend.d/07-networkmanager.sh
```
#!/bin/sh

/usr/bin/dbus-send --system \
      --dest=org.freedesktop.NetworkManager \
      --type=method_call \
      /org/freedesktop/NetworkManager \
      org.freedesktop.NetworkManager.sleep

```

/etc/acpi/resume.d/63-networkmanager.sh
```
#!/bin/sh

/usr/bin/dbus-send --system \
      --dest=org.freedesktop.NetworkManager \
      --type=method_call \
      /org/freedesktop/NetworkManager \
      org.freedesktop.NetworkManager.wake

```

make scripts executable:
```
sudo chmod +x /etc/acpi/suspend.d/07-networkmanager.sh
sudo chmod +x /etc/acpi/resume.d/63-networkmanager.sh
```

and add your wireless driver to MODULES_WHITELIST="" in /etc/default/acpi-support 
for me this looks like: MODULES_WHITELIST="ipw3945"

---

### Post by snowpalmer on 2006-11-23
> **linuxguiri said:**
> just found a bug in launchpad that seems to be related here:
[https://launchpad.net/distros/ubuntu/+source/network-manager/+bug/40125](https://launchpad.net/distros/ubuntu/+source/network-manager/+bug/40125)

i'm sifting through it trying to make sense of which workaround works best.

My problem must be a little different since I'm not using Network Manager. Although it did just start happening after installing Edgy.

---

### Post by Papa-san on 2006-11-23
I am dealing with the same issue, but while using Breezy. (Dapper and Edgy don't work at all with my wireless setup.) Strange, though, it was never an issue with it the first timke I used Breezy. I am now using something called 'Connection Manager' but be forewarned it is in pre-beta stage.

[http://www.ubuntuforums.org/showthread.php?t=299462](http://www.ubuntuforums.org/showthread.php?t=299462)

However, I have not lost my connection in over a day... Not even sure why, but it seems to have worked.

If you decide to try it. You MUST do a full backup, as you probably don't want to re-install...

---

### Post by kalm on 2006-11-23
yes... altough i use rt61 ( seems that for once ubuntu did have all that installed all ready to go, its just worse ) and now that i apparently have 2 wifi interfaces in ifconfig ? (wlan0 and wmaster0 <--- but i understand why its there.. seem like waste though) oh yes and i use edgy. which drops my wireless connection out of nowhere (this can happend during a big installation from synaptic :| ) and only, THE only way i can reconnect is.. that i restart the whole friggin computer! i have no idea of what to do...

---

### Post by l951b951 on 2007-01-05
I'm having this same problem.  Sporadically my wireless will just die.  the network manager applet sees the router, and tries to connect forever.  Never actually connects and I have to reboot (logging out/in doesn't fix it). 
The problem is sporadic, it dies randomly.  I've tried the network manager unchecking "enable wireless" and then waiting and re-enabling it, but to no avail.  Is there a log file generated by network manager that would let me see what my wireless says prior to the drop?  


> **kalm said:**
> yes... altough i use rt61 ( seems that for once ubuntu did have all that installed all ready to go, its just worse ) and now that i apparently have 2 wifi interfaces in ifconfig ? (wlan0 and wmaster0 <--- but i understand why its there.. seem like waste though) oh yes and i use edgy. which drops my wireless connection out of nowhere (this can happend during a big installation from synaptic :| ) and only, THE only way i can reconnect is.. that i restart the whole friggin computer! i have no idea of what to do...

---

### Post by arcanus on 2007-12-30
> **l951b951 said:**
> I'm having this same problem.  Sporadically my wireless will just die.  the network manager applet sees the router, and tries to connect forever.  Never actually connects and I have to reboot (logging out/in doesn't fix it). 
The problem is sporadic, it dies randomly.  I've tried the network manager unchecking "enable wireless" and then waiting and re-enabling it, but to no avail.  Is there a log file generated by network manager that would let me see what my wireless says prior to the drop?

This is EXACTLY what happens to my laptop too. With the added flavor of a system deadlock of some sort. No command ever returns, seem to happen when i have some network load (1+MB/sec DL). I have no idea what causing it. Im using the ipw3945 aswell. It works OOTB.

---

### Post by graabein on 2007-12-30
> **linuxguiri said:**
> creating two scripts seems to do the trick (so far):

/etc/acpi/suspend.d/07-networkmanager.sh
```
#!/bin/sh

/usr/bin/dbus-send --system \
      --dest=org.freedesktop.NetworkManager \
      --type=method_call \
      /org/freedesktop/NetworkManager \
      org.freedesktop.NetworkManager.sleep

```

/etc/acpi/resume.d/63-networkmanager.sh
```
#!/bin/sh

/usr/bin/dbus-send --system \
      --dest=org.freedesktop.NetworkManager \
      --type=method_call \
      /org/freedesktop/NetworkManager \
      org.freedesktop.NetworkManager.wake

```

make scripts executable:
```
sudo chmod +x /etc/acpi/suspend.d/07-networkmanager.sh
sudo chmod +x /etc/acpi/resume.d/63-networkmanager.sh
```

and add your wireless driver to MODULES_WHITELIST="" in /etc/default/acpi-support 
for me this looks like: MODULES_WHITELIST="ipw3945"



Does this (still) work on (X)ubuntu 7.10? 

Or is it just for laptops? (Suspend/resume might also be inactive/screensaver function, no?)


I expect you find your wireless driver with:
```
lshw -class network
```

And for me that would be **acx_pci**, right??
```
  *-network               
       description: Wireless interface
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 10
       bus info: pci@0000:00:10.0
       logical name: wlan0
       version: 00
       serial: 00:11:95:64:66:47
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=acx_pci ip=XXX.XXX.XXX.XXX latency=64 module=acx multicast=yes wireless=IEEE 802.11b+/g+
```

---

### Post by graabein on 2007-12-30
I found another thread [Auto reconnect]("http://ubuntuforums.org/showthread.php?t=567895") that **pings** a website every now and then and runs **reconnect** command if ping returns no answer.

Maybe that is the way to go? **Ping** is not very resource heavy I take it? I don't know exactly when I loose network connection but the main thing is it reconnects itself without having to restart the machine. 

My parents and sisters use the machine so automatic reconnect is better than clicking an icon etc.

---

