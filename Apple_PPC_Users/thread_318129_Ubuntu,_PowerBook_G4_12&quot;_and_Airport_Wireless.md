---
title: "Ubuntu, PowerBook G4 12&quot; and Airport Wireless"
date: 2006-12-13
forum: Apple PPC Users
---

### Post by Gerbo on 2006-12-13
Hello all!

I've been reading and following various tutorials posted both here on the Ubuntuforums and other places but with no success of getting the WiFi card on the PowerBook G4 working with Ubuntu.  The very same things happened in Dapper Drake, Edgy Eft and the latest Feisty Fawn (which the machine is currently running on).

I have the *network-manager-gnome* installed, and this is what dmesg gives me when I try to run *dhclient eth1*:

```
[ 2431.673150] SoftMAC: Open Authentication completed with 00:11:09:29:b7:d8
[ 2434.725346] SoftMAC: Open Authentication completed with 00:11:09:29:b7:d8
[ 2445.077169] SoftMAC: Open Authentication completed with 00:11:09:29:b7:d8
[ 2455.445122] SoftMAC: Open Authentication completed with 00:11:09:29:b7:d8
[ 2465.797293] SoftMAC: Open Authentication completed with 00:11:09:29:b7:d8
[ 2476.149171] SoftMAC: Open Authentication completed with 00:11:09:29:b7:d8
[ 2486.501166] SoftMAC: Open Authentication completed with 00:11:09:29:b7:d8
[ 2505.378370] ADDRCONF(NETDEV_UP): eth1: link is not ready
```

The bcm43xx driver *is* loaded with the latest firmware downloaded with the scripts provided by the developers.  ndiswrapper is *not* loaded (nor installed).

*iwlist eth1 scan* returns the following:

```
eth1      Scan completed :
          Cell 01 - Address: 00:11:09:29:B7:D8
          ESSID:"lundheim24"
          Protocol:IEEE 802.11bg
          Mode:Master
          Channel:1
          Encryption key:off
          Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                    6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                    48 Mb/s; 54 Mb/s
          Quality=100/100  Signal level=-30 dBm  Noise level=-71 dBm
          Extra: Last beacon: 348ms ag
```

I've also attempted to run the *iwconfig eth1 rate 11M*-command with no apparent success.

*iwconfig eth1* returns this:

```
eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Invalid   
          Bit Rate:1 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

In /etc/default/wpasupplicant, I have the following:

```
ENABLED=0
```

So, I'm trying to connect - unencrypted - to an open network called *lundheim24* from an Apple PowerBook G4 using the bcm43xx-driver.  I find it odd that I can both scan and see the network, but not actually connect to it.

I'm very grateful for help on this, as I can't seem to figure this out by using any of the other tutorials or advice given on these forums.

Cheers.

---

### Post by KaOS-bEat on 2006-12-23
Hi On Edgy I just do it with a simple script, I run it manually (as root) as I don't need to be connected all the time. also I have to run it 2 times for some reason (first time it complains about network being down) 

script is called "airme"
```
#!/bin/bash 

rmmod bcm43xx
modprobe bcm43xx
iwconfig eth1 rate 11M
iwconfig eth1 essid lundheim24
ifconfig eth1 up
dhclient eth1
```

I repeat I run it two times, I ctrl-c as soon as I see network is down on the screen, and then run it again. Works great, but it's a a dirty hack


Kaos

---

### Post by lumberjackchester on 2007-01-08
Greetings,

After about a week of reading all of the relevant threads and succeeding once to access my wireless network, I have failed to consistently get the wireless card in my Powerbook G4 12'' to work in Dapper.  It seems to be a problem form many Apple owners.  

Since I am quite new to the Linux environment, I am usually just copping and pasting the commands into the terminal.

But I am having the same problems with my Broadcom 4306 chip as Gerbo.

I did have it working once but after a reboot it never worked again.

any more help would be greatly appreciated!

---

