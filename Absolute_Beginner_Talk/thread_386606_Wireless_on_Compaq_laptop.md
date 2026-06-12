---
title: "Wireless on Compaq laptop"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by sifo on 2007-03-17
Hi everyone, I just made the switch to Linux. I did a clean installation of Ubuntu 6.2 on my lap Compaq Presario M2015LA. I do have a friend that helped me from the start, however we did not make much progress. This what we tried so far:

we have run the "lspci" command and have verified that the wireless card is an intel 2200BG wireless card. UBUNTU recognizes it as a wireless interface but that when trying to configure the interface it refuses to set a password for the WEP encryption, ie you run the command iwconfig xxx key xxxxx and when you check the configuration there is no key there...

any suggestion?

Thanks

---

### Post by Griffiss on 2007-03-17
post the outputs of ```
sudo iwconfig
``` to see if the device is working and ```
iwlist scan
``` to see if your wireless network is detected. 

Also post your /etc/network/interfaces file:```
sudo gedit /etc/network/interfaces
```Then someone can help you.

---

### Post by sifo on 2007-03-18
OK here it goes...

sudo iwcofig...

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

iwlist scan...

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results
sit0      Interface doesn't support scanning.

sudo gedit /etc/network/interfaces...

auto lo
iface lo inet loopback


iface eth0 inet dhcp


iface eth1 inet dhcp
wireless-essid finegold
wireless-key f19a5ce072
pre-up wpa_supplicant -Bw -Dwext -ieth1 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


Thanks for the help....

---

### Post by Griffiss on 2007-03-19
Well sifo I'm new too so the help I can give is limited. I was hoping someone more experienced would spot your data and help you out...

Have you tried ```
sudo iwconfig eth1 essid "*yournetworkname*"
sudo iwconfig eth1 key *yournetworkkey*
sudo dhclient eth1
```

the first line should set your network name (include the quotes), the second line sets your key (no quotes), and the third one tries to connect to the network. If that doesn't work, post your outputs and see if someone better comes along...

---

### Post by srt4play on 2007-03-19
Are you using 6.10 edgy eft or dapper drake 6.06?

Have you tried configuring your wireless card in System -> Administration -> Networking?

---

### Post by sifo on 2007-03-19
Thanks for the tip, I tried the code suggested and this is what I got:

Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:0e:35:b5:26:53
Sending on   LPF/eth1/00:0e:35:b5:26:53
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


Any Idea anyone?

---

### Post by sifo on 2007-03-19
I am using Ubuntu 6.10 Edgy Eft.  The first thing I tried was the Admin- Networking
thanks

---

### Post by scrooge_74 on 2007-03-19
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

[http://www.ubuntuforums.org/showthread.php?t=202834](http://www.ubuntuforums.org/showthread.php?t=202834)

hope this helps

it seems you almost have it working

---

### Post by Griffiss on 2007-03-20
the links scrooge gives are very good - I got my wireless working using wieman's HowTo. But they're for WPA and you said in your first post you had WEP? 

In any case, have you tried turning off your encryption to see if you can connect without it? - this will let you know whether it's just an issue with the encryption.

---

