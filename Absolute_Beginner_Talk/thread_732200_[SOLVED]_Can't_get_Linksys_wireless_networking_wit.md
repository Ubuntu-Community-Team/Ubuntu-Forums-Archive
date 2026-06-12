---
title: "[SOLVED] Can't get Linksys wireless networking with Linksys WPC55AG PCMCIA to work"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by I Use Dial on 2008-03-22
I've looked at some previous threads from searches, but my problem seems to be different.

I have a Thinkpad A31 running Gutsy.  The card was plugged in when I installed Ubuntu and there is restricted driver 'Atheros Hardware Access Layer (HAL) enabled.

In Admin Network Settings I have a 'Wireless connection' and the local network is listed.  I have selected the password type and password and selected DHCP in the Connection Settings.  But I don't connect to the network.

In Admin Network Tools I see three Network devices that could be the card.

Unknown Interface (wifi0).  There is no IP Information and when I click 'Configure' it reports "The interface does not exist."

Unknown Interface (ath0).  There is an IPv6 protocol address and mask.  When I click 'Configure'  I get the same window that I get when I select 'Wireless properties' in the Network Settings.

Unknown Interface (ath0:avahi).  There is an IPv4 protocol address and mask, but it is not an address assigned by my router and the netmask is wrong.  When I click 'Configure' it reports "The interface does not exist."

How do I get a wifi network card running on this computer?

---

### Post by jan quark on 2008-03-22
please post the result of these terminal commands

```
sudo lshw -C network
iwconfig
sudo iwlist scan
cat /etc/network/interfaces
```

you can also try to install [WiCD]("http://wicd.sourceforge.net/") instead of the nm-applet

---

### Post by I Use Dial on 2008-03-22
What is the nm-applet?  Is that what came with Ubuntu?


paul@thinkpad:~$ sudo lshw -C network
[sudo] password for paul:
  *-network               
       description: AR5001-0000-0000
       product: Wireless LAN Reference Card
       vendor: Atheros Communications, Inc.
       physical id: 0
       version: 00
       slot: Socket 0
       resources: irq:11
  *-network
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:02:8a:21:74:e9
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=full firmware=N/A ip=192.168.1.136 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications, Inc.
       physical id: 1
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:12:17:62:f8:a3
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.2) latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g


paul@thinkpad:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:2535  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

paul@thinkpad:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:13:10:03:C8:FD
                    ESSID:"Wireless"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=18/70  Signal level=-77 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    Extra:wme_ie=dd180050f2020101800003a4000027a4000042435e0062322f00

 paul@thinkpad:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface ath0 inet dhcp
wpa-psk c99c05411bdfe601aab42286703e8c3a629d280ff2936c2e755973f1e000bdb7
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid Wireless

auto ath0

iface eth0 inet dhcp

auto eth0

---

### Post by jan quark on 2008-03-22
after the first reading I do not see big error ( correct me please)

nm= network manager
yes it is the standard application for managing network connections
but I have heard wicd works flawlessly where nm fails
so it is worth a try

---

### Post by I Use Dial on 2008-03-22
Maybe I just don't understand what to do, but I can't get it to connect to the network.  The LAN just connects, so I thought I'd get the same thing with the PC card.  Is there something extra I should do to get the wireless connection to work?

---

### Post by I Use Dial on 2008-03-22
wicd fixed my problems.

I added the deb [http://apt.wicd.net](http://apt.wicd.net) gutsy extras repository to software sources, found wicd in Synaptic, which automically selected nm to be removed.

WiCD pops up in my internet menu and I configured very easily and now it just works.

Thank you!

---

