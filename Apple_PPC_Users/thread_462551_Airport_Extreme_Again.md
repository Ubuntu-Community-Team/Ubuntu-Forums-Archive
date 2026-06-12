---
title: "Airport Extreme Again"
date: 2007-06-02
forum: Apple PPC Users
---

### Post by tomos on 2007-06-02
Have Airport Extreme (base station and card) on my powerbook g4.  Running Feisty.  But I cannot get a connection with airport extreme.  (Reminds me of trying to use a modem - good luck) I did install bcm43xx-fwcutter but no go, contrary to the PPCFAQs.  Suggestions appreciated.

TIA
tomos

---

### Post by luckyd on 2007-06-02
Did you try this?
> A note about Airport Extreme and G-only routers:

Once Airport Extreme is activated through the fwcutter method, it will only be broadcasting at 802.11b, or 11Mbps. This probably will cause problems when trying to connect to a router that is G-only. Often, this is a simple fix:

1) Log in to your router through a browser. (See your router's documentation for specific info. For example, for some Linksys routers, go to "192.168.1.1" in your browser and, leaving the username field blank, enter the default password "admin" to access the router's configuration panel.)

2) Find the option where you specify the Network Type, Wireless Network Mode, etc. - it should be an option that has "G-only" or something similar selected.

3) Change the network mode to "Mixed" or "B and G" or something similar.

4) Save your router settings and try to connect again. Hopefully everything will work!

---

### Post by tcrroadie on 2007-06-02
Lukyd is correct.  The Airport Extreme card that uses the Broadcom chipset, will only work on wireless B enabled networks under Linux.  I have never owned an Apple Airport Base station before, but if my research is correct, it looks like your base station may not support 802.11b.  I may be wrong.  See your manual for your base station for more information.  

Please let us know what your findings are.

---

### Post by tomos on 2007-06-02
Thanks guys, but airport extreme is never "activated" enough to log in to the router.  I got into the router using the mac.  It is set up for network types B or G (Specifically: Radio Mode says 802.11n(802.11b/g compatible).  The other options involve 802.11n and 802.11a.


tomos

---

### Post by tcrroadie on 2007-06-02
Lets try to gather some data from your Airport base station using your ibook.  Boot into Ubuntu Feisty and run this command in a terminal.  Assuming eth1 is your wireless network card.

```
sudo iwlist eth1 scanning
```

You should recieve output similar to mine

```
eth1      Scan completed :
          Cell 01 - Address: 00:12:17:A9:E3:EC
                    ESSID:"Homer"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:9
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=-25 dBm  Noise level=-73 dBm
                    Extra: Last beacon: 24ms ago
```

The line that says "Protocol" will show the standards that your base station is broadcasting/recieving on.  My WAP is set to mixed (B&G).

Please post your results.

---

### Post by tomos on 2007-06-02
Thanks tcrroadie.  Here are the results.  "LiftOff" is the name of the base station. (It looks like it ought to connect.)

>  sudo iwlist eth1 scanning

eth1      Scan completed :
          Cell 01 - Address: 00:1B:63:2B:BB:83
                    ESSID:"LiftOff"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=88/100  Signal level=-45 dBm  Noise level=-68 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 68ms ago

tomos

---

### Post by tcrroadie on 2007-06-02
Great. 

Have you tried connecting with your encryption turned off?  Just for testing sake. 

You also may need to try configuring your your wireless network settings on your ibook from a terminal using iwconfig.  Very easy to do.  I can help some if you need it.

---

### Post by tomos on 2007-06-03
Thanks tcrroadie.  Still no connection with encryption off.  Any advice you have for configuring iwconfig from the mac terminal would be welcome.  (By the way, it is a g4 powerbook, not an ibook - if that makes any difference.)

Thanks for all of your help
tomos

---

### Post by tcrroadie on 2007-06-03
Hmmm.  Well, at least we know that your wireless card is working because we received data about your network with the tool iwlist.  

Open a terminal and lets try this. 

We will be using a command line tool called iwconfig to configure your wireless setttings.  

We will be using the information you received earlier from iwlist to set your wireless network settings.  Lets leave your encryption off just for now.  See man iwconfig for more information.

```
man iwconfig
```

To set your essid run this command

```
iwconfig eth1 essid LiftOff
```

To set your channel.  

```
iwconfig eth1 channel 11
```

To check the status of your wireless network run iwconfig on its own.

```
iwconfig
```

Output should look similar to mine

```
kris@ibook:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"Homer"  Nickname:"Homer"
          Mode:Managed  Frequency=2.452 GHz  Access Point: 00:12:17:A9:E3:EC   
          Bit Rate:11 Mb/s   Tx-Power=17 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=101/100  Signal level=-25 dBm  Noise level=-72 dBm
          Rx invalid nwid:0  Rx invalid crypt:104  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

To check and see if your wireless card has received an ip address via DHCP, run ifconfig

```
ifconfig
```

Output should look something like this. 

```
kris@ibook:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:51:30:94:1E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:41 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:14:51:80:67:EB  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:51ff:fe80:67eb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1903 errors:0 dropped:172 overruns:0 frame:0
          TX packets:2144 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1935885 (1.8 MiB)  TX bytes:376815 (367.9 KiB)
          Interrupt:52 Base address:0xc000 
```

You may need to edit /etc/network/interfaces.  In fact you will probably need to. 

You can add the configuration information you entered above to this file so that your wireless network comes up automatically when your system boots.  Add the information you set above to the end of this file.  

```
sudo gedit /etc/network/interfaces
```

The end of my /etc/network/interfaces file looks like this.  Edit yours as needed. 

```
iface eth1 inet dhcp
wireless-essid Homer
wireless-key my wep key here

auto eth1
```

Don't forget to add auto eth1 to your file. 

Hope this does it for you.  Please post back with your results.

---

### Post by tomos on 2007-06-03
Works!  Thanks so much, tcrroadie!  Not knowing too much about what I was doing, my mistake  was to use static-ip instead of dhcp.  Your /etc/network/interfaces file (compared to mine) did the trick.

Thanks again
tomos

---

### Post by tcrroadie on 2007-06-03
Great work.  Glad to hear you got your wireless card working.  

Thanks for posting back.  :D

---

