---
title: "Losing Ubuntu wifi on dual boot"
date: 2007-09-02
forum: Apple Intel Users
---

### Post by PaulFXH on 2007-09-02
Dual booting OSX and Ubuntu Feisty on a Macbook (2.16GHz, 1GB RAM, 160GB HD) and I'm really pleased with how well Ubuntu performs on this platform (the major downside is that because it runs so well, I hardly ever use OSX).
However, there is a problem with the wifi connection that is potentially very seriously annoying and I really hope I have just made an error in the configuration.
The problem is that, while the wireless works perfectly in Ubuntu, if I switch over to OSX (where wireless is also perfect) and then back to Ubuntu, I must re-configure the wifi connection.
OK, this is something that takes less than a minute but can be a pain:(
I think this problem is related to the fact that my access point has WEP encryption and the key (apparently) needs to be punched in under certain circumstances (such as when OSX takes over the wireless connection).
Note that if I shut-down Ubuntu and turn it back on without having used OSX, the wireless is good to go on bootup.
Can anybody help me understand this?
Thanks
Paul

---

### Post by moore.bryan on 2007-09-02
[I]do you reboot or shutdown and then start again after using mac osx?

i know with some lappies with windows, it takes over control of the wireless card and shutting-down, waiting a few moments, and the starting back up resets the card.

i guess it's possible your macbook is similar...
 [/I]

---

### Post by PaulFXH on 2007-09-02
Thanks, but I'm afraid that didn't work.
I had been rebooting when switching between OSes but when I saw your post I booted into OSX then shutdown and stayed down for about a minute.
Then I booted into Ubuntu, but had the same problem with no wifi

---

### Post by moore.bryan on 2007-09-02
[I]okay, that's a little strange.  the two os's should affect each other.  apparently, osx is doing something with the card making it reset so ubuntu doesn't know what to do with it.

could you post the outputs of ```
lspci
sudo lshw -C network
iwconfig
```?
[/I]

---

### Post by PaulFXH on 2007-09-03
Here's the information you requested:

1) lspci

```
paul@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:07.0 Performance counters: Intel Corporation Unknown device 27a3 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
02:00.0 Network controller: Atheros Communications, Inc. Unknown device 0024 (rev 01)
03:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)

```

2) sudo lshw -C network

```
paul@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@01:00.0
       logical name: eth0
       version: 22
       serial: 00:19:e3:46:4e:aa
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.13 duplex=full firmware=N/A latency=0 link=no multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:50200000-50203fff ioport:1000-10ff irq:17
  *-network
       description: Wireless interface
       product: Atheros Communications, Inc.
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@02:00.0
       logical name: wifi0
       version: 01
       serial: 00:1c:b3:b4:9e:98
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (svn r2695) ip=192.168.1.6 latency=0 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:50100000-5010ffff irq:16

```

3) iwconfig

```
paul@ubuntu:~$ iwconfig
lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"eircom1073 4700"  Nickname:""
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:0F:CC:23:B6:0C   
          Bit Rate:12 Mb/s   Tx-Power:14 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=79/70  Signal level=-17 dBm  Noise level=-96 dBm
          Rx invalid nwid:36916  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.


```

---

### Post by moore.bryan on 2007-09-03
[I]okay, that's good because ubuntu sees your card.  couple more questions, though:
[/I][LIST=1]
[*]*are you running ubuntu, kubuntu, or xubuntu*?
[*]*what "flavor" are you running; i.e. dapper (6.06), edgy (6.10), feisty (7.04), or gutsy (7.10).*[/LIST]*the answers to the top two will decide down which path we'll go.*

---

### Post by PaulFXH on 2007-09-03
Yes, I'm using Ubuntu Feisty (7.04)

---

### Post by moore.bryan on 2007-09-03
[I]okay, let's try using wicd instead of network-manager to handle your wireless stuff.

[/I][LIST=1]
[*]*add ```
deb http://wicd.longren.org feisty extras
``` to your /etc/apt/sources.list.*
[*]*update/upgrade your package lists ```
sudo aptitude update && sudo aptitude upgrade
```*
[*]*install wicd; it will ask you to remove network-manager and, maybe, a few other packages... it's okay.  if wicd doesn't solve your problem, we'll reinstall it and that reinstallation may fix your problem any way. ```
sudo aptitude install --with-recommends wicd
```*
[*]*now, let's start the tray icon so we can set things up: ```
cd /opt/wicd && ./tray.py &
```*
[*]*the wicd icon should be in your tray and if you left-click it once, the gui should pop-up.  it may take a second or two, so be patient.  you can then plug-in all the important info.*[/LIST]*if you run into any problems, just post and we'll work through them.*

---

### Post by PaulFXH on 2007-09-03
Bit of a hiccup here, I'm afraid. My Ubuntu installation on the Macbook has been rendered unbootable (I believe momentarily) due to my attempts to create more Linux-type partitions on the internal HD (using Parted magic).
So, for the moment I have to hold off doing what you suggested. Hope to be back soon. Will post

---

### Post by moore.bryan on 2007-09-03
*sorry to hear that... whenever you get a chance, just post.*

---

### Post by ivesjd on 2007-09-03
how do you get the applet to load on startup?

---

### Post by moore.bryan on 2007-09-03
[I]from the wicd site:
> [/I]
In GNOME, to get the tray icon to automatically appear at boot, go to System > Preferences > Sessions. In the "Startup Programs" tab, click the "New" button. Give it a name ("Wicd" works fine). For a command, enter "/opt/wicd/tray.py". In KDE, run the following command from a terminal:```
sudo ln -s /opt/wicd/tray.py ~/.kde/Autostart/tray.py
```
:-)

---

### Post by ivesjd on 2007-09-03
awesome. Thanks. I am really liking Wicd so far.

---

### Post by moore.bryan on 2007-09-03
[I]no problem.  i'm pretty selective about what goes in my sig, but i've been so impressed with wicd, i had to put it there.  that's not to say it doesn't have any draw-backs (signal-strength can be off a bit and it **seemingly** doesn't report the strength accurately to begin with), but it knocks the socks off of network-manager.

happy ubuntu-ing.
[/I]

---

### Post by PaulFXH on 2007-09-03
OK, I've got my Ubuntu back and I've installed wicd.
This is what's appeared in the terminal since i launched the tray icon.
```
paul@ubuntu:~$ cd /opt/wicd && ./tray.py &
[1] 7770
paul@ubuntu:~$ attempting to connect daemon...
success
Couldn't reconnect to last used network, scanning for an autoconnect network...
None
attempting to connect daemon...
success
starting...
refreshing...
disabling ip
disabling dns
no wired profiles found
1
ESSID : eircom1073 4700
making a new network entry...
disabling ip
disabling dns
0

```

Actually, I'm surprised that the terminal is still "open" given that you have an & at the end of the command. If I shut down the terminal will I lose the tray icon too?

In any event, where do I go from here?

---

### Post by PaulFXH on 2007-09-03
Well, I set up wicd as best I could for wireless internet and it seemed to be working fine in Ubuntu.
So, I decided to see if it would allow me to hang onto my wireless connection while switching over to OSX and then back to Ubuntu.
Unfortunately, it did not and gave exactly the same problem I've been seeing with network-manager.
However, with wicd, I couldn't even get my wired connection back (possibly because, as I found later, no DNS addresses were included at all -- I had been adding these through a prepend command in /etc/dhcp3/dhclient.conf which seemingly got inactivated with wicd).
Anyway, to get any sort of connection back I was forced to revert to network-manager.
Any thoughts on how I could have done better?

---

### Post by moore.bryan on 2007-09-03
*hmm... it still doesn't make much sense, but at least now we know the issue wasn't network-manager related.  i really think osx, for whatever reason, is doing something to your hardware that ubuntu isn't used to.  how to fix that?  not a clue... yet.  i'll sleep on it and give it some thought.*

---

### Post by pxwpxw on 2007-09-04
Suggestion (vague) - dhcp configuration for the wireless router, lease duration and reallocation, maybe use fixed IP. But no knowledge about wicd. Don't wish to interrupt.

---

