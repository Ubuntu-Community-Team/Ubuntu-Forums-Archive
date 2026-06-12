---
title: "Wireless problems, sooo frustrated"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by alibaba on 2007-03-14
I know, probably to you, another wireless thread, but plz help

:( 

this is the second day of trying to connect using every guide I can find. can someone please point me where to go

iwconfig:

iwconfig
lo        no wireless extensions. 

eth0      no wireless extensions.

eth1      unassociated  ESSID:"Garvin"  
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:16:B6:2F:30:77   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions

:(

please I can give mostly any info, just someone please help


Thanks in advance

---

### Post by elephant007 on 2007-03-14
what wifi card do you have, that would be helpful.

---

### Post by siciliancasanova on 2007-03-14
What are your outputs for 

lspci
arp
netstat -nr

---

### Post by alibaba on 2007-03-14
06:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

 arp
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.1.1              ether   00:16:B6:2F:30:75   C                     eth0


 netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0

---

### Post by alibaba on 2007-03-14
I got the windows driver and wireless drivers say Installed and Hardware available

---

### Post by dannyboy79 on 2007-03-14
please post this info for help

sudo iwlist scan

ifconfig -a

lspci -v | grep Network

cat /etc/network/interfaces

---

### Post by siciliancasanova on 2007-03-14
Your wireless card and network interface card have the same IP address.  I don't know if that makes a difference but have you tried disabling your Network Card in **System > Administration > Networking **?  If it does work then you just need to change the ip address of one of the two.

---

### Post by alibaba on 2007-03-14
eth1      Scan completed :
          Cell 01 - Address: 00:16:B6:2F:30:77
                    ESSID:"Garvin"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=78/100  Signal level=-44 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 136ms ago
          Cell 02 - Address: 00:11:50:31:E1:65
                    ESSID:"belkin54g"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=55/100  Signal level=-68 dBm  
                    Extra: Last beacon: 11680ms ago
          Cell 03 - Address: 00:14:BF:4A:48:21
                    ESSID:"woon"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=58/100  Signal level=-66 dBm  
                    Extra: Last beacon: 436ms ago

sit0      Interface doesn't support scanning.

eth0      Link encap:Ethernet  HWaddr 00:01:4A:5C:A9:88  
          inet addr:192.168.1.136  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:4aff:fe5c:a988/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:79406 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50459 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:115925588 (110.5 MiB)  TX bytes:4061401 (3.8 MiB)

eth1      Link encap:Ethernet  HWaddr 00:12:F0:25:E9:7A  
          inet addr:192.168.1.136  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:66748 (65.1 KiB)  TX bytes:20598 (20.1 KiB)
          Interrupt:209 Base address:0x8000 Memory:b0106000-b0106fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16448 (16.0 KiB)  TX bytes:16448 (16.0 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lspci -v | grep Network
06:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.1.136
netmask 255.255.255.0
gateway 192.168.1.1


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp






auto eth0



iface eth1 inet dhcp
wireless-essid Garvin
wireless-key cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.1.136
netmask 255.255.255.0
gateway 192.168.1.1


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp






auto eth0



iface eth1 inet dhcp
wireless-essid Garvin
wireless-key 0016B62F3077

auto eth1


Hope this info helps

auto eth1

---

### Post by alibaba on 2007-03-14
ups

---

### Post by siciliancasanova on 2007-03-14
Don't bump so much, I usually wait an hour on mine to bump, typically the people who leave you responses are subscribed to your thread so they will know when you post something new, they also might have seen your response and are working on an answer.

---

### Post by alibaba on 2007-03-14
sorry, Thanks

---

### Post by siciliancasanova on 2007-03-14
It's cool because you didn't know but just saying, there are a lot of people on here right now trying to get their problems fixed.

---

### Post by siciliancasanova on 2007-03-14
Have you changed your router so it's an open network with no password?  Have you disabled your wired card so that all you have running is your wireless?  (don't worry just renable it to get back online)

---

### Post by alibaba on 2007-03-14
I tried using wireless radar but it doesnt do anything except show signal strength,

---

### Post by siciliancasanova on 2007-03-14
It shows the MAC address of your router though, that you're connected to it.

---

### Post by alibaba on 2007-03-14
I would rather keep my router as password, but I cant even connect to unprotected ones in the neighborhood ( for testing of course :)  )

---

### Post by siciliancasanova on 2007-03-14
You know the ESSID's of the open networks or you just can't see them listed in wifi-radar?

---

### Post by alibaba on 2007-03-14
I know one or two

---

### Post by alibaba on 2007-03-14
wifi radar says im connected to Garvin??

---

### Post by siciliancasanova on 2007-03-14
What type of key are you trying to connect with? WPA or WEP?

---

### Post by markofealing on 2007-03-14
I'm running Kubuntu Edgy 6.10 on a Dell C640 with the Intel Pro Wireless 2200BG (rev 05), same as yours. 

It is fully compatible with this version of Ubuntu and works "out of the box". In fact it installs better under Ubuntu (zero config) than under Windows XP which did not have the drivers, much to my surprise!

What version of Ubuntu are you using?

---

### Post by handaxe on 2007-03-14
My standard response when nothing fundamentally seems wrong:

You might try WICD as your manager of wireless connections. Under active development.

[http://compwiz18.blackhole.cx/wicd/wb/](http://compwiz18.blackhole.cx/wicd/wb/)

Deb install. Also installs a tray icon BUT does not put an entry is startup. You do that by going to "System" "Preferences" "Sessions" "Startup Programs" and enter /opt/wicd/tray-edgy (if using Edgy) or /opt/wicd/tray-dapper (Dapper (Doh!)).

WICD handles many forms of encryption and unlike Network Manager does not require you to mess about with /etc/network/interfaces.

HA

---

### Post by alibaba on 2007-03-14
I think the pass is wpa for the router, but i cant connect to ones without a pass,

hmm should I try a reinstall?

---

### Post by siciliancasanova on 2007-03-14
You're going to need wpa_supplicant, although I'm not exactly sure how you're connected to the router right now if you have entered a wpa key.

---

### Post by siciliancasanova on 2007-03-14
I will let someone else take it from here, try the two posts above your last post, I haven't run into this yet so I'm not exactly sure from this point where you should go.

---

### Post by handaxe on 2007-03-14
Try wicd. Wpasupplicant is a dependancy of wicd so that will make sure of that. As a previous poster wrote, the ipw2200 generally is plain sailing under Ubuntu.


HA

---

### Post by alibaba on 2007-03-14
> **handaxe said:**
> My standard resposne when nothing fundamentally seems wrong:

You might try WICD as your manager of wireless connections. Under active development.

[http://compwiz18.blackhole.cx/wicd/wb/](http://compwiz18.blackhole.cx/wicd/wb/)

Deb install. Also installs a tray icon BUT does not put an entry is startup. You do that by going to "System" "Preferences" "Sessions" "Startup Programs" and enter /opt/wicd/tray-edgy (if using Edgy) or /opt/wicd/tray-dapper (Dapper (Doh!)).

WICD handles many forms of encryption and unlike Network Manager does not require you to mess about with /etc/network/interfaces.

HA


its stopping at obtaining IP address :confused:  I can connect while in windows, hmm

---

### Post by alibaba on 2007-03-14
I forgot to put in my static IP, Now it works Thanks soooooo much everyone!!!!!!

:)

---

### Post by alibaba on 2007-03-14
Thanks for that program man!

---

### Post by handaxe on 2007-03-14
Great - I'm grinning......

HA

---

### Post by siciliancasanova on 2007-03-14
Yeah, it may come off as a downside but eventually you will see how it is better than Windows.  I started saving commands people gave me and commands I found in other posts in text files, like one is called "Networking" and you can quickly see what your network is doing, how it's connecting, and pin point problems, faster and quicker than you ever would in Windows.

---

