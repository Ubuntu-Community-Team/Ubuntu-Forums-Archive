---
title: "Various problems on my brand new edgy..."
date: 2007-01-10
forum: Apple PPC Users
---

### Post by el-sio on 2007-01-10
Hello everyone !

I was contemplating my ibook G4 12'' wondering what to do with it and I decided to install Ubuntu (which is the best idea I could have had isn't it  ;)  )

I have had a few linux adventures before but always with i86 arch and nvidia graphics so I was quite affraid when I started the installation wit ATI radeon mobility 9200 and G4 proc but it worked surpisingly well :)

Anyway, a few things are still not working and I ask here for advice on where I could find the good howtos to solve those problems :

first the wifi : I have followed the instructions to get the airport drivers and they are loaded

```
el-sio@rivendell:~$ lsmod | grep iee
ieee80211_crypt_wep     6464  1 
ieee80211softmac       34816  1 bcm43xx
ieee80211              35464  2 bcm43xx,ieee80211softmac
ieee80211_crypt         6912  2 ieee80211_crypt_wep,ieee80211
ieee1394              431440  2 sbp2,ohci1394
```

then the iwconfig gives the following :

```
eth1      IEEE 802.11b/g  ESSID:"rivendell"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid   
          Bit Rate:1 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I find the nickname a bit suspicious for an airport card but who knows :/

The problem is that the network applet doesn't shows the valid wireless networks which I&#12288;heard is a bug specific to edgy, so I installed wifi-radar and I saw my ssid but Nothing seems to happen when I try to connect to a wireless network (the simplest one with static IP and no security, just to try a ping :p  )
maybe I&#12288;missed a step or my configuration is just lousy...

my network files :

```
el-sio@rivendell:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:11:24:8a:76:06 arp 1
eth1 mac 00:11:24:9c:0b:0e arp 1

el-sio@rivendell:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

 auto eth1
iface eth1 inet static
wireless-essid rivendell
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1
wireless-key s:


```


My second problem concerns beryl...

I have read too many different things about where to find the latest and even latest beryl repository that I am a bit confused right now, anyway here is my source list (only the part concerning beryl... ) :

```
deb http://beryl-mirror.pricechild.co.uk edgy main
deb http://ubuntu.beryl-project.org edgy main
deb http://beryl.limitless.lupine.me.uk edgy main
deb http://mental-ppc.tuxfamily.org/dists edgy-mppc main incoming
deb http://download.tuxfamily.org/3v1deb edgy beryl-svn
deb-src http://download.tuxfamily.org/3v1deb edgy beryl-svn

```

with apt-get update, I recieve the following error :

```
Impossible de récupérer http://download.tuxfamily.org/3v1deb/dists/edgy/Release  Unable to find expected entry  beryl-svn/binary-powerpc/Packages in Meta-index file (malformed Release file?)
```

which is a svn packages repository of beryl found on another thread of this forum...

Anyway, I could install beryl and launch it without problems, but when I try to run beryl-settings, I receive the following :

```
el-sio@rivendell:~$ beryl-settings 

** ERROR **: no d_ for a_active_plugins
aborting...
Abandon (core dumped)

```

So beyl works, but I&#12288;can't load or change any feature :confused: 

my 3D is perfectly working on ppracer and other 3D games (speaking of which I love armagetron :D ) but I get this warning for each 3D program :
```

el-sio@rivendell:~$ glxgears -printfps
libGL warning: 3D driver claims to not support visual 0x4b
5066 frames in 5.0 seconds = 1013.074 FPS
5045 frames in 5.0 seconds = 1007.711 FPS
```

but I don't think it is related since 0x'b is just a code for 32bits color graphics (or so I read on the forums)...


Anyway If someone find something obvious in what I have told here, please telle me, even a RTFHowto or RTFDoc will be greatly helpful (if you provide the reference to the docummentation of course ;) )

---

