---
title: "Telstra 4G Mobile Broadband Setup"
date: 2012-10-21
forum: Australia Team
---

### Post by bra|10n on 2012-10-21
I recently purchased a Telstra 4G USB device and anticipated I'd need to jump through a few hoops to get this to work on Kubuntu (12.10). 
In fact getting this up and running proved quite simple...

After connecting the unit to a USB port I ran **lsusb**, with the following output;

```
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
[COLOR=Red]Bus 003 Device 003: ID 19d2:0257 ZTE WCDMA Technologies MSM [/COLOR]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 064e:c21c Suyin Corp. 
```Using this information I went to /lib/udev/rules.d/40-usb_modeswitch.rules and added the following entry;
```
# ZTE MF821 4G LTE
ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="0257", RUN+="usb_modeswitch '%b/%k'"
```As you can see all I did was copy the closest entry in description, which was 
```
# ZTE MF820 4G LTE 
ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="0166", RUN+="usb_modeswitch '%b/%k'"
```and substitute the correct values from the earlier usb scan.

I then created a file called **19d2:0257** in /etc/usb_modeswitch.d/ and put in the following,
```
# Telstra ZTE LTE 4g modem
#
DefaultVendor=  0x19d2
DefaultProduct= 0x0257

TargetVendor=  0x19d2
TargetProduct= 0x0257

MessageContent="55534243123456782400000080000685000000240000000000000000000000"

CheckSuccess=20
```Finally, to have Network Manager automatically recognise the device I added the following line to /etc/rc.local;
```
modprobe usbserial vendor=0x19d2 product=0x0257
```Now the device is recognised as a Mobile Broadband connection whenever it is plugged including after a reboot.

cheers

---

### Post by Jared Norris on 2012-10-22
Awesome work! We've been keeping a running tally of what devices do and don't work in Australia at [https://wiki.ubuntu.com/AustralianTeam/Projects/WirelessBroadbandInformation]("https://wiki.ubuntu.com/AustralianTeam/Projects/WirelessBroadbandInformation")

Would you mind spending a couple of minutes adding your information to that? Feel free to link to this post for all the how to though so you don't have to write it all out again though.

---

### Post by bra|10n on 2012-10-23
> **head_victim said:**
> 
Would you mind spending a couple of minutes adding your information to that? Feel free to link to this post for all the how to though so you don't have to write it all out again though.

Done.

---

### Post by bmork on 2012-11-11
> **bra|10n said:**
> Finally, to have Network Manager automatically recognise the device I added the following line to /etc/rc.local;
```
modprobe usbserial vendor=0x19d2 product=0x0257
```Now the device is recognised as a Mobile Broadband connection whenever it is plugged including after a reboot.

cheers


Note that the generic usbserial you are using here is intended only for testing and one-off lowspeed prototypes.  It will work, but will probably severely limit the throughput of a 4G modem.

The device in question was recently added to the option serial driver and the qmi_wwan network driver.  The addition to the option driver is included in all maintained stable and longterm kernel relases, except 2.6.32.y, so manually adding the device to any serial driver should be completely unnecessary.

---

### Post by Jared Norris on 2012-11-14
> **bmork said:**
> Note that the generic usbserial you are using here is intended only for testing and one-off lowspeed prototypes.  It will work, but will probably severely limit the throughput of a 4G modem.

The device in question was recently added to the option serial driver and the qmi_wwan network driver.  The addition to the option driver is included in all maintained stable and longterm kernel relases, except 2.6.32.y, so manually adding the device to any serial driver should be completely unnecessary.

Thanks for that information, I'd think that this device is going to be fairly common throughout Australia going forward so it will be good for anyone happening by to know.

---

### Post by bra|10n on 2012-11-19
> **bmork said:**
> Note that the generic usbserial you are using here is intended only for testing and one-off lowspeed prototypes.  It will work, but will probably severely limit the throughput of a 4G modem.

The device in question was recently added to the option serial driver and the qmi_wwan network driver.  The addition to the option driver is included in all maintained stable and longterm kernel relases, except 2.6.32.y, so manually adding the device to any serial driver should be completely unnecessary.

Thank you for your work in this area and your comments. I confirm the driver now being used is option1. With a clean install of Chakra w/. kernel 3.6.6-1 the modem is still unrecognised; i.e NetworkManager doesn't initiate the MobileBroadband option. Copying the "**19d2:0257**" file, (*pasted above*), to /usr/share/usb_modeswitch folder fixed this problem. With only this additional file the modem is recognised on startup and when removed and replugged.

---

### Post by Martin Hecht on 2013-08-21
In Germany I have received an "O2 LTE 4G Surf stick" whih is recognized as "ZTE WCDMA Technologies MSM" and carries the labelling "Model: MF821D". I'm using it with Ubuntu 12.04 LTS. Normally I have configured my ethernet and wlan devices manually, i.e. directly in /etc/network/interfaces and I manage them with ifup/ifdown ifconfig. I'm posting my steps to get the stick working here assuming it could be useful for anybody else.

To get the stick working I basically followed the instructions above. I did
```

# apt-get install usb-modeswitch usb-modeswitch-data modemmanager

```
plugged in the stick and found it:
```

# lsusb 
...
Bus 001 Device 004: ID 19d2:0326 ZTE WCDMA Technologies MSM 
...

```
However, neither editing a file in /lib/udev/rules.d/, nor putting an appropriate file in /etc/usb_modeswitch.d/ did make the stick working.
Here [http://www.linuxforums.org/forum/wireless-internet/193096-zte-ac682-modem-not-working-ubuntu-12-04-a.html](http://www.linuxforums.org/forum/wireless-internet/193096-zte-ac682-modem-not-working-ubuntu-12-04-a.html) I have found the required hint:
```

# eject /dev/sr0

```
caused the stick to switch from the stroage mode to the modem mode. (maybe someone can provide a better way using udev, but at least it is working now). About 60 seconds after ejecting it is ready to be used as a modem.

Furthermore, I needed:
```

# apt-get install wvdial minicom

```
for my O2 Go Surf & Flat M contract the following parameters (see [http://hilfe.o2online.de/t5/Funktionen-Einstellungen/Einstellungen-Mobiltelefon-manuell-einrichten/ta-p/143574](http://hilfe.o2online.de/t5/Funktionen-Einstellungen/Einstellungen-Mobiltelefon-manuell-einrichten/ta-p/143574)) in /etc/wvdial.conf
```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
New PPPD = yes
Modem = /dev/ttyUSB2
ISDN = 0
Baud = 57600
Ask Password = 0
Dial Command = ATDT
Stupid Mode = 1
Compuserve = 0
Idle Seconds = 0
Init3 = AT+CGDCONT=1,"IP","internet"
Phone = *99#
Password = internet
Username = o2
Auto DNS = 0

```
actually username is not required by the provider, but wvdial would not accept the config file if username is not in there.
To open a connection I use the following script:
```

#!/bin/bash
# close other connections to avoid routing trouble
ifconfig wlan0 down
ifconfig eth0 down
# start services if not running yet
service modemmanager restart
service network-manager restart
# remind me to plug in the surf stick ;-)
echo insert stick
# wait until it is there and switch to modem mode
while [ ! -e /dev/sr0 ] ; do sleep 1 ; done
echo Stick found
sleep 3
echo ejecting sr0
eject sr0
# be verbose to make the 60 seconds more comfortable... 
# we watch syslog to see what's happening
echo "waiting 60s for unlocking of stick (when it's green you can ctrl-c and call wvdial)"
tail -f /var/log/syslog &
for s in $(seq 60) ; do 
 echo ; echo -n "${s}s: "
 sleep 1
done
# hoping that we were waiting long enough (modem-manager asks us to enter the PIN in the meantime) - we stop watching syslog
kill %1
echo
echo to disconnect press ctrl-c
# dial in
wvdial
# after user hits ctrl-c we stop the managers again so that we can manually start other network connections again
service modemmanager stop
service network-manager stop

```
finally, I had to adapt my firewall settings to allow traffic over the ppp0 interface

I'm still trying to get rid of the network-manager and the modem manager. One step towards this would be to enter the PIN of the SIM card with minicom, but I did not yet manage to do so (and I'm afraid locking down my card completely). Useful links to this topic:
[http://3g-modem.wikifoundry.com/page/ZTE+AT-commands](http://3g-modem.wikifoundry.com/page/ZTE+AT-commands) and here an example for the use of the At commands to force the stick to 4G mode: [http://www.eigenmagic.com/2012/03/14/how-to-get-telstra-4g-mobile-broadband-working-with-linux/](http://www.eigenmagic.com/2012/03/14/how-to-get-telstra-4g-mobile-broadband-working-with-linux/)
Manual for the LTE 4G stick: [http://zte.com.au/downloads/manuals/MF821_Manual.pdf](http://zte.com.au/downloads/manuals/MF821_Manual.pdf) (I have found this on google, but I can not access th file from outside Australia, maybe someone can post the AT commands for this model here?)

---

### Post by bmork on 2013-08-21
> **Martin Hecht said:**
> In Germany I have received an "O2 LTE 4G Surf stick" whih is recognized as "ZTE WCDMA Technologies MSM" and carries the labelling "Model: MF821D". I'm using it with Ubuntu 12.04 LTS. Normally I have configured my ethernet and wlan devices manually, i.e. directly in /etc/network/interfaces and I manage them with ifup/ifdown ifconfig. I'm posting my steps to get the stick working here assuming it could be useful for anybody else.

To get the stick working I basically followed the instructions above. I did
```

# apt-get install usb-modeswitch usb-modeswitch-data modemmanager

```
plugged in the stick and found it:
```

# lsusb 
...
Bus 001 Device 004: ID 19d2:0326 ZTE WCDMA Technologies MSM 
...

```


That's odd.  The 19d2:0326 ID is supposed to be the switched (modem) ID, which would indicate that usb-modeswitch had already done it's job.  The unswitched ID of this device should be 19d2:0325.  Maybe you could confirm that by looking in e.g. the dmesg output?

What does "lsusb -vd 19d2:0326" look like before and after you do "eject /dev/sr0"?


> 
However, neither editing a file in /lib/udev/rules.d/, nor putting an appropriate file in /etc/usb_modeswitch.d/ did make the stick working.
Here [http://www.linuxforums.org/forum/wireless-internet/193096-zte-ac682-modem-not-working-ubuntu-12-04-a.html](http://www.linuxforums.org/forum/wireless-internet/193096-zte-ac682-modem-not-working-ubuntu-12-04-a.html) I have found the required hint:
```

# eject /dev/sr0

```
caused the stick to switch from the stroage mode to the modem mode. (maybe someone can provide a better way using udev, but at least it is working now). About 60 seconds after ejecting it is ready to be used as a modem.


"eject" is the common command used to switch ZTE devices, so that sounds reasonable. The usb-modeswitch equivalent of eject is "5553424312345678000000000000061b000000020000000000000000000000" if you just want to add a usb-modeswitch configuration for your device.

But it is already there AFAICS.  The only issue is that there is a likely typo in the 19d2:0325 entry:  The TargetVendor should probably be 0x19d2 instead of 0x12d1



> 

Furthermore, I needed:
```

# apt-get install wvdial minicom

```
for my O2 Go Surf & Flat M contract the following parameters (see [http://hilfe.o2online.de/t5/Funktionen-Einstellungen/Einstellungen-Mobiltelefon-manuell-einrichten/ta-p/143574](http://hilfe.o2online.de/t5/Funktionen-Einstellungen/Einstellungen-Mobiltelefon-manuell-einrichten/ta-p/143574)) in /etc/wvdial.conf
```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
New PPPD = yes
Modem = /dev/ttyUSB2
ISDN = 0
Baud = 57600
Ask Password = 0
Dial Command = ATDT
Stupid Mode = 1
Compuserve = 0
Idle Seconds = 0
Init3 = AT+CGDCONT=1,"IP","internet"
Phone = *99#
Password = internet
Username = o2
Auto DNS = 0

```
actually username is not required by the provider, but wvdial would not accept the config file if username is not in there.
To open a connection I use the following script:
```

#!/bin/bash
# close other connections to avoid routing trouble
ifconfig wlan0 down
ifconfig eth0 down
# start services if not running yet
service modemmanager restart
service network-manager restart
# remind me to plug in the surf stick ;-)
echo insert stick
# wait until it is there and switch to modem mode
while [ ! -e /dev/sr0 ] ; do sleep 1 ; done
echo Stick found
sleep 3
echo ejecting sr0
eject sr0
# be verbose to make the 60 seconds more comfortable... 
# we watch syslog to see what's happening
echo "waiting 60s for unlocking of stick (when it's green you can ctrl-c and call wvdial)"
tail -f /var/log/syslog &
for s in $(seq 60) ; do 
 echo ; echo -n "${s}s: "
 sleep 1
done
# hoping that we were waiting long enough (modem-manager asks us to enter the PIN in the meantime) - we stop watching syslog
kill %1
echo
echo to disconnect press ctrl-c
# dial in
wvdial
# after user hits ctrl-c we stop the managers again so that we can manually start other network connections again
service modemmanager stop
service network-manager stop

```
finally, I had to adapt my firewall settings to allow traffic over the ppp0 interface

I'm still trying to get rid of the network-manager and the modem manager. One step towards this would be to enter the PIN of the SIM card with minicom, but I did not yet manage to do so (and I'm afraid locking down my card completely). Useful links to this topic:
[http://3g-modem.wikifoundry.com/page/ZTE+AT-commands](http://3g-modem.wikifoundry.com/page/ZTE+AT-commands) and here an example for the use of the At commands to force the stick to 4G mode: [http://www.eigenmagic.com/2012/03/14/how-to-get-telstra-4g-mobile-broadband-working-with-linux/](http://www.eigenmagic.com/2012/03/14/how-to-get-telstra-4g-mobile-broadband-working-with-linux/)
Manual for the LTE 4G stick: [http://zte.com.au/downloads/manuals/MF821_Manual.pdf](http://zte.com.au/downloads/manuals/MF821_Manual.pdf) (I have found this on google, but I can not access th file from outside Australia, maybe someone can post the AT commands for this model here?)

I can understand your problems with network-manager, but I will recommend that you look closer at recent ModemManager development before giving it up completely.  Maybe contributing to make it do what you want is a better option?

Modern LTE/UMTS/CDMA modem management is much more than just connect/disconnect, and traditional static network confgurations will severely limit the usability of these devices.  It might be OK for you, but I would not recommend it for the common user.  Most people will want some control wrt roaming, LTE/3G/2G network selection/priority, SMS, positioning etc.  And they will also want to use the ethernet-like interface instead of PPP to achieve the full LTE speed in both directions.  You can of course script all these things yourself (I know - I have done it :-), but using ModemManager does it so much better.

Not that it can't still be improved.  But I beleive that it is better to work in that direction than trying to work around it.

---

### Post by Martin Hecht on 2013-09-12
> **bmork said:**
> That's odd.  The 19d2:0326 ID is supposed to be the switched (modem) ID, which would indicate that usb-modeswitch had already done it's job.  The unswitched ID of this device should be 19d2:0325.  Maybe you could confirm that by looking in e.g. the dmesg output?

What does "lsusb -vd 19d2:0326" look like before and after you do "eject /dev/sr0"?

you are right. it is 19d2:0325 before the eject and 19d2:0326 afterwards

> **bmork said:**
>  "eject" is the common command used to switch ZTE devices, so that sounds reasonable. The usb-modeswitch equivalent of eject is "5553424312345678000000000000061b000000020000000000000000000000" if you just want to add a usb-modeswitch configuration for your device.

But it is already there AFAICS.  The only issue is that there is a likely typo in the 19d2:0325 entry:  The TargetVendor should probably be 0x19d2 instead of 0x12d1 

yes, automatic mode switching works now. I have added the following line to /lib/udev/rules.d/40-usb_modeswitch.rules
```

## ZTE MF821 4G LTE
ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="0325", RUN+="usb_modeswitch '%b/%k'"

```

and created a file /etc/usb_modeswitch.d/19d2:0325
```

# Telstra ZTE LTE 4g modem
#
DefaultVendor=  0x19d2
DefaultProduct= 0x0325

TargetVendor=  0x19d2
TargetProduct= 0x0326

#MessageContent="55534243123456782400000080000685000000240000000000000000000000"
MessageContent="5553424312345678000000000000061b000000020000000000000000000000"
CheckSuccess=20

```

Probably I had a copy-paste error in the device IDs, but also the eject command looks different from what I have found on the net. What does it mean? Is it vendor-specific? Is there a documentation somewhere how these strings have to look like? 

> **bmork said:**
>  I can understand your problems with network-manager, but I will recommend that you look closer at recent ModemManager development before giving it up completely.  Maybe contributing to make it do what you want is a better option?

To be honest, I was a bit frustrated that the automatic mode switching didn't work, which actually has nothing to do with the modem management afterwards. But maybe in future releases of Ubuntu the configuration for these new devices will already be included. Anyhow, I was ending up writing my own script for doing things which I expected to work out of the box - and that's something I know from network manager which promises that it "simply makes networking just work" but fails to manage some things (maybe it is the same issue that the levels below often don't work as expected, setting priorities for different Wifi's...)

Well, thank you for the hints so far. Since mode switching works automatically now, my connection script look like this:
```

#!/bin/bash
# close other connections to avoid routing trouble
ifconfig wlan0 down
ifconfig eth0 down
killall dhclient
killall wpa_supplicant
# start services if not running yet
service modemmanager start
service network-manager start
# remind me to plug in the surf stick ;-)
if !  lsusb | grep -q 19d2:0326 ; then 
echo insert stick
# wait until it is there and has switched to modem mode
while ! lsusb | grep -q 19d2:0326 &>/dev/null  ; do sleep 1 ; done
echo Stick found
fi
# be verbose to make the 60 seconds more comfortable... 
# we watch syslog to see what's happening
echo "waiting 60s for unlocking of stick (when it's green you can ctrl-c and call wvdial)"
tail -f /var/log/syslog &
for s in $(seq 60) ; do 
 echo ; echo -n "${s}s: "
 sleep 1
done
# hoping that we were waiting long enough - we stop watching syslog
kill %1
echo
echo to disconnect press ctrl-c
# dial in
wvdial

```
I have moved the shutdown of the services to my other scripts with which I connect to Wifi or ethernet. I hope that this way modem manager survives a trip with the subway and helps me connecting at the other end of the tunnel :-)

---

### Post by chester2 on 2013-09-28
Greeetings,

Just binned windrows 8 and installed ubuntu 12.10.03 lts. Only problem so far is the telstra 4g usb mobile broadband. The network connection manager recognises the item and I have set it up to the best of my knowledge but it will not connect, light remains red and popup says "disconnected"

Any thoughts as to where to start, new to ubuntu and waaay too long on windows.

Thanks in advance.
Chester

---

