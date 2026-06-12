---
title: "WiFi connected, all IP's look right, but no connection to the Internet"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by Doc.Caliban on 2007-06-01
I have an Intel 2200GB (just gave up on the Atheros and took it out).  Everything seems to be working fine: It finds the AP, connects with WPA2, draws all of the DHCP addresses, and has a 98% signal strength.

The only problem is that it still doesn't get me onto the net.  :-)

Here are the results of my iwconfig:
```

eth1      IEEE 802.11g  ESSID:"CS Ops"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:16:B6:DA:B1:B6   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=98/100  Signal level=-26 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:2
```

Ideas?

Thanks,

-Doc

---

### Post by Nikron on 2007-06-01
check you route

'route' will display your gateway

route add default gw 'theipofyourgatewayhere'

that'll add it

---

### Post by jimrz on 2007-06-01
> **Doc.Caliban said:**
> I have an Intel 2200GB (just gave up on the Atheros and took it out).  Everything seems to be working fine: It finds the AP, connects with WPA2, draws all of the DHCP addresses, and has a 98% signal strength.

The only problem is that it still doesn't get me onto the net.  :-)

Here are the results of my iwconfig:
```

eth1      IEEE 802.11g  ESSID:"CS Ops"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:16:B6:DA:B1:B6   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=98/100  Signal level=-26 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:2
```

Ideas?

Thanks,

-Doc

just a thought...go to System > Administration > Network > the DNS tab and check that you have appropriate servers listed. have on several occassions found this cured problems that i had after fresh installs.

---

### Post by Doc.Caliban on 2007-06-01
Thanks for the replies.


Here is my route output:

```

estination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1

```

The router's IP is, of course, 192.168.1.1   Right now I am connected via eth0 again and it's working fine.

Something I've noticed is that when I unplug the cable, Gaim remains logged in and working just fine via eth1. 

The only DNS listed is the router.  It seems to work fine with eth0.

-Doc

---

### Post by Doc.Caliban on 2007-06-01
> **jimrz said:**
> just a thought...go to System > Administration > Network > the DNS tab and check that you have appropriate servers listed. have on several occassions found this cured problems that i had after fresh installs.

That did it.  I had tried that earlier but it wasn't saving the entry.  I had to save it as a "location" and switch to it.  I'll have to see if I have to switch locations every time I boot up to get it to work...

Odd that the wired connection worked fine with the default DNS info, yet the wireless needed an external DNS address.

Thanks!

-Doc

---

### Post by Doc.Caliban on 2007-06-02
Actually, I take that back. 

This thing is still a mess.   Sometimes the additional DNS IP helps, most of the time it still doesn't.  The network config thing can't seem to maintain the location anyway so I always have to go set it agian and again and again.  Something wrong there for sure.

The biggest things is:  Why does the wifi connection need the external DNS IP when the wired connection does just fine with only the router IP as a DNS entry?   

So in the end, this still isn't working.

-Doc

EDIT:  The network settings gui thing is making me insane.  It defaults to no location.  If you make any changes to the DNS info, it won't save it.  If you make changes and save it to a new location, it won't let you start up in that location, it will always be in it's default "no location" mode.

---

### Post by wormser on 2007-06-02
I am not sure what is going on with setting the DNS in the gui issue is about.  Try setting it via the shell.

```
sudo nano /etc/resolv.conf
```

Another option is to log into your router and add addition DNS settings.  Use 4.2.2.2 and 4.2.2.1.

---

### Post by Doc.Caliban on 2007-06-02
> **wormser said:**
> I am not sure what is going on with setting the DNS in the gui issue is about.  Try setting it via the shell.

```
sudo nano /etc/resolv.conf
```

Another option is to log into your router and add addition DNS settings.  Use 4.2.2.2 and 4.2.2.1.

At this point I've killed Network Manager.  Is that a bad move?  I edited the resolv.conf file and replaced the router address with the actual external DNS IP.

Now the problem I'm running in to is the fact that I don't know how to manually edit /etc/network/interfaces in a way that will enable WPA2.  In roaming mode it allows for it, but not seemingly in manual mode.

-Doc

EDIT:  I re-enabled Network Manager and sure enough, it overwrote the resolv.conf file again with the 192.160.1.1 entry.

---

### Post by Doc.Caliban on 2007-06-05
This is still unresolved.  This is as far as I've gotten:

I am using the ipw2200 driver in roaming mode.  In this mode it finds my network and asks for the WPA2 passphrase.  It connects and aquires the correct DHCP addresses from the router.  I cannot, however, connect to anything... not even the router by IP.

The alternative of using a manual configuration instead of roaming mode is not an option because, for some really really strange reason, manual config only offers WEP.

Still looking for help on this one.

-Doc

---

### Post by Doc.Caliban on 2007-06-07
I've tried this now with no encryption at all and I still get no connectivity.  All IP's are correct, signal strength is 98%.  I can't even connect by IP.

-Doc

---

### Post by airtonix on 2007-06-07
just another thought : check to see if you or someone else has limited which computers can connect to the router via mac address.

or check with someone whoe owns a : 
 mac with wifi
 windoze with wifi

and get them to try to connect.

I know iwconfig is seemingly for listing details of wifi devices.does ipconfig show the same information about the device?

thirdly i had wifi (not sure if it was wpa2) working between a dell laptop and a apple airport station. in this situation i had to make the Airport Admin Utility reveal a "Non Apple Aiport" version of the key. again not sure if it was wpa2 or not here.

---

### Post by Doc.Caliban on 2007-06-08
> **airtonix said:**
> just another thought : check to see if you or someone else has limited which computers can connect to the router via mac address.

or check with someone whoe owns a : 
 mac with wifi
 windoze with wifi

and get them to try to connect.

I know iwconfig is seemingly for listing details of wifi devices.does ipconfig show the same information about the device?

thirdly i had wifi (not sure if it was wpa2) working between a dell laptop and a apple airport station. in this situation i had to make the Airport Admin Utility reveal a "Non Apple Aiport" version of the key. again not sure if it was wpa2 or not here.


Great suggestions, thanks!

This router is one I've been using for about a year now with XP machines, and recently a friend's Vista box.  I did dig through all the settings in the router's firmware (DD-WRT) just to make sure I hadn't missed anything, but all is well on that end.

Man, this is really frustrating because I can't find anything else to look at!  

I've checked /etc/network/interfaces and it just says "iface wlan0 inet dhcp" where it should.  I'm guessing that it's correct.

EDIT:  Output from IWCONFIG

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Get Your Own"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:16:B6:DA:B1:B6   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=94/100  Signal level=-33 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:7   Missed beacon:2 
```

I disabled all the encryption just in case it was that, but still no luck.


-Doc

---

### Post by Doc.Caliban on 2007-06-09
SOLUTION:

I disabled network manager and added a network montior do-dad to my tool bar.  From there I manually configured the connection and it works just fine.

---

