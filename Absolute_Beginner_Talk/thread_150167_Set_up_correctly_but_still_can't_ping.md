---
title: "Set up correctly but still can't ping?"
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by rj686 on 2006-03-25
Hey guys i followed [https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto]("https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto")
to set up my WUSB54G, i installed ndisgtk and ndiswrapper-utils no problem. I got my driver off the disk and everything looked like it was set up correctly. My wlan0 device is listed in System > Administration > networking so i thought all was good. I entered my ssid and such, but i still cant ping anything? Could someone help me?

---

### Post by flammenwurfer on 2006-03-25
I am also having the same problem, only with a Hawking HWP54G PCI card.  Everything is setup correctly, but I can't ping or acces the internet.

---

### Post by wsanders on 2006-03-25
can you post the output of 
```

ifconfig

```
and
```

iwconfig

```

---

### Post by rj686 on 2006-03-25
```
ryan@RyAnScOmP:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:873 errors:0 dropped:0 overruns:0 frame:0
          TX packets:873 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:66384 (64.8 KiB)  TX bytes:66384 (64.8 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:0F:66:73:03:34
          inet6 addr: fe80::20f:66ff:fe73:334/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

ryan@RyAnScOmP:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:2 Mb/s
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

---

### Post by Magrioteli on 2006-03-25
[QUOTE=rj686]- - - 
         [COLOR="Red"] inet addr:127.0.0.1  Mask:255.0.0.0 [/COLOR]
. . . . [/CODE][/QUOTE]

That IP/inet addr is only for you network card. (local host)
But how do you manage writing here - another comp?

Have you searched the forum for your type of card?

---

### Post by rj686 on 2006-03-25
yes i had to copy and paste that since that computer has NO intenet connection at the moment, i've seen many people use ndiswrapper w/ the usb adapter that i have, i think i have it set up right just for some reason i cant ping anything or search teh web...

---

### Post by wsanders on 2006-03-25
It looks like you aren't associated with an access point. Was it successful after you entered the SSID into the network manager? Make sure you activate  the changes after entering the SSID.

---

### Post by rj686 on 2006-03-25
[QUOTE=wsanders]It looks like you aren't associated with an access point. Was it successful after you entered the SSID into the network manager? Make sure you activate  the changes after entering the SSID.[/QUOTE]


i hit ok, it took a long time then it closed teh window....

its weird cuz it picks up all the networks near me it just doesnt let me connect to one of them...

---

### Post by wsanders on 2006-03-25
Usually when it takes a long time, that indicates it wasn't actually successful. Is there any encryption and/or security on this network?

---

### Post by rj686 on 2006-03-25
it did have encryption but i turned it off, but on the network list it still lists that its encrypted (with a little key next to it). IS there a way to refresh the list? I have aim if that would be easier than just posting everytime, pm if u wanna do that instead of posting

---

### Post by flammenwurfer on 2006-03-25
It is also taking a long time when I activate my wlan0 and when I click OK after entering my AP info .  Here is what I get from ifconfig and iwconfig



iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"KempoTiger"  Nickname:"acx100 v0.2.0pre8"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      no wireless extensions.

sit0      no wireless extensions.

ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:106888 errors:0 dropped:0 overruns:0 frame:0
          TX packets:106888 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:7979991 (7.6 MiB)  TX bytes:7979991 (7.6 MiB)

wlan0     Link encap:Ethernet  HWaddr 00:E0:98:F2:85:0C
          inet6 addr: fe80::2e0:98ff:fef2:850c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0xc000

---

### Post by rj686 on 2006-03-25
i hate to say it.... but bump

---

### Post by harisund on 2006-03-25
Hello everyone 

Here's what I would suggest you do. And use the command line please :D

First, the good news is your card is recognized. 
Second, use sudo everywhere as appropriate. 

```
iwlist wlan0 scan | grep ESSID
```
This should show you the list of access points that your wireless card sees. Do you see yours? Try it a couple more times.. each time you may see more or less networks than the previous time (depending on how geeky your neighbours are... :D)

Then do these: 
```
iwconfig wlan0 mode Managed
```
```
iwconfig wlan0 essid <name_of_your_essid>
```
```
iwconfig wlan0 key restricted <enter your wep key if you have it>
```
```
dhclient wlan0
```

Then you should get a message, informing you of what IP address you have acquired. You are then good to go. 

Do post back. 

hari .S

---

### Post by rj686 on 2006-03-25
w00t that worked for me :), but i had to re-do it when i restarted, and the restart was unusually slow```

ryan@RyAnScOmP:~$ sudo iwlist wlan0 scan | grep ESSID
Password:
                    ESSID:"GANTOR"
                    ESSID:"admin"
                    ESSID:"dlinkb"
                    ESSID:"default"
                    ESSID:"patrick"
                    ESSID:"Wireless"
                    ESSID:"CheptaiS"
                    ESSID:"Todd"
                    ESSID:"NETGEAR"
                    ESSID:"default"
                    ESSID:"FUCKOFFSTOPSTEALING"
                    ESSID:"2WIRE240"
                    ESSID:"linksys"
ryan@RyAnScOmP:~$ sudo iwconfig wlan0 mode managed
ryan@RyAnScOmP:~$ sudo iwconfig wlan0 essid FUCKOFFSTOPSTEALING
ryan@RyAnScOmP:~$ sudo iwconfig wlan0 key restricted **********
ryan@RyAnScOmP:~$ dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

can't create /var/lib/dhcp3/dhclient.leases: Permission denied
Can't create /var/run/dhclient.pid: Permission denied
drop_privileges: could not set group id: Operation not permitted
ryan@RyAnScOmP:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:0f:66:73:03:34
Sending on   LPF/wlan0/00:0f:66:73:03:34
Sending on   Socket/fallback
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.1.1
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.1.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.108 -- renewal in 34130 seconds.
ryan@RyAnScOmP:~$

```

so it did work though, seeing as how im using that computer to type this now :), but i wonder why it didnt work through the gui front end?

---

### Post by harisund on 2006-03-25
Yay! Glad that worked out for you.. 

Anyway, a couple of details :D

1. Most interesting. You have quite a few networks around your house. Apparently, the guys owning stuff like NetGear, Linksys and default are n00bs. Oh well. 
2. I like your essid. ;-)
3. I am surprised, for it typically shouldn't have to make that many DHCPREQUESTS and DHCPACK. Glad it worked though. 
4. No idea why it didn't work through the GUI. As somebody mentioned, if it takes a while using the GUI, most probably it doesn't work. Sometimes, don't you agree that the command line is better, for it tells you what is going on? 
5. The grep ESSID filter in the first command is used basically only to show you the ESSID. If you simply do a iwlist wlan0 scan you will see a bunch of details (most of which I don't understand anyway)
6. What do you mean "redo it when I restarted?" If you mean type the commands again.. hmm, yeah I agree. I haven't figured out a way to get it started on boot time yet. Perhaps we could write it as a script and put it in /etc/rcS.

---

### Post by rj686 on 2006-03-25
lol, thanks, my dad saw that essid and fell out of his chair, he knew it was his son that wrote that. But yes i was talking about the reboot, its only a few commands but for n00bs its still a pain. I dont mind doing it command line though that way you can de-bug it ;).

---

### Post by flammenwurfer on 2006-03-26
I'm having a problem.  I'm not getting anything when I do "iwlist wlan0 scan | grep ESSID"  or even when I do "iwlist wlan0 scan".

Ndiswrapper says my driver is loaded and hardware is present, but it can't find or connect to any APs.  This same computer and Network card is working in Mepis right now, so I know it's not a hardware or router problem.

---

### Post by harisund on 2006-03-26
flammenwurfer, can you post the output of 
```
iwconfig
```

and the output of 

```
ifconfig
```

here?

---

### Post by flammenwurfer on 2006-03-27
iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

wlan0 IEEE 802.11b+/g+ ESSID:"KempoTiger" Nickname:"acx100 v0.2.0pre8"
Mode:Managed Frequency:2.412 GHz Access Point: 00:00:00:00:00:00
Bit Rate=54 Mb/s Tx-Power=15 dBm Sensitivity=1/3
Retry min limit:7 RTS thrff
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

eth1 no wireless extensions.

sit0 no wireless extensions.

ifconfig
lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:106888 errors:0 dropped:0 overruns:0 frame:0
TX packets:106888 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:7979991 (7.6 MiB) TX bytes:7979991 (7.6 MiB)

wlan0 Link encap:Ethernet HWaddr 00:E0:98:F2:85:0C
inet6 addr: fe80::2e0:98ff:fef2:850c/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:18 Base address:0xc000

---

### Post by harisund on 2006-03-27
Hmm.. It doesn't seem to a problem with detecting hardware. Your wireless card seems to be detected and working. 

I would think not using sudo could be a minor hurdle. When you are doing ```
iwlist wlan0 scan
``` you are prefixing it with sudo, or are running it as root, right? 

But anyhow, a scan doesn't really require root permissions. Is your router is turned on and is broadcasting your essid? (Meaning, if you hvae another computer, is that able to connect to the wireless?) 

Anyhow, what is KempoTiger? Is it something you simply created to hide your regular essid, or is that the essid you wish to connect to? 

Even otherwise, assuming you have a wep key of <key> try doing the following
```

sudo iwconfig wlan0 mode Managed essid KempoTiger key restricted <key>
sudo dhclient wlan0

```
I am assuming that might get you an ip address. What do you do in mepis to get it to work anyway?

---

### Post by flammenwurfer on 2006-03-27
KempoTiger is the actual ESSID.  There are 3 other computers in the house that can connect to the router.  In Mepis I go to the OS Center and enter the essid and wep key and click start wlan0 and it just works.  

I've tried doing what you just suggested but still no dice.  I'll try it again when I get home though.  

Would it help for you to see the iwconfig of Mepis where it works?

---

### Post by harisund on 2006-03-27
You could post it in here, but I dont really see how helpful it could be. 


What happens when you type in the above 2 commands I had mentioned? That is what the control center in Mepis does in the background too (the iwconfig command followed by the dhclient command)

---

### Post by flammenwurfer on 2006-03-27
Well, when I do the Iwconfig command it doesn't give me anything, but no errors.  When I did the dhclient command It went through everything but it took a long time and said there were no leases or something to that effect.

---

