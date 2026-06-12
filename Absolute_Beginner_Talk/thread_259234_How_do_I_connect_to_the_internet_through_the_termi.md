---
title: "How do I connect to the internet through the terminal?"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by etotehpii on 2006-09-17
I've been searching around but havn't found the command to activate and deactivae my connection to the internet.
I use ra0 wireless and I need to deactivate and reactivate it in order to use it when I boot up.  I would like to know so I can connect to the internet in case Xserver breaks for whatever reason.

Thanks

---

### Post by ciscosurfer on 2006-09-17
Try```
sudo ifup ra0
```to bring it up and ```
sudo ifdown ra0
```to release it.

---

### Post by etotehpii on 2006-09-17
Its not working for me.  After I run that command it will say that the connection is active under Network Settings but lynx and firefox will not be able to access the internet.  I have tried deactivating from terminal and Network Settings and activating through the terminal, its a no go.   I can connect fine when I activate from Network Settings though.

```
 sudo ifup ra0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/ra0/00: etc....
Sending on   LPF/ra0/00: etc....
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```


Thanks

---

### Post by Zaffe on 2006-09-17
I dont really use it, but maybe this will work

```

1) iwlist ra0 scan
2) iwconfig ra0 essid (ESSID)
3) iwconfig ra0 key open (WEP-KEY)
4) ifup ra0

```

Shuld be something like that, probably u have to change point 3, check "man iwconfig".

---

### Post by etotehpii on 2006-09-17
```
iwlist ra0 scan
ra0       Scan completed :
          Cell 01 - Address: 0 etc.
                    Mode:Managed
                    ESSID:"Name"
                    Encryption key:on
                    Channel:1
                    Quality:25/100  Signal level:-74 dBm  Noise level:-193 dBm
          Cell 02 - Address: 00:13:10:94:1C:01
                    Mode:Managed
                    ESSID:"DCRhomenetworklinksys"
                    Encryption key:off
                    Channel:6
                    Quality:0/100  Signal level:-74 dBm  Noise level:-193 dBm
 iwconfig ra0 essid (Name)
bash: syntax error near unexpected token `('

 iwconfig ra0 essid Name
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device ra0 ; Operation not permitted.
iwconfig ra0 essid (Name)
bash: syntax error near unexpected token `('
 
man iwconfig ra0 key open (key)
bash: syntax error near unexpected token `('

 man iwconfig ra0 key open Key
Reformatting iwconfig(8), please wait...
No manual entry for ra0
No manual entry for key
--Man-- next: open(1) [ view (return) | skip (Ctrl-D) | quit (

sudo ifup ra0
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on etc...
Sending on   etc...
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 21
receive_packet failed on ra0: Network is down
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleep

 sudo ifup ra0
ifup: interface ra0 already configured



```

Still no connection.

---

### Post by Zaffe on 2006-09-17
Try this:
```

sudo iwconfig ra0 essid Name
sudo iwconfig ra0 key PASSWORD
sudo ifdown ra0
sudo ifup ra0

```

```

man iwconfig

```
Will show you a manual of the command iwconfig

---

### Post by wildseven on 2006-09-17
> **etotehpii said:**
> ```
iwlist ra0 scan
ra0       Scan completed :
          Cell 01 - Address: 0 etc.
                    Mode:Managed
                    ESSID:"Name"
                    Encryption key:on
                    Channel:1
                    Quality:25/100  Signal level:-74 dBm  Noise level:-193 dBm
          Cell 02 - Address: 00:13:10:94:1C:01
                    Mode:Managed
                    ESSID:"DCRhomenetworklinksys"
                    Encryption key:off
                    Channel:6
                    Quality:0/100  Signal level:-74 dBm  Noise level:-193 dBm
 iwconfig ra0 essid (Name)
bash: syntax error near unexpected token `('

 iwconfig ra0 essid Name
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device ra0 ; Operation not permitted.
iwconfig ra0 essid (Name)
bash: syntax error near unexpected token `('
 
man iwconfig ra0 key open (key)
bash: syntax error near unexpected token `('

 man iwconfig ra0 key open Key
Reformatting iwconfig(8), please wait...
No manual entry for ra0
No manual entry for key
--Man-- next: open(1) [ view (return) | skip (Ctrl-D) | quit (

sudo ifup ra0
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on etc...
Sending on   etc...
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 21
receive_packet failed on ra0: Network is down
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleep

 sudo ifup ra0
ifup: interface ra0 already configured



```

Still no connection.


ok you have some boo boo's lol.

for the ESSID
you need to be root or sudo to do it that's why you have permission denied. so do.

```
sudo iwconfig ra0 essid Name
```
ok thats step number one.
then since that AP is on channel 1, you need to change channels.
```
sudo iwconfig ra0 channel 1
```
then it says that encyption is ON, so you can't just type "open" you actually need the key. It will probably be a 128 bit WEP key.  If that is your router you should be able to ask whoever set it up the password. Otherwise try the other AP that you see with "scan"
well if you get the key you do:
```
sudo iwconfig ra0 key <put key here, but dont put "<>" >
```
then do
```
sudo ifconfig ra0 up
sudo dhclient ra0
```

and that should be it.
good luck^^

---

### Post by mattkenn4545 on 2006-09-17
try

sudo /etc/init.d/networking restart

---

### Post by ciscosurfer on 2006-09-17
Have you also tried unplugging your router, then plugging it back in (waiting at least 20 seconds or so to reset the router)?

---

### Post by etotehpii on 2006-09-17
That did it wildseven, thanks for your help and everyone else for trying.

---

### Post by wildseven on 2006-09-17
oh yeh heh. i forgot. if you choose another AP instead of "Name" and you use the other one, i forgot the name, make sure you change the info to that of the other AP.
change the essid, key=off if there is no encryption, or you can try open. make sure you change to the channel it operates on.
good luck ^^

---

### Post by wildseven on 2006-09-17
hah np. congratualtions and good luck in the future ^^

-wildseven

---

### Post by etotehpii on 2006-09-17
This worked if anyone else wanted to know:

```
 
sudo iwconfig ra0 essid Name
Error : unrecognised wireless request "Na"
sudo iwconfig ra0 essid "Name"
sudo iwconfig ra0 channel 1
sudo iwconfig ra0 key PASSWORD
sudo ifconfig ra0 up
sudo dhclient ra0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on etc....
Sending on   etc...
Sending on   Socket/fallback
DHCPREQUEST on ra0 to 255.255.255.255 port 67
DHCPACK from IP
bound to IP -- renewal in 40068 seconds.

```

---

### Post by stani on 2006-11-23
Grrr, still doesn't work here:
```
~$ iwlist ra0 scan
ra0       Scan completed :
          Cell 01 - Address: 00:14:A5:9D:3D:69
                    ESSID:"Livebox-f63a"
                    Mode:Managed
                    Channel:10
                    Encryption key:on
                    Bit Rates:0 kb/s
~$ sudo iwconfig ra0 essid "Livebox-f63a"
~$ sudo iwconfig ra0 channel 10
~$ sudo iwconfig ra0 key xxx
~$ sudo ifconfig ra0 up
~$ sudo dhclient ra0
There is already a pid file /var/run/dhclient.pid with pid 6204
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/ra0/00:0e:2e:8a:6e:ae
Sending on   LPF/ra0/00:0e:2e:8a:6e:ae
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT61 Wireless  ESSID:""
          Mode:Auto  Frequency:2.457 GHz  Bit Rate=54 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-41 dBm  Noise level:-111 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
I've followed this guide to install ra0 for rt1: [http://ubuntuforums.org/showthread.php?t=296822](http://ubuntuforums.org/showthread.php?t=296822)

---

