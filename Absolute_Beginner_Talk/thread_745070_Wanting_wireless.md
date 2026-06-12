---
title: "Wanting wireless"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by Helios1276 on 2008-04-04
Hey folks, I need to finally get around to sorting out my wireless connection, I'm currently  using a wired connection to my Belkin router at the moment. Anybody up for lending a hand?

shane@Acer:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:38:DE:07  
          inet addr:192.168.2.5  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe38:de07/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21943 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18736 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25330692 (24.1 MB)  TX bytes:2840346 (2.7 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

shane@Acer:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by opscure on 2008-04-04
Try this page:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/)

---

### Post by Dr Small on 2008-04-04
Do you have a wireless card? If so, what type?
Is it a PCI card, or USB?

Depending on which it is, please run one or the other commands:
```
lspci
```
```
lsusb
```

---

### Post by Helios1276 on 2008-04-04
my wireless is built in/embedded(?) into the laptop

---

### Post by brian_p on 2008-04-04
> **Helios1276 said:**
> my wireless is built in/embedded(?) into the laptop

To repeat Dr Small's request: please post the output from the command 'lspci'.

---

### Post by Helios1276 on 2008-04-04
shane@Acer:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express (rev 21)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
shane@Acer:~$ lsusb
Bus 005 Device 002: ID 08ec:0008 M-Systems Flash Disk Pioneers 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 002 Device 001: ID 0000:0000  
shane@Acer:~$

---

### Post by brian_p on 2008-04-04
> **Helios1276 said:**
> shane@Acer:~$ lspci
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

Good. It's a supported chipset. Not that I've ever dealt with them. But there will be plenty who have. It should just be a matter of configuring /etc/network/interfaces.

Here is something to help you on your way:

[http://intellinuxwireless.org/](http://intellinuxwireless.org/)

---

### Post by Amarsingh0793 on 2008-04-04
Have you tried ndiswrapper yet?

---

### Post by Helios1276 on 2008-04-04
Haven't touched Ndiswrapper yet no, is it a simpler option?

---

### Post by Helios1276 on 2008-04-04
> **brian_p said:**
> Good. It's a supported chipset. Not that I've ever dealt with them. But there will be plenty who have. It should just be a matter of configuring /etc/network/interfaces.

Here is something to help you on your way:

[http://intellinuxwireless.org/](http://intellinuxwireless.org/)

That link recommends the  iwlwifi driver, whats my next step?

---

### Post by Seisen on 2008-04-04
Does anything show up in restricted drivers manager?

---

### Post by brian_p on 2008-04-04
> **Helios1276 said:**
> That link recommends the  iwlwifi driver, whats my next step?

What does 'uname -a' say? This gives the kernel version.

---

### Post by Amarsingh0793 on 2008-04-04
It is quite simple. ndiswrapper uses windows drivers for your wireless devices so if have the drivers for that wireless device then it may work. 

You can read more about it and download it from Sourceforge.

Hope this helps!:)

---

### Post by Seisen on 2008-04-04
Actually ndiswrapper is in the repositories,  Amarsingh0793. So no need to compile it unless you absolutely have too.

---

### Post by ugm6hr on 2008-04-04
```
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
```

This is important.

You don't need ndiswrapper.

In fact, that chipset is one of the best supported in Linux.

It should work out-of-the-box.

The fact that ifconfig doesn't list the device at all suggests that it is turned off.  Do you have a BIOS switch, or a button on the outside, or a keyboard shortcut to activate it?

Does wifi work in any other OS?  What exact model of laptop do you have?

This will confirm whether a driver is loaded or not:
```
lshw -C network
```

---

### Post by Helios1276 on 2008-04-04
> **ugm6hr said:**
> ```
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
```

This is important.

You don't need ndiswrapper.

In fact, that chipset is one of the best supported in Linux.

It should work out-of-the-box.

The fact that ifconfig doesn't list the device at all suggests that it is turned off.  Do you have a BIOS switch, or a button on the outside, or a keyboard shortcut to activate it?

Does wifi work in any other OS?  What exact model of laptop do you have?

This will confirm whether a driver is loaded or not:
```
lshw -C network
```

Ok, I hit the wireless switch on there sorry .

shane@Acer:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express (rev 21)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
shane@Acer:~$ lsusb
Bus 005 Device 002: ID 08ec:0008 M-Systems Flash Disk Pioneers 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 002 Device 001: ID 0000:0000  
shane@Acer:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:13:02:0f:ad:06
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () latency=0 module=ipw3945 multicast=yes wireless=unassociated
  *-network
       description: Ethernet interface
       product: NetLink BCM5789 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 21
       serial: 00:16:36:38:de:07
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.77 firmware=5789-v3.49a ip=192.168.2.5 latency=0 module=tg3 multicast=yes
shane@Acer:~$ 

The laptop is an Acer 5672 wmli.
It recognised the connection before but I couldnt surf or anything (firefox wouldnt connect)

---

### Post by ugm6hr on 2008-04-04
```
driver=ipw3945
```

That driver should work fine.

In System->Administration->Network, do you have roaming enabled?

Now that the wifi button is on - try these again:
```
ifconfig
iwconfig
```

Do you use Network Manager?

What happens when you click on the icon?

[IMG]http://www.gnome.org/projects/NetworkManager/images/wireless-at-tealuxe.png[/IMG]

PS: I've seen a few other threads you've started on this same topic.  I'm going to close them.  Please don't open new threads on the same topic.

---

### Post by Helios1276 on 2008-04-04
Roaming is indeed enabled.

shane@Acer:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:38:DE:07  
          inet addr:192.168.2.5  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe38:de07/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:57294 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49651 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:58192937 (55.4 MB)  TX bytes:7574483 (7.2 MB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:13:02:0F:AD:06  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:6971 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0x6000 Memory:54000000-54000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

shane@Acer:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:7005   Missed beacon:0

p.s. excuse the multiple threads , i was floundering in my noobiness

---

### Post by Pekkalainen on 2008-04-04
Your card should Just Work (tm) out of the box. Strange. Restart the comp with the wireless switch on and you should just need to use network manager next to the clock to connect to a network.

---

### Post by ugm6hr on 2008-04-04
So which is your SSID in the list?

What happens when you select it?

What encryption do you use?

This will give a bit of info:
```
iwlist scan
```

---

### Post by Helios1276 on 2008-04-04
SSID= The Information Super-highway

encryption= wpa2

When I click it , it just says waiting for network key...

---

### Post by bumanie on 2008-04-04
Hi Helios1276.
Try the ipv6 things I mentioned the other night. Might work this time as your card is enabled. Worth  a try as you know you can reverse them if they don't work.

---

### Post by Helios1276 on 2008-04-04
No, I'm still getting "waiting for network key"

---

### Post by bumanie on 2008-04-04
This may or may not help, but have a look anyway.
[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)
It seems to have been a known issue, but from what I can find, not a common issue. Seems to be specific to the keyring at this point. Look at this [http://ubuntuforums.org/showthread.php?t=424262](http://ubuntuforums.org/showthread.php?t=424262)
Good luck.

---

### Post by Helios1276 on 2008-04-04
I input my wpa2 code , it connects ( connected to wireless network (98%) ) but I just can't get Firefox to connect to Google, this is driving me nuts lol I had a friend over yesterday who just installed gutsy and was able to get to his own router fine but over here he could'nt either? do I call an IT guy or a priest?

---

### Post by bumanie on 2008-04-04
I'm very surprised that the ipv6 thing doesn't work for you. 90% of the time if the internet won't connect in gutsy, that is the reason (that is, when everything else seems to be working fine). I really have no more ideas. I have a wired modem connected to a wireless router and have not had any problems, thus I have not had to find solutions to an issue such as this. Hardy is less than 3 weeks away, personally I think Hardy is much better than gutsy ( based upon using it for a time at alpha 3 and 6 stages). I am considering using the beta release. Worth a thought, but as its beta, there can still be issues with its stability across the entire OS. If you set up your system with a separate /home, you could try installing hardy to / and see how that goes. If you find it unstable, you can go back to gutsy. Depends how much download/bandwidth you have for downloads/updates etc.

---

### Post by Helios1276 on 2008-04-04
Im definitely considering Hardy, I had planned to wait and see if it improves on the wireless side of things after the release. Theres a few other things I wanna see first though, like trying to connect to another router with and without enabled encryption and such. ITs very frustrating , I mean there must be loads of ppl with gutsy and my wireless setup who are fine??

---

### Post by ugm6hr on 2008-04-04
> **Helios1276 said:**
> I input my wpa2 code , it connects ( connected to wireless network (98%) ) but I just can't get Firefox to connect to Google, this is driving me nuts lol I had a friend over yesterday who just installed gutsy and was able to get to his own router fine but over here he could'nt either? do I call an IT guy or a priest?

Ok.

After "connecting" with wifi, and disconnecting for wired, do the following - and report on results:

```
route -n
ping www.google.com
ping 66.249.91.99
```

---

### Post by Helios1276 on 2008-04-04
shane@Acer:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth1
shane@Acer:~$ ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)
shane@Acer:~$ ping 66.249.91.99
PING 66.249.91.99 (66.249.91.99) 56(84) bytes of data.
From 192.168.2.7 icmp_seq=1 Destination Host Unreachable
From 192.168.2.7 icmp_seq=2 Destination Host Unreachable
From 192.168.2.7 icmp_seq=3 Destination Host Unreachable
From 192.168.2.7 icmp_seq=4 Destination Host Unreachable
From 192.168.2.7 icmp_seq=5 Destination Host Unreachable
From 192.168.2.7 icmp_seq=6 Destination Host Unreachable
From 192.168.2.7 icmp_seq=7 Destination Host Unreachable
From 192.168.2.7 icmp_seq=8 Destination Host Unreachable
From 192.168.2.7 icmp_seq=9 Destination Host Unreachable
From 192.168.2.7 icmp_seq=10 Destination Host Unreachable
From 192.168.2.7 icmp_seq=11 Destination Host Unreachable
From 192.168.2.7 icmp_seq=12 Destination Host Unreachable
From 192.168.2.7 icmp_seq=14 Destination Host Unreachable
From 192.168.2.7 icmp_seq=15 Destination Host Unreachable
From 192.168.2.7 icmp_seq=16 Destination Host Unreachable
From 192.168.2.7 icmp_seq=18 Destination Host Unreachable
From 192.168.2.7 icmp_seq=19 Destination Host Unreachable
From 192.168.2.7 icmp_seq=20 Destination Host Unreachable
From 192.168.2.7 icmp_seq=22 Destination Host Unreachable
From 192.168.2.7 icmp_seq=23 Destination Host Unreachable
From 192.168.2.7 icmp_seq=24 Destination Host Unreachable
From 192.168.2.7 icmp_seq=25 Destination Host Unreachable
From 192.168.2.7 icmp_seq=26 Destination Host Unreachable
From 192.168.2.7 icmp_seq=27 Destination Host Unreachable
From 192.168.2.7 icmp_seq=29 Destination Host Unreachable
From 192.168.2.7 icmp_seq=30 Destination Host Unreachable
From 192.168.2.7 icmp_seq=31 Destination Host Unreachable
From 192.168.2.7 icmp_seq=32 Destination Host Unreachable
From 192.168.2.7 icmp_seq=33 Destination Host Unreachable
From 192.168.2.7 icmp_seq=34 Destination Host Unreachable

---

### Post by ugm6hr on 2008-04-04
OK - and now:
```
ping 192.169.2.1
```

---

### Post by Helios1276 on 2008-04-04
shane@Acer:~$ ping 192.169.2.1
PING 192.169.2.1 (192.169.2.1) 56(84) bytes of data.

---

### Post by Helios1276 on 2008-04-04
So...close ...must..BUMP

---

### Post by ugm6hr on 2008-04-04
> **Helios1276 said:**
> shane@Acer:~$ ping 192.169.2.1
PING 192.169.2.1 (192.169.2.1) 56(84) bytes of data.

No destination unreachable error with that?

This is bizarre...

You have an assigned IP (192.168.2.7).
NM appears to think you are connected.
However, you can't ping your router (which I believe is 192.168.2.1 based on the route -n output).

One more question - do you use MAC address filtering?

I would suggest you remove all your wifi encryption (temporarily) to make sure you can connect with an open network.

At least when you know that, we will have isolated the problem.

---

### Post by Helios1276 on 2008-04-04
Hey, I dont have access to the comp at the moment but I'll run through what you have outlined there in the morning. Cheers for sticking with the thread!

---

### Post by Helios1276 on 2008-04-05
Ok, here goes

1. Took off encryption- was able to connect wireless no problem

2. Mac filtering option is there but not turned on

---

### Post by brian_p on 2008-04-05
> **Helios1276 said:**
> Ok, here goes

1. Took off encryption- was able to connect wireless no problem

And able to access the net? Re-enable encryption. Note what you do. Still able to surf?

---

### Post by ugm6hr on 2008-04-05
OK - you can connect without encryption.  That is promising.

I don't use WPA2 - so not sure how well it is supported.  I will do a bit of research and get back to you.

---

### Post by Helios1276 on 2008-04-05
Cheers , If all else fails I pretty sure I have the option of setting the encryption to just wpa if that helps?

Yup browser running also@Brian

---

### Post by ugm6hr on 2008-04-05
> **Helios1276 said:**
> Cheers , If all else fails I pretty sure I have the option of setting the encryption to just wpa if that helps?

Yup browser running also@Brian

I use WPA-PSK - so perhaps try that for now.

---

### Post by lswest on 2008-04-05
i think you'd be better off with WPA encryption, wpa2 might just not be supported entirely yet.  You can always try WICD to see if that gives you better results with WPA2, but i doubt it.  Try sticking with a wpa encryption for now, should solve your problem.

---

### Post by Helios1276 on 2008-04-05
Switched to WPA but when I try to connect wireless now it just keeps repeating the request for the password , which I enter but get nowhere??

---

### Post by brian_p on 2008-04-05
> **Helios1276 said:**
> Switched to WPA but when I try to connect wireless now it just keeps repeating the request for the password , which I enter but get nowhere??

Check what you are using on the router.  I'd go for WPA/TKIP.  Make the password really simple. ubuntu12, say.

Set up the same encryption and password in Ubuntu. I'm assuming the adapter supports WPA/TKIP. Check what it says in /etc/network/interfaces.

---

### Post by Helios1276 on 2008-04-05
this is what I'm working with

---

### Post by brian_p on 2008-04-05
> **Helios1276 said:**
> this is what I'm working with

Looks reasonable. I'd be inclined to have Security Mode as WPA(PSK) if possible. Don't know what Obscure PSK is. I'd switch it off.

At some point seeing what you have in /etc/network/interfaces might be useful.

---

### Post by Helios1276 on 2008-04-05
> **brian_p said:**
> Looks reasonable. I'd be inclined to have Security Mode as WPA(PSK) if possible.
the option ive selected is the only one for wpa ..the other are like 128bit etc

 Don't know what Obscure PSK is. I'd switch it off.
that would just show my password i think

At some point seeing what you have in /etc/network/interfaces might be useful.
do i sudo that? i suck at the terminal

---

### Post by northern lights on 2008-04-05
```
cat /etc/network/interfaces
```

---

### Post by Helios1276 on 2008-04-05
shane@Acer:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

---

### Post by brian_p on 2008-04-05
> **Helios1276 said:**
> shane@Acer:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

If that is all there really is in that file you're never going to connect to any outside host. There should be sections for eth0 and/or eth1 or eth2.

And yet you can access the internet without encryption. If you went back and confirmed that the interfaces file should have more than lo (the local interface) in it. Also ifconfig and iwconfig should show what interfaces are active.

---

### Post by Helios1276 on 2008-04-05
not sure how to confirm that?

shane@Acer:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:38:DE:07  
          inet addr:192.168.2.5  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe38:de07/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14007 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13711 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8720003 (8.3 MB)  TX bytes:2651102 (2.5 MB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:13:02:0F:AD:06  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:91 dropped:6662 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32663 (31.8 KB)  TX bytes:96472 (94.2 KB)
          Interrupt:17 Base address:0x6000 Memory:54000000-54000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

shane@Acer:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:6575   Missed beacon:0

---

### Post by brian_p on 2008-04-05
> **Helios1276 said:**
> not sure how to confirm that?

Earlier you said you connected the wireless without encryption. I assume you could also access the internet. Return to that configuration and see what you get for eth1 (from iwconfig) and the contents of the interfaces file. The interfaces file must have eth1 information in it.

> shane@Acer:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:38:DE:07  
          inet addr:192.168.2.5  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe38:de07/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14007 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13711 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8720003 (8.3 MB)  TX bytes:2651102 (2.5 MB)
          Interrupt:18 


This is the wired connection. It's connected because it has an inet address and packet traffic.

> eth1      Link encap:Ethernet  HWaddr 00:13:02:0F:AD:06  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:91 dropped:6662 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32663 (31.8 KB)  TX bytes:96472 (94.2 KB)
          Interrupt:17 Base address:0x6000 Memory:54000000-54000fff 


This is the wireless interface. No inet address. No traffic. It's not operative.

> lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

This is the loopback interface. It connects the machine to itself. Looks ok.

> shane@Acer:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0.
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:6575   Missed beacon:0

No wireless connection. But we know that from above

---

### Post by Helios1276 on 2008-04-05
Ok, the following is from a wireless connection to the router(wpa2/tpik) in which i am connected but cant get my browser to access google.

shane@Acer:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

shane@Acer:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:38:DE:07  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:95084 errors:0 dropped:0 overruns:0 frame:0
          TX packets:77856 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:113006171 (107.7 MB)  TX bytes:12209039 (11.6 MB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:13:02:0F:AD:06  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:92 dropped:11764 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33953 (33.1 KB)  TX bytes:189403 (184.9 KB)
          Interrupt:17 Base address:0x6000 Memory:54000000-54000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

shane@Acer:~$  iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:11681   Missed beacon:0

---

### Post by brian_p on 2008-04-05
> **Helios1276 said:**
> Ok, the following is from a wireless connection to the router(wpa2/tpik) in which i am connected but cant get my browser to access google.

shane@Acer:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback



When you set up networking from the gui it should write to /etc/network/interfaces. It hasn't. There are only two lines. Why I do not know.

Using a text editor (with sudo) add the following to /etc/network/interfaces:


```
iface eth0 inet dhcp

iface eth1 inet dhcp
# pre-up ip link set eth1 up
wireless-essid UBUNTU

```

Save and then, with an ethernet cable attached to the router, do

```
sudo ifup eth0
```

Can you now get to Google? Yes?

Do

```
sudo ifdown eth0
```

followed by

```
sudo ifup eth1
```

Can you get to Google now? No. Take the eth1 interface down and remove the # from the interfaces file. Bring eth1 up again. Is Google responding?

**Note.**

The router must have no encryption set and the ESSID it broadcasts must be UBUNTU.

The adapter wireless driver must be loaded. I do not know its name.  ipw3945?

Check with

```
sudo lsmod | grep ipw
```

---

### Post by Helios1276 on 2008-04-05
Using a text editor (with sudo) add the following to /etc/network/interfaces

sorry for reeking of noob but could u clarify this?

---

### Post by brian_p on 2008-04-05
> **Helios1276 said:**
> Using a text editor (with sudo) add the following to /etc/network/interfaces

sorry for reeking of noob but could u clarify this?

No need to apologise. We've all been there.

```
sudo nano /etc/network/interfaces
```

nano should be on the system. Exit it with ^X (I think). That is, hold down the control key and press x.

---

### Post by ugm6hr on 2008-04-05
> **brian_p said:**
> If that is all there really is in that file you're never going to connect to any outside host. There should be sections for eth0 and/or eth1 or eth2.

And yet you can access the internet without encryption. If you went back and confirmed that the interfaces file should have more than lo (the local interface) in it. Also ifconfig and iwconfig should show what interfaces are active.

Sorry to interrupt - but that's not correct.

I use NM to connect wifi.  My interfaces file is equally empty.  I can definitely get online.

Maybe try with the HEX key instead of ASCII:

```
wpa_passphrase *ssid ascii_password* 
```

This will generate the HEX key for you.

---

### Post by brian_p on 2008-04-05
> **ugm6hr said:**
> Sorry to interrupt - but that's not correct.

I use NM to connect wifi.  My interfaces file is equally empty.  I can definitely get online.

Thanks for the correction. It had passed through my mind that there was something else going on here. I do not use Network Manager, or any other manager for that matter, so anyone who has experience of it can only be of help to 
Helios1276.

However, I hope you would agree that loading the correct module and configuring /etc/network/interfaces is the canonical way of configuring interfaces.

Your suggestion of leaving encryption off struck me as good way forward. Wouldn't it be better to keep searching for a solution and not have it in the equation.

---

### Post by ugm6hr on 2008-04-05
> **Helios1276 said:**
> Ok, here goes

1. Took off encryption- was able to connect wireless no problem

2. Mac filtering option is there but not turned on

It already works unencrypted.

We are now trying to allow a secure wifi network that Helios can connect to.

NM sometimes misbehaves with password handling.

If the HEX alternative doesn't work - I'd try Wicd (see link below).

---

### Post by Helios1276 on 2008-04-05
Hey guys, cheers for staying with me on this one! I'm away from the comp so I can't work on it yet but I was thinking would not having Wpasupplicant installed be a cause? Just randomly going through a friend's Ubuntu here at the moment.

---

### Post by ugm6hr on 2008-04-05
> **Helios1276 said:**
> would not having Wpasupplicant installed be a cause?

No.  NM includes wpa supplicant support.

---

### Post by Helios1276 on 2008-04-05
oh right, I just noticed it wasnt installed through synaptic and thought I was onto something.

---

### Post by ugm6hr on 2008-04-06
> **Helios1276 said:**
> oh right, I just noticed it wasnt installed through synaptic and thought I was onto something.

Hang on.... I think I misunderstood.

In Synaptic, you haven't got *wpasupplicant* marked as installed?  Where did you install Ubuntu from?  This is default installed, I thought....

Maybe you should try installing that.

---

### Post by Helios1276 on 2008-04-06
Nah sorry was confusion at 5am there, it's installed alright. It's Kwan or something that isn't. I'll have a go at the last recommendation you made.

---

### Post by Helios1276 on 2008-04-06
> **ugm6hr said:**
> Sorry to interrupt - but that's not correct.

I use NM to connect wifi.  My interfaces file is equally empty.  I can definitely get online.

Maybe try with the HEX key instead of ASCII:

```
wpa_passphrase *ssid ascii_password* 
```

This will generate the HEX key for you.

So this involves changing the encryption on the router to WPA and then running that command which will give me a hex key to input as my new password?

---

### Post by ugm6hr on 2008-04-06
> **Helios1276 said:**
> So this involves changing the encryption on the router to WPA and then running that command which will give me a hex key to input as my new password?

Yes.

Make sure *ssid* and *ascii password* are case sensitive.

---

### Post by Helios1276 on 2008-04-06
ssid="ssid"
        #psk="********"
        psk=****************************************

Ok, bear with me here I'm a little confused. ***= are new passwords? I have to set these at the router? Then try to connect wireless and input the Hex key as my password? Sorry about this, I'm new to it and I wanna make sure I dont frag the wireless for everyone else lol

---

### Post by ugm6hr on 2008-04-06
I thought your ssid was *The Information Super-highway*?

Not sure, but I think spaces mean that would be *"The Information Super-highway"*, but perhaps try changing to something with no spaces.

The HEX password is after psk=

In theory, you shouldn't have to change the password at the router (although it is worth doing that if it doesn't work).

---

### Post by Helios1276 on 2008-04-06
SSID is the network name right? I called it The Information Super-highway.
Right so I'll rename it and try the hex key.

---

### Post by ugm6hr on 2008-04-06
> **Helios1276 said:**
> SSID is the network name right? I called it The Information Super-highway.
Right so I'll rename it and try the hex key.

Yes - but you initially said it was *The Information Super-highway*, but your entry 3 above says *ssid*.

Make sure you chose (and use) the correct one.

---

### Post by Helios1276 on 2008-04-06
Well when I set the router up, I named it ' The Information Super-highway', all the xp machines see it as that. If the SSID has any other connotations besides the name of the network I dont know them. I can't give a reason for the difference between what came up in the terminal and such, I just dont have the savvy. To date, I have changed the router to wpa and the password to the hex(huge series of numbers/digits the terminal gave me) that I got from the earlier command. At first the NM kept thinking it was still WPA2 but after  a while then asked for a password for WPA, which I inputed but it just kept on repeating the request and I couldn't connect.

---

### Post by ugm6hr on 2008-04-06
Hang on.  I'm getting confused.

The command should have been:
```
wpa_passphrase "The Information Super-highway" *ascii_password*
```

Where ascii_password is your chosen ascii password

This should return:
```
wpa_passphrase "The Information Super-highway" ascii_password
network={
        ssid="The Information Super-highway"
        #psk="ascii_password"
        psk=d6baf19767f82164d57c37a875bf403c4cec61509c3faa1693242cd5389e394f
}

```

The long string after psk= is the HEX password.

Make sure that the ssid (aka Network name) is *The Information Super-highway* on the router, and it is set to WPA.

---

### Post by Helios1276 on 2008-04-06
shane@Acer:~$ wpa_passphrase "The Information Super-highway" *********************(A)
network={
        ssid="The Information Super-highway"
        #psk="********"(just the beginning of A)
        psk=***********************************************

Thats what I'm getting and thats what I'm using,Still seems just just keep requesting me to input the password over and over. IS it ok if the first psk part is only the beginning of the actuall ascii password?

Also, my password contains spaces also , if that could be having an effect?It hasn't on windows machines.

---

### Post by Helios1276 on 2008-04-06
[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)
Would this apply to me? I've gotta fix this problem, have essays and exams due very soon and I wont get extensions on the grounds of Ubuntu wifi problems! lol:(

---

### Post by ugm6hr on 2008-04-06
> **Helios1276 said:**
> [http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)
Would this apply to me? 

No - that is only for Dapper (not Gutsy).  Gutsy has Network Manager and wpa supplicant as default install.

Password with spaces..... that is the problem.

Do the same command, but like this:
```
wpa_passphrase "The Information Super-highway" "ascii password with spaces"
```

---

### Post by Helios1276 on 2008-04-06
> **ugm6hr said:**
> No - that is only for Dapper (not Gutsy).  Gutsy has Network Manager and wpa supplicant as default install.

Password with spaces..... that is the problem.

Do the same command, but like this:
```
wpa_passphrase "The Information Super-highway" "ascii password with spaces"
```

I used the spaces for the password in that command before, as in I input the password exactly how it is used in every instance. Unless your implying to put'with spaces' after the password . If it would be easier I could send any and all details you would need (including pass) privately?

---

### Post by Helios1276 on 2008-04-06
#psk="********"..if it means anything , this section stops at the first space in the actual(full) password

---

### Post by ugm6hr on 2008-04-06
> **Helios1276 said:**
> I used the spaces for the password in that command before, as in I input the password exactly how it is used in every instance. Unless your implying to put'with spaces' after the password . If it would be easier I could send any and all details you would need (including pass) privately?

No - I meant to put the "" marks in.

```
wpa_passphrase "The Information Super-highway" "ascii password with spaces"
network={
        ssid="The Information Super-highway"
        #psk="ascii password with spaces"
        psk=8e8d9164175ae28a8b73ecedd2faa520db695518515d9125e748db4afa2ed265
}

```

---

### Post by Helios1276 on 2008-04-06
Still not working, there was a a difference in the SSID (Information-information) which I fixed but it still keeps asking for the password after I input it.

---

### Post by ugm6hr on 2008-04-06
> **Helios1276 said:**
> Still not working, there was a a difference in the SSID (Information-information) which I fixed but it still keeps asking for the password after I input it.

I'm stuck now...

Either try Wicd (see link below).

Or manual connection: [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by Helios1276 on 2008-04-06
Ok man, thanks for all your help

---

### Post by Helios1276 on 2008-04-06
Update- Wicd performs no better than NM, unsure if I can follow that guide at first glance.

---

### Post by ugm6hr on 2008-04-06
> **Helios1276 said:**
> Update- Wicd performs no better than NM, unsure if I can follow that guide at first glance.

With Wicd
1.  Did you try HEX key?
2. Did you try entering ASCII password in "" marks?

---

### Post by Helios1276 on 2008-04-06
Tried both the HEX key you helped me obtain and the original that I used on the other machines(which is still working for them). I haven't made any changes to the terminal since the ones we walked through. This seems crazy to me now, How can encryption be causing this much trouble?

---

### Post by ugm6hr on 2008-04-06
Try the password quoted in "" marks too.

I have no idea what else could be the problem.  Although I have never had a password with spaces myself.

I have set up multiple WPA and WEP laptops with no problem on Gutsy.

---

### Post by Helios1276 on 2008-04-06
> **ugm6hr said:**
> Try the password quoted in "" marks too..
Gave it a shot but same result.

I suppose at this point , I should try changing the password so it has no spaces and trying again.Should I keep this thread alive or have we exhausted all avenues? If I can't fix this then I'll have to consider setting up a dual boot with xp so I have some sort of wireless connectivity or possibly hounding a local Linux power user if I can find one , it might factor out any human error on my part.

---

### Post by ugm6hr on 2008-04-06
I can't think of anything else to try.

But I'm not really an expert either.

Maybe post a summary of what has happened, what we've tried, and see if anyone else has any ideas.

---

### Post by Helios1276 on 2008-04-06
Ok, I will have to leave the problem for a while untill after exams. Once again, thanks for all your help

---

### Post by Helios1276 on 2008-04-10
Bump..in case someone has fixed this before

---

### Post by pablol on 2008-04-26
I had the same problem and this worked for me


sudo gedit /etc/network/interfaces

Comment out everything other than “lo” entries in that file and save the file

Create a file called /etc/default/wpasupplicant, add entry ENABLED=0 and save the file

sudo touch /etc/default/wpasupplicant

Reboot your system.

Complete entry here:
[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

Good luck!

---

