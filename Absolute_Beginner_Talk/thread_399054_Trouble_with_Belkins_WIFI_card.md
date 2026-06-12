---
title: "Trouble with Belkins WIFI card"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by led_scorched on 2007-04-01
I just installed Dapper Drake 6.06 LTS on a Toshiba Satellite A15.

I initially had issues getting the onboard ethernet card to work, but finally got it configured.  But now i am trying to get the Wifi card to work without any success.

The card is a Belkins F5D7010 Ver 4100.  When i goto Network Settings, it lets me Activate it, and claims it is working, but the card itself isnt doing anything.  I dont even get the power light on it to come on.  

Any ideas on how to get it working and connected?

---

### Post by Dual Cortex on 2007-04-01
Open up a terminal and type 
> iwconfig

Do you see any network adapters with wireless extensions?

---

### Post by led_scorched on 2007-04-01
> eth2      IEEE 802.11b/g  ESSID:"me"  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

thats what i get.

---

### Post by Dual Cortex on 2007-04-01
Do you mind using static settings instead of DHCP?
Shortens the margin of error a bit.

Open up a terminal, then type
> gksudo gedit /etc/network/interfaces

Find your network adapter (eth2) and replace according to the following guide:

```

auto eth2
iface eth2 inet static
address 192.168.0.108    <-- IP address assigned to your computer
netmask 255.255.255.0    <-- netmask.. leave this one
gateway 192.168.0.1      <-- IP of your router
wireless-essid MGTComputers <-- SSID of your wireless network
wireless-key 1234567890 <-- WEP key, if any

```

---

### Post by led_scorched on 2007-04-01
ok... done.  now what do we do?

---

### Post by Dual Cortex on 2007-04-01
Either restart or, better yet, type in a terminal:
> sudo /etc/init.d/networking restart

See if it works (try accessing your router) and it if doesn't, please post the results of 
> ifconfig
and
> sudo iwconfig
and
> iwlist eth2 scan

---

### Post by led_scorched on 2007-04-01
Results-

[QUOTE=ifconfig] 
eth0      Link encap:Ethernet  HWaddr 00:08:0D:36:95:C5
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::208:dff:fe36:95c5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:2511 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2794 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1044444 (1019.9 KiB)  TX bytes:536446 (523.8 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:672 (672.0 b)  TX bytes:672 (672.0 b)
[/QUOTE]

[QUOTE=sudo iwconfig]lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.
[/QUOTE]

[QUOTE=iwlist eth2 scan]eth2      Interface doesn't support scanning.
[/QUOTE]

---

### Post by Dual Cortex on 2007-04-01
Well, it seems that you're network adapter disappeared. Sure it's enabled?

---

### Post by led_scorched on 2007-04-01
started over.  Wifi card moved to Eth1 for some reason

[QUOTE=iwconfig]eth1      IEEE 802.11b/g  ESSID:"patterson"  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/QUOTE]

[QUOTE=iwlist eth1 scan]eth1      No scan results
[/QUOTE]

---

### Post by led_scorched on 2007-04-02
I got my card working.

followed [these instructions]("http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=5").  works like a charm now! :)

---

