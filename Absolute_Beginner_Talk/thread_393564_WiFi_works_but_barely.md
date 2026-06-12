---
title: "WiFi works but barely"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by nayo on 2007-03-25
Hi all.  My wifi was working totally groovily on a dell d600 running dapper for weeks.  We had an electrical outage while I was out and everything presumably rebooted, including the router and DSL modem (had to massage them to get them back on board with all their lights on but now they are running the other computer on the network fine).

Anyway, on my Ubuntu laptop the wireless is suddenly not working! At least, Firefox is not leading pages and internet requiring applets are not working. But,  smallish packets are being sent and received according to the System Monitor and Connection Properties and the signal strength is fine.

What did I do wrong?  How can I fix it?  I want to search the web again!

Any help much appreciated.

---

### Post by cowlip on 2007-03-25
perhaps DHCP is messed up?  Can you ping you router's IP address?

What do ifconfig and iwconfig output?  And paste the file /etc/network/interfaces here as well..

---

### Post by nayo on 2007-03-25
sorry -- I dont know how to ping my main computer or router -- just to be honest.  I can get to the ping section of the network tools but how do I find my address on a windows machine?  i tried to ping 192.168.0.1 and it didn't work

also, I'm sorry I can't cut and paste things since the ubuntu laptop is of course, down

iwconfig has wlan0 and eth1 recognized as wi-fi.  I am using wlan0 which is active -- it was what I was using for weeks at a time too

---

### Post by tgalati4 on 2007-03-25
It's also possible that your wireless router took a voltage spike.  Any wireless devices are subject to antenna drift.  Try other wireless devices with the router to determine if you are getting full throughput.  Sometimes hitting the reset button (using a paperclip through the hole) will reset the antenna's digital trimmers.

The DSL router could have also taken a hit.  Modems are sensitive to voltage spikes.  Try a direct wire connection to the DSL modem and try one of the internet speed sites to get a baseline throughput.  Most DSL's can support 768 kilobits per second.  I get around 2,200 kilobits per second with SBC in Southern California.

Let us know what you discovered.

---

### Post by nayo on 2007-03-25
ok, so I pinged 192.168.1.1 5 times and they all came back with an average of 5 ms

the following is what works with the hookups:

dsl modem > Win XP  FINE

dsl modem > linksys router > Win XP FINE -- this is the hookup I have presently while trying to get the Ubuntu wifi zooming again

however, if I use the Win XP machine's wifi just to try to pickup the
dsl modem > router radio signal I get a weak signal (yellowish) and when I try to connect to the internet, nothing happens  (signal data is -76 dBm and noise is -95 dBm and SNR is 19 dB)
  
this would suggest I guess that the router radio is somehow bad, wouldn't it?

does it make sense that the XP machine when connected to the router would still work while still having the router radio not be active?  I'm just making all this up off the top of my head.  What do you think?

Thanks!

---

### Post by nayo on 2007-03-25
ok i pinged 192.168.1.111 and there was no packet loss etc.  Could this be a problem if the Win XP says it's at 192.168.1.1?  When I ping that, it takes longer and there's packet loss.

ifconfig looks ok -- sorry I cant cut and paste -- what do I look for in the output?

---

### Post by tgalati4 on 2007-03-26
20 dB is not great for SNR.  Try moving the radio antenna.  Ideally it should be on a high shelf away from other computer equipment.  It sounds like your DSL modem works in wired mode, and your router also works in wired mode.  This isolates the wireless radio.  Is there a reset switch on the router?  This may reset the trimmers to get your frequencies aligned.  Also, if you have a removeable antenna, try disconnecting and reconnecting.  Sometimes contact resistance on the antenna can cause problems.

Your ifconfig should look like:

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:472 (472.0 b)  TX bytes:472 (472.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:XX:2F:38:XX:80
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9974 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5987 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8892134 (8.4 MiB)  TX bytes:801439 (782.6 KiB)
          Interrupt:11 Memory:22010000-22020000


There should be no errors.

---

### Post by nayo on 2007-03-26
aha!  I get 72 errors on my wlan0
and now I've activated the ethernet and connected the wire  from the router to here so I can cut and paste etc.

anyway, this is what i've got for ifconfig


eth0      Link encap:Ethernet  HWaddr 00:0D:56:7A:7E:83
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:fe7a:7e83/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8425 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7445 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7963018 (7.5 MiB)  TX bytes:1736665 (1.6 MiB)
          Interrupt:11

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1312 (1.2 KiB)  TX bytes:1312 (1.2 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:11:A3:02:21:C6
          inet addr:192.168.1.111  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:a3ff:fe02:21c6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:633 errors:72 dropped:0 overruns:0 frame:72
          TX packets:3697 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:20524 (20.0 KiB)  TX bytes:292609 (285.7 KiB)

---

### Post by nayo on 2007-03-26
here is my interfaces

auto lo
iface lo inet loopback


iface eth1 inet dhcp
wireless-essid linksys

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp


iface wlan0 inet dhcp
wireless-essid linksys













auto wlan0

auto eth1

iface eth0 inet dhcp

auto eth0

---

### Post by nayo on 2007-03-26
on my XP computer, it can read the radio signal and the diagnostics seem fine but then it wouldnt load a webpage as well... is this sort of the same sort of situation as the original problem with the ubuntu laptop?

---

### Post by tgalati4 on 2007-03-26
It's also possible that you are getting interference from your neighbors.  Perhaps someone nearby set up a wireless node on the same channel (probably 6) as you.  If so, move your channel to 1 or 11.

There are several tools you can use to get more wifi information.  Under Ubuntu, Wifi Radar is a simple one, also there is a Gnome panel applet called Network Manager that will show packets passed and signal strength.  There are more dedicated tools, but they take some configuration effort to work.

At least we have narrowed it down.

You can log in to your wireless router (in a browser [http://192.168.1.1](http://192.168.1.1), admin, password) and look for statistics.  See if there are TX or RX errors.  This will help narrow down the router radio or the computer radio as the culprit.

With wireless, you have a transmitter and receiver on the router and a transmitter and receiver on the computer.  If one of these 4 channels is bad, then you lose communication.  Ever had a phone call where you couldn't hear the other party, but they could hear you?

First use WiFi Radar, or similar Windows tool to see if there are competing wireless networks nearby that are causing errors.  We need to determine this before suspecting hardware.

Good luck.

---

