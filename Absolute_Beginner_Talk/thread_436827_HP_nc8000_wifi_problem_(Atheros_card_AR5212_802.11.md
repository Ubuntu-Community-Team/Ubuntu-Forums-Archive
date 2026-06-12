---
title: "HP nc8000 wifi problem (Atheros card: AR5212 802.11abg NIC)"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by Timo425 on 2007-05-08
Hi,

First of all, I have HP nc8000 laptop, with Atheros card, named AR5212 802.11abg NIC. I tried to fix this problem some weeks ago. My father tried to fix the problem too, spending hours for it, he is a Gentoo user for some years and quite skilled ,but it seems, that not enough for this one. From the installation of 7.04 (I was XP user before and I am more or less green in linux) I have been in net wired. 

It took us days, but I feel desperate about the issue, because it just seems to never get working. :confused: 

I have Atheros 5212, I have madwifi-ng installed and wpasupplicant.
He even got it succesfully scanning for accesspoints. But somethings is still wrong. (I am not sure if it still scans).

He even tried newest kernel (2.6.20), but it made only worse.

Please someone tell me what to do and also ask for extra information, if needed.
Oh yes, I am trying to reach WPA encrypted router (correct me if I say something in a wrong way).

I appreciate help!

---

### Post by Kobalt on 2007-05-08
Do you try to connect to your network using Network-Manager ? If so, I advise you to try without it (you can remove it from Synaptic) and try to connect using this method : [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)
Network-Manager also caused me some troubles with my wpa encrypted network...

---

### Post by Timo425 on 2007-05-08
> **Kobalt said:**
> Do you try to connect to your network using Network-Manager ? If so, I advise you to try without it (you can remove it from Synaptic) and try to connect using this method : [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)
Network-Manager also caused me some troubles with my wpa encrypted network...


Well, everything seems nice, but I lost my wired net too, when i uninstalled Network-manager.. And it is tricky to get it back since I don't have net at all now..I am in XP (lucky that I have dual-boot). Please tell me how to get wired back without network-manager. :lolflag:

---

### Post by Kobalt on 2007-05-08
You will now need to configure your network through System > Admin. > Networking. You also need to add the network-monitor applet into your notification area (from which you can also configure your network) through right-click in your notification area, Add to the panel. Scroll down to Hardware and System and double click on the network monitor icon. Once you click on it, enter your interface label for your wifi connection, which you will find with the following command line ```
iwconfig
```

PS: please don't PM members when they don't answer right away, these are huge forums and we all try to do our best :)

---

### Post by Timo425 on 2007-05-08
> **Kobalt said:**
> You will now need to configure your network through System > Admin. > Networking. You also need to add the network-monitor applet into your notification area (from which you can also configure your network) through right-click in your notification area, Add to the panel. Scroll down to Hardware and System and double click on the network monitor icon. Once you click on it, enter your interface label for your wifi connection, which you will find with the following command line ```
iwconfig
```

PS: please don't PM members when they don't answer right away, these are huge forums and we all try to do our best :)

I see you mentioned wifi here. It is about wifi? My primary issue is wired in a moment.

---

### Post by Kobalt on 2007-05-08
I suggest you connect with an ethernet cable ? Do you only have one ethernet plug ?
If you can't connect to your network it is because your /etc/network/interfaces file must be empty. Let's try to add an ethernet interface first. Open the Terminal and open the file with ```
gksu gedit /etc/network/interfaces
```
In this file add (after a blank line) this part [quote]auto eth0
iface eth0 inet dhcp[/code]
If you connect with a static IP then come back here for more help on configurating your connection.
Finally save & close the file and restart your network with ```
sudo /etc/init.d/networking restart
```.
Now you should be up and running.

---

### Post by Timo425 on 2007-05-08
It helped, thanks! However I already had those lines in /etc/networking/interfaces. Strange.
Btw I haven't been in net via wifi a second in Ubuntu, I have always been with ethernet cable, uninstalling network-manager cutted cable off, too. Maybe I just needed this networking restart. :)
Now I take a look to this link you gave.

---

### Post by Timo425 on 2007-05-08
No it didn't help (and I have seen this page and followed it some weeks ago).

I don't use static, but dhcp, this info there seems to be only for static.

> timo@timo-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 6133
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:14:38:0c:9e:36
Sending on   LPF/eth0/00:14:38:0c:9e:36
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.10 port 67
Ignoring unknown interface ath0=ath0.
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:14:38:0c:9e:36
Sending on   LPF/eth0/00:14:38:0c:9e:36
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
wlan0: ERROR while getting interface flags: No such device
ioctl[SIOCSIWPMKSA]: No such device
ioctl[SIOCSIWMODE]: No such device
Could not configure driver to use managed mode
ioctl[SIOCGIFFLAGS]: No such device
Could not set interface 'wlan0' UP
ioctl[SIOCGIWRANGE]: No such device
ioctl[IEEE80211_IOCTL_SETPARAM]: No such device
ioctl[SIOCSIWAP]: No such device
ioctl[SIOCGIFFLAGS]: No such device
Failed to initialize driver interface
wpa_supplicant: /sbin/wpa_supplicant daemon failed to start
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
wlan0: ERROR while getting interface flags: No such device
Failed to bring up wlan0.
                                                                         [ OK ]




Let me also show interfaces file, which I changed due to the page you linked:

> auto lo
iface lo inet loopback

# orig oli sees:
# auto eth1
# iface eth1 inet dhcp


# orig oli sees:
# auto eth2
# iface eth2 inet dhcp

# lan:
auto eth0
iface eth0 inet dhcp

# Timo lisas:

auto wlan0
iface wlan0 inet static
address 192.168.168.40
gateway 192.168.168.230
dns-nameservers 192.168.168.230
netmask 255.255.255.0
wpa-driver madwifi
wpa-ssid ####
wpa-ap-scan 2
wpa-proto WPA
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk #################################################
[IMPORTANT: See "WPA-PSK key generation"]

######################
# WIFI
# Selle osa tegi Timo (mina) trellitatuks.

#auto ath0
#iface ath0 inet dhcp
#wpa-driver madwifi
#wpa-ap-scan 2
#pre-up sleep 10
#pre-up wpa_supplicant -dd -Bw -D madwifi -iath0 -c/etc/#wpa_supplicant.conf 
#

#wireless-essid #########
#wireless-key s:##################
# post-down killall -q wpa_supplicant

I also changed the term "madwifi" to "wext", no difference, i guess.

What next?

---

### Post by Kobalt on 2007-05-08
Did you set your wifi connection for static IP or DHCP ? Here it is set to be on static IP...
Which one is your wifi interface : wlan0 or ath0 (my guess would be ath0 according to your card) ? only wlan0 is configured here, not ath0...

---

### Post by Timo425 on 2007-05-08
My bad, there is about dhcp, and lot of.
It looks like there was a tiny something moving through wifi, when I did this (one page loaded helluva slow and ugly):

Part of interfaces:
> auto ath0
iface ath0 inet dhcp
wpa-driver madwifi
wpa-ssid ####
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk #########################################

I also try RSN instead of WPA...... nothing.

And terminal (WPA in interfaces):
> timo@timo-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 8357
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:14:38:0c:9e:36
Sending on   LPF/eth0/00:14:38:0c:9e:36
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.10 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:14:38:0c:9e:36
Sending on   LPF/eth0/00:14:38:0c:9e:36
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
wpa_supplicant: plaintext or ascii wpa-psk has 65 characters, it must have between 8 and 63
wpa_supplicant: if wpa-psk truly is a 256-bit hexadecimal key, it must have 64 characters
There is already a pid file /var/run/dhclient.ath0.pid with pid 6218
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:12:79:41:c2:70
Sending on   LPF/ath0/00:12:79:41:c2:70
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]




But I should have AES-CCMP instead of TKIP. So I try this now... Same thing.
Now I try wpa-ap-scan 2 instead of 1.

> timo@timo-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 9628
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:14:38:0c:9e:36
Sending on   LPF/eth0/00:14:38:0c:9e:36
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.10 port 67
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.ath0.pid with pid 9711
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:12:79:41:c2:70
Sending on   LPF/ath0/00:12:79:41:c2:70
Sending on   Socket/fallback
DHCPRELEASE on ath0 to 192.168.1.10 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:14:38:0c:9e:36
Sending on   LPF/eth0/00:14:38:0c:9e:36
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
wpa_supplicant: plaintext or ascii wpa-psk has 65 characters, it must have between 8 and 63
wpa_supplicant: if wpa-psk truly is a 256-bit hexadecimal key, it must have 64 characters
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:12:79:41:c2:70
Sending on   LPF/ath0/00:12:79:41:c2:70
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]


interfaces (important part):
> auto ath0
iface ath0 inet dhcp
wpa-driver madwifi
wpa-ssid ####
wpa-ap-scan 2
wpa-proto WPA
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk #########################

It so complicated that I'm confused..

Anyway I should have:
SSID: (Hidden)
key: SWPA Pre-Shared key (ABS)  
WPA1 - Personal
Crypto: AES-CCMP

---

### Post by Timo425 on 2007-05-08
I am trying to follow this guide:
[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

But I get this error:
root@timo-laptop:/home/timo/veel/ubuntu/src/madwifi-0.9.3/scripts# ./madwifi-unload.bash
FATAL: Module wlan_scan_sta is in use.
FATAL: Module wlan is in use.

But I did those before it:
ifconfig ath0 down
ifconfig wifi0 down

:confused:

---

### Post by Timo425 on 2007-05-08
I had to remove several modules. Ok now this far..

---

### Post by Timo425 on 2007-05-08
Still doesn't help.. Can someone please help ](*,)

---

### Post by Timo425 on 2007-05-08
I got it up, I guess! Thanks to 
[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)
and
[http://madwifi.org/wiki/UserDocs/802.11i](http://madwifi.org/wiki/UserDocs/802.11i)

BUT:
> root@timo-laptop:/home/timo/veel/ubuntu/src/wpa_supplicant-0.5.7# wpa_supplicant -w -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf
Trying to associate with SSID '####'
Associated with 00:14:bf:25:fa:61
WPA: Key negotiation completed with 00:14:bf:25:fa:61 [PTK=CCMP GTK=CCMP]
CTRL-EVENT-CONNECTED - Connection to 00:14:bf:25:fa:61 completed (auth) [id=0 id_str=] 

And this stays that way, not ending the process.. wifi light is blinking, but I still can't get to net. :confused:

---

