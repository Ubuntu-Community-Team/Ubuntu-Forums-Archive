---
title: "Wireless connection cloes - please help!"
date: 2006-01-14
forum: Absolute Beginner Talk
---

### Post by boomerian on 2006-01-14
Hello friends,
After a successful install and much reading of these various forums, I am stuck without successful internet access via Linksys WMP54G v.2 wireless adapter with Broadcomm chipset. Can someone look at the following and assist?
ian@ubu:~$ sudo modprobe ndiswrapper
ian@ubu:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:13:46:16:12:30
                    ESSID:"default"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-36 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:14:6C:13:6C:40
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-78 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:54 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:11:24:08:0A:31
                    ESSID:"harry's network"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:0/100  Signal level:-78 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

ian@ubu:~$ sudo ifup wlan0
ifup: interface wlan0 already configured
ian@ubu:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present
ian@ubu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:16 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:145215   Missed beacon:0

sit0      no wireless extensions.

ian@ubu:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:751102 errors:0 dropped:0 overruns:0 frame:0
          TX packets:751102 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:61640644 (58.7 MiB)  TX bytes:61640644 (58.7 MiB)

wlan0     Link encap:Ethernet  HWaddr 00:0F:66:6E:51:7C
          inet6 addr: fe80::20f:66ff:fe6e:517c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Memory:febfc000-febfdfff

ian@ubu:~$


I want to continue learning bash commands in Terminal, and to this point have been using a combination of Synaptic and Terminal.
Working with an old machine, on which I want to learn...
Assistance is greatly appreciated!

---

### Post by Inarius03 on 2006-01-14
In terminal, type 'network-admin' or click System>Administration>Networking, and configure all that the way it suits your connection.

In order to get my connection working, I had to:

iwconfig wlan0 key restricted 'network key here' <---WEP/WPA encryption

then **dhclient wlan0** to get it connected to my router. I still have to do this everytime I log in to get it connected, as I'm still looking for a fix to get it to do this automatically upon startup.

---

### Post by boomerian on 2006-01-14
Thanks for responding, Inarius03.
Here's what I got:
ian@ubu:~$ network-admin
iwconfig wlan0 key restricted <my WEP network key>
ian@ubu:~$ iwconfig wlan0 key restricted <my WEP network key>
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Operation not permitted.
ian@ubu:~$ dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
can't create /var/lib/dhcp3/dhclient.leases: Permission denied
Can't create /var/run/dhclient.pid: Permission denied
drop_privileges: could not set group id: Operation not permitted
ian@ubu:~$

I'm still puzzled. All the setup stuff looks right??

---

### Post by Inarius03 on 2006-01-14
[QUOTE=boomerian]Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Operation not permitted.[/QUOTE]

[Try this and see if it works]("http://www.ubuntuforums.org/showpost.php?p=456778&postcount=2")

and all those permission denied errors are probably because you have to run that in super-user.

EDIT: [This]("http://ubuntuforums.org/showthread.php?t=25683&highlight=FATAL%3A+Module+ndiswrapper") may or may not help, but hopefully it does as it fixed my problem with my wireless.

---

