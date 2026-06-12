---
title: "Wireless STILL a problem!"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by mrsanfran on 2007-03-06
I've been using Ubuntu for about 2 weeks now and still have not been able to get the wireless working.  I'm using a Dell Inspiron 6000 with an Intel PRO/Wireless card on Edgy, but the Network Manager refuses to pick up my router and when it does get a signal, I receive a server error message in Firefox.

I've searched several dozen websites and posts in this forum, but nobody's solutions have fixed my problem.  Help?!

---

### Post by maniacmusician on 2007-03-06
should've asked for help sooner :) 

Please post the output of the following commands:

ifconfig

iwconfig

---

### Post by mrsanfran on 2007-03-06
Thanks so much!  I hope this helps.

ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:12:3F:DA:F4:1B  
          inet addr:10.120.146.146  Bcast:10.120.146.151  Mask:255.255.255.248
          inet6 addr: fe80::212:3fff:feda:f41b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26558 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14972 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29638501 (28.2 MiB)  TX bytes:1533101 (1.4 MiB)
          Interrupt:201 

eth1      Link encap:Ethernet  HWaddr 00:12:F0:94:5C:81  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 Memory:dfdfd000-dfdfdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13969 (13.6 KiB)  TX bytes:13969 (13.6 KiB)

iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:"cablecar"  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

### Post by maniacmusician on 2007-03-06
okay, well, we can see that eth1 is  your wireless.

post the contents of this file: /etc/networking/interfaces

and try this command: sudo ifdown eth1 && sudo ifup eth1


PS: to make your posts look neater, try using [code] tags. to do that, use the # button in the posting toolbar above.

---

### Post by mrsanfran on 2007-03-06
Thanks for the forum tips.  I'm a little noobish.  I tried to look up the file, but it does not exist.

---

### Post by maniacmusician on 2007-03-06
> **mrsanfran said:**
> Thanks for the forum tips.  I'm a little noobish.  I tried to look up the file, but it does not exist.
ah sorry, my bad. I meant to say:

/etc/network/interfaces

---

### Post by mrsanfran on 2007-03-06
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid "my id"
wireless-key "my password"

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

---

### Post by chili555 on 2007-03-06
I notice your iwconfig reports, in part: ```
eth1 radio off
```

Is it Fn+F2 that is supposed to turn the wireless on in your Inspiron? Does that affect iwconfig?

---

### Post by mrsanfran on 2007-03-06
Yes, that's the shortcut.

---

### Post by maniacmusician on 2007-03-06
Are you sure the wireless is on in your computer?

You need to give some more information about your setup. What network are you trying to access? Is it an open network or does it use WEP/WPA?

---

### Post by mrsanfran on 2007-03-06
I have turned the wireless on, which now reads as "unassociated" where it read "radio off" beforehand.

I've tried to access several different points.  My home router is a WPA setup, but I've also tried to access open points from a hotel as well as my school's open wireless, but none have been able to connect.

---

### Post by maniacmusician on 2007-03-06
okay. Try the following commands to set up your wireless:

sudo iwconfig eth1 essid "your_essid"

sudo iwconfig eth1 channel auto

sudo iwconfig eth1 rate auto

sudo iwconfig eth1 key "your_key"

sudo iwconfig commit

sudo ifdown eth1 && sudo ifup eth1


obviously, substitute your own values for things in "quotes".

What happens after those commands?

---

### Post by mrsanfran on 2007-03-06
Well several different things happened.  I continued plugging the code, no matter the error msg, so this is the progression of responses; for all others, there was no response.

channel auto:
```
Error for wireless request "Set Frequency" (8B04) :
    SET failed on device eth1 ; Invalid argument.
```

eth1 key:
```
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "passkey".
```

commit:
```
commit    No such device
```

lastly:
```
There is already a pid file /var/run/dhclient.eth1.pid with pid 6964
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:12:f0:94:5c:81
Sending on   LPF/eth1/00:12:f0:94:5c:81
Sending on   Socket/fallback
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "kingofspades787".
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:12:f0:94:5c:81
Sending on   LPF/eth1/00:12:f0:94:5c:81
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

Confusing, no?  Thanks for your continued patience and persistence.

---

### Post by maniacmusician on 2007-03-06
:) I hate working with wireless. 

For "sudo iwconfig eth1 key "your_key", did you substitute passkey for "your_key"? I don't think that's right. In place of "your_key" you were supposed to input your WPA hex key. 

And, what do you get from: iwlist scan

---

### Post by mrsanfran on 2007-03-06
I put in the password I use for the router which I created when I set it up.  So it's a combo of letters and numbers.  This is the result of the new input:

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:11:50:76:2A:32
                    ESSID:"cablecar"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=98/100  Signal level=-26 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : TKIP CCMP 
                        Authentication Suites (1) : PSK  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : CCMP 
                        Authentication Suites (1) : PSK  
                       Preauthentication Supported
                    Extra: Last beacon: 828ms ago
          Cell 02 - Address: 00:40:10:20:00:03
                    ESSID:"LingBling"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=56/100  Signal level=-67 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 748ms ago
          Cell 03 - Address: 00:18:3F:6C:6A:E1
                    ESSID:"2WIRE688"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=51/100  Signal level=-70 dBm  
                    Extra: Last beacon: 796ms ago
          Cell 04 - Address: 00:15:05:11:D2:19
                    ESSID:"ACTIONTEC"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:9
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=51/100  Signal level=-70 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 708ms ago
          Cell 05 - Address: 00:18:39:40:B5:C5
                    ESSID:"ncc1701"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=61/100  Signal level=-64 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 1876ms ago
          Cell 06 - Address: 00:06:25:DD:0F:D7
                    ESSID:"glwireless"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=33/100  Signal level=-80 dBm  
                    Extra: Last beacon: 10612ms ago
          Cell 07 - Address: 00:0F:B3:49:02:DB
                    ESSID:"OIOI"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:9
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=55/100  Signal level=-68 dBm  
                    Extra: Last beacon: 724ms ago
          Cell 08 - Address: 00:18:F8:B3:A1:9D
                    ESSID:"EV Net"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=42/100  Signal level=-75 dBm  
                    Extra: Last beacon: 11692ms ago
          Cell 09 - Address: 00:11:95:76:CA:0A
                    ESSID:"retard"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=27/100  Signal level=-83 dBm  
                    Extra: Last beacon: 3096ms ago
          Cell 10 - Address: 00:14:6C:07:DF:EE
                    ESSID:"OUR NETWORK"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=31/100  Signal level=-81 dBm  
                    Extra: Last beacon: 2860ms ago
          Cell 11 - Address: 00:18:3F:32:14:49
                    ESSID:"MT206"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=20/100  Signal level=-86 dBm  
                    Extra: Last beacon: 788ms ago
          Cell 12 - Address: 02:13:CE:00:06:04
                    ESSID:"Free Public WiFi"
                    Protocol:IEEE 802.11bg
                    Mode:Ad-Hoc
                    Channel:11
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=29/100  Signal level=-82 dBm  
                    Extra: Last beacon: 7220ms ago
          Cell 13 - Address: 82:96:64:20:DD:7C
                    ESSID:"hpsetup"
                    Protocol:IEEE 802.11b
                    Mode:Ad-Hoc
                    Channel:11
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=64/100  Signal level=-62 dBm  
                    Extra: Last beacon: 676ms ago
          Cell 14 - Address: 6A:C8:01:5F:49:DA
                    ESSID:"Free Public WiFi"
                    Protocol:IEEE 802.11b
                    Mode:Ad-Hoc
                    Channel:11
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=39/100  Signal level=-77 dBm  
                    Extra: Last beacon: 688ms ago

sit0      Interface doesn't support scanning.

```

---

### Post by maniacmusician on 2007-03-06
That's a LOT of networks. Which one do you want to join? 

You may want to start with an open one and work out WPA key stuff later.

edit: Also, the key command doesn't want your router password; it wants your exact WPA key. You can find this information in your router's interface.

---

### Post by mrsanfran on 2007-03-07
I would join any open one just so long as the wireless works. :confused: Then I can work on the WPA.

---

### Post by maniacmusician on 2007-03-07
Okay. let's try the Free Public Wifi one. (You've got that in Seattle? lucky)

Here's your new /etc/network/interfaces file. Copy and paste it in place of the old one. What I did was modify the wireless bit and I added #'s in front of the ones that weren't being used, to keep them from interfering. putting a # in front of a line makes the computer ignore it.

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid Free Public WiFi

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp


then do:
> 
sudo /etc/init.d/networking restart

If that doesn't work, then you can try tying down your wireless card to that specific access point:

```
sudo iwconfic eth1 ap 6A:C8:01:5F:49:DA
```

---

### Post by mrsanfran on 2007-03-07
No change from before.

---

### Post by maniacmusician on 2007-03-07
> **mrsanfran said:**
> No change from before.
oh, oops, I typed the command wrong. should be iwconfig, not iwconfic. did you correct that?


If it still doesn't work, that's a bummer. I think I just got it working for someone else who had the same card as you...his was a lot easier for some reason. I'm not sure why it's not working....Or perhaps it's just too late at night for me to make any sense of it...

---

### Post by mrsanfran on 2007-03-07
I did change the command.  No worries, it's been a problem for weeks and varied solutions still haven't solved it.  Maybe Feisty will work out the kink.  Thanks for the attempt.

---

### Post by maniacmusician on 2007-03-07
:( I have a feeling I may have been able to fix it if I had the computer in front of me. Things are just so much faster and more intuitive then. 

you can try out feisty right now if you want. It's fairly stable. And it **does** have the new KNetworkManager for KDE.

Oh, that reminds me! You're using gnome, right?

Try installing network-manager-gnome and use that to configure it. I can't believe I didn't think of that sooner.

sudo apt-get install network-manager-gnome

I believe that's the package you want...It helps people sort out wireless problems a lot of the time.

I hope this works.

---

### Post by mrsanfran on 2007-03-07
After that's been done, how would I find and run it?

---

### Post by maniacmusician on 2007-03-07
I haven't used Gnome for a while so I'm not sure where it is in the menu. Try opening a terminal and running "network-manager-gnome"

---

### Post by Iarwain ben-adar on 2007-03-07
Pressing Alt-F2 gets the same done :D

Alt-F2
network-manager-gnome


Iarwain

---

### Post by maniacmusician on 2007-03-07
> **mrsanfran said:**
> After that's been done, how would I find and run it?

so, yeah, how's it going?

going to bed now, hopefully your problem will be fixed by the time I get up :)

---

### Post by mrsanfran on 2007-03-07
I don't know what I did aside from install the network-manager-gnome and turn off the computer, but everything worked itself out.  And just when I was doubting Ubuntu.  Thanks for the help!

---

