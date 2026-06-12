---
title: "Automating wireless login"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by Dngrsone on 2008-01-01
I'm running 7.10 (gutsy) on a Dell Latitude C610 with an Atheros AR5212 mini-PCI card.

I'm connecting with a Netgear wireless router using WEP shared.

Currently, I am connecting by opening up a terminal and typing in the following sequence:

```


sudo modprobe ath_pci
sudo ifconfig ath0 up
sudo iwpriv ath0 authmode 2
sudo dhclient ath0

```

I have to have the networking set to manual mode, or things don't work.

So, how can I fix this so I can connect automatically upon boot when I am home?

Should I write a shell script?  How do I write a conditional statement to determine whether my wireless SSID is in range?

---

### Post by shad0w_walker on 2008-01-01
Does the network manager not work for you? This seems a rather round about way to do things if it does. If it doesn't and you want a possible GUI for the wifi I suggest you look into WICD

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by kevdog on 2008-01-01
Why do you need to load the driver (ath_pci) everytime.  Is this driver not being loaded at boot?  Is it not contained in the /etc/modules file?

---

### Post by Dngrsone on 2008-01-01
Thanks for the rapid responses, guys.

The Network Manager is not working well for me.  Frankly, I am not so much worried about having a GUI as I am that I can boot up and be connected immediately when I am at home.

Kevdog, I appended ath_pci ti the modules script and now I no longer need to run it manually, but the other three commands are still necessary.

---

### Post by zipperback on 2008-01-01
I have an Acer 5050-3371 and it has an Atheros chipset for the wifi.

I use wicd for my network management and it works fantastic.

- zipperback
:popcorn:

---

### Post by zipperback on 2008-01-01
Here is the URL for wicd.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

Works great!

- zipperback
:popcorn:

---

### Post by kevdog on 2008-01-01
You can either write a script file (which isnt that hard).  If you want it to auto-detect if the network is available, you are going to have to write some logic that is going to examine the results of iwlist scan.  If your network is seen it will connect, if not, then it will not attempt a connection.  Its not that hard, just a series of grep/sed statements (might also need cut, awk) to filter the output from iwlist scan, and then run it through a series of if/else statements.

WICD might also be an alternative for you -- underneath it works just like the command line.  It provides a gui if you want, but you dont need to use it.  Ive used this on one computer.

---

### Post by Dngrsone on 2008-01-01
Thanks again, guys.

I will try wicd, though I will likely write the script anyway, as it's a good exercise/learning experience.

---

### Post by Dngrsone on 2008-01-02
Well, wicd sure looks pretty...

It shows me a list of available networks, but I am getting no joy trying to connect through it.

There must be some config file somewhere where I can set the authmod and allow the system to do its job proper.  [img]http://xs109.xs.to/xs109/06476/argh.gif[/img]

---

### Post by zipperback on 2008-01-02
> **Dngrsone said:**
> Well, wicd sure looks pretty...

It shows me a list of available networks, but I am getting no joy trying to connect through it.

There must be some config file somewhere where I can set the authmod and allow the system to do its job proper.  [img]http://xs109.xs.to/xs109/06476/argh.gif[/img]

Launch wicd.

Go to preference and make sure you added the wifi adapter to the wireless interfaces box.

Also, is your router using wep or wpa?

If you can see the list of wifi access points, then you should be able to configure your connection.

Select the additional options for the wifi access point you want to configure from the list of available ones.

Click the name or the arrow just to the left of the name, this will give you the required configuration options for the access point.

If you want to always have it automatically connect to the access point, then check the box next to "Automatically connect to this network."

Next click on "Advanced Settings".

Check the "Use Encryption" check box.

Select the encryption method you are using.

Provide the required access key.

Click "Connect"

You should now be connected to your access point.

You can now close the application, and your wifi connection should automatically be established  from this point on.

- zipperback
:popcorn:

---

### Post by Dngrsone on 2008-01-02
Thanks, zipperback.

This is what I have in preferences:

WPA Supplicant Driver:  madwifi

Wireless Interface:  ath0

Wired Interface:  eth0

Automatically reconnect on connection loss:  checked


I am running WEP shared via a Netgear WGU-624 wireless router.  Wicd will say it's connected from the icon, but it isn't.  If I try to get DHCP from the server, I never get an IP issued.  If I set a fixed IP, it seems to connect, but I have no internet.

I tried connecting to another wireless router that also uses WEP shared,  same problem.

What's more, once I mess around with wicd, I am not able to recover connectivity through the console using the abovementioned methods... I invariably end up rebooting the computer.

---

### Post by zipperback on 2008-01-03
> **Dngrsone said:**
> Thanks, zipperback.

This is what I have in preferences:

WPA Supplicant Driver:  madwifi

Wireless Interface:  ath0

Wired Interface:  eth0

Automatically reconnect on connection loss:  checked


I am running WEP shared via a Netgear WGU-624 wireless router.  Wicd will say it's connected from the icon, but it isn't.  If I try to get DHCP from the server, I never get an IP issued.  If I set a fixed IP, it seems to connect, but I have no internet.

I tried connecting to another wireless router that also uses WEP shared,  same problem.

What's more, once I mess around with wicd, I am not able to recover connectivity through the console using the above mentioned methods... I invariably end up rebooting the computer.


Attempt a connection with wicd and then post the output of the following commands.

lspci

ifconfig

iwconfig

sudo iptables --list




- zipperback
:popcorn:

---

### Post by Dngrsone on 2008-01-03
```
$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:11:F5:55:10:C7  
          inet addr:192.168.0.81  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:f5ff:fe55:10c7/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:0B:DB:08:92:3A  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x6c00 

eth0:avah Link encap:Ethernet  HWaddr 00:0B:DB:08:92:3A  
          inet addr:169.254.5.68  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0x6c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:25 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2144 (2.0 KB)  TX bytes:2144 (2.0 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-11-F5-55-10-C7-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5263 errors:0 dropped:0 overruns:0 frame:1930
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:565894 (552.6 KB)  TX bytes:2092 (2.0 KB)
          Interrupt:5 


$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Carlo"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=34/70  Signal level=-61 dBm  Noise level=-95 dBm
          Rx invalid nwid:5543  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


$ sudo iptables --list

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         



$ lspci
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:01.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:03.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)

```

There you are.

---

### Post by Dngrsone on 2008-01-03
[img]http://xs209.xs.to/xs209/06476/eh.gif[/img]  Umm... it's fixed?

Maybe?

Changes made--

Added the following line to /etc/network/interfaces:

```


pre-up iwpriv ath0 authmode 2 

```

and modified the ath0 entry 

```
wireless-key <key> restricted
```

by appending "restricted."

Rebooted a few times, and apparently it's working now.

[reference](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by zipperback on 2008-01-04
Glad to hear it's working for you now.

- zipperback
:popcorn:

---

