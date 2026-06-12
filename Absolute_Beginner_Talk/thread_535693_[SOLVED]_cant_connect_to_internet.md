---
title: "[SOLVED] cant connect to internet"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by jamesmurphy1234 on 2007-08-26
hi,

I just installed Ubuntu v 7.04 on my computer, but I cannot connect to the internet.

I have a LinkSys Wireless G card, and a LinkSys WRT54G router. It tells me I am connected to the wireless network alright, but when I open Firefox it can't find google.

I have taken all the security features off my router for the time being (wooohoo! free internet on cobourg street!)

I have two other machines connected to the network and internet, one with Win2000 and the other WinXP. 

I can ping my Ubuntu machine from my Windows machines, but I cannot ping my router or my Windows machines from the Ubuntu machine.

resolv.conf is empty, and I cannot edit it (I get an access denied message).

I have cable DHCP internet.

I did a ipconfig in a Windows, recorded the information, and went to input it into the network settings in Ubuntu. The difficulty is, the terminology is slightly different.

Any help would be greatly appreciated,


James

---

### Post by Austin_KW on 2007-08-26
The router is not important but the driver will depend on the chipset of the wireless card. It may be the problem but without knowing the model and revision we can not say.

To find the card type open a terminal and type the command "lspci" fro a pci card or "lsusb" for a usb adapter. If you can not figure it out then post the results of the command back here.

to edit a file owned by root your need to change to root, eg, to edit resolv.conf in  gedit, enter "gksudo gedit /etc/resolv.conf " in a terminal.
However this should be setup by your router when dhcp sets the ip address so there may be something else wrong

Some useful terminal commands you may want to look at or post back the results;
**ifconfig -a**                                 #similar to ipconfig in windows
**sudo iwconfig**                          #list wireless settings
**sudo iwlist scan**                      #scan for wirless networks
**cat /etc/resolv.conf**                  #list your dns settings
**cat /etc/network/interfaces**     #network interface setup

---

### Post by jamesmurphy1234 on 2007-08-27
Thanks for the lead!

I did everything you suggested, and found:

1) Although it is a LinkSys WMP54G router, it is showing up as an RaLink RT2500

2) It looks like it is connected to channel (if that is the right word) ra0, although when I goto the Network Tools interface box and look under devices, ra0 shows up as an Unknown Interface, and the IP address does not look right at all (it includes letters and colons in the place of periods).


Maybe I need to install another driver?

If anyone knows what any of this means, please let me know!

Thanks

James

--------------------
Command-line output below, [...] indicates an irrelevant part I have removed


murphy@murphy:~$ lspci
[...]
00:0d.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
[...]
murphy@murphy:~$ ifconfig -a

lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:142 errors:0 dropped:0 overruns:0 frame:0

          TX packets:142 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:13808 (13.4 KiB)  TX bytes:13808 (13.4 KiB)



ra0       Link encap:Ethernet  HWaddr 00:0F:66:EC:07:5E  

          inet6 addr: fe80::20f:66ff:feec:75e/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:409705 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 b)  TX bytes:16388200 (15.6 MiB)

          Interrupt:11 Base address:0x4000 



ra0:avahi Link encap:Ethernet  HWaddr 00:0F:66:EC:07:5E  

          inet addr:169.254.5.146  Bcast:169.254.255.255  Mask:255.255.0.0

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          Interrupt:11 Base address:0x4000 



murphy@murphy:~$ sudo iwconfig

lo        no wireless extensions.



ra0       RT2500 Wireless  ESSID:""  

          Mode:Managed  Frequency=2.412 GHz  Bit Rate:11 Mb/s   Tx-Power:0 dBm   

          RTS thr:off   Fragment thr:off

          Encryption key:6236-6338-6334-3239-3165-0000-00   Security mode:open

          Link Quality=0/100  Signal level=-120 dBm  Noise level:-195 dBm

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



murphy@murphy:~$ sudo iwlist scan

lo        Interface doesn't support scanning.



ra0       Scan completed :

          Cell 01 - Address: 00:12:17:C5:67:DC

                    Mode:Managed

                    ESSID:"Milkbone"

                    Encryption key:off

                    Channel:1

                    Quality:0/100  Signal level:-26 dBm  Noise level:-195 dBm
[...]



murphy@murphy:~$ cat /etc/resolv.conf

domain phub.net.cable.rogers.com

nameserver 64.71.255.198

search 74.101.181.129

murphy@murphy:~$ cat /etc/network/interfaces

auto lo

iface lo inet loopback



auto eth0

iface eth0 inet dhcp



auto eth1

iface eth1 inet dhcp



auto eth2

iface eth2 inet dhcp



auto ath0

iface ath0 inet dhcp



auto wlan0

iface wlan0 inet dhcp



iface ra0 inet dhcp

wireless-essid Milkbone

wireless-key s:b6c8c4291e


auto ra0

---

### Post by WebSiteGuru on 2007-08-27
try pinging your router, see if it reach it. I had a LinkSys Wireless card alos and I tried that and it works after I use the ping. it seem almost like the Wireless card was on a standby mode and when you ping the router it wake up. (never hurt to try it) ;)

---

### Post by ncappel1 on 2007-08-27
after "iwlist scan" do you see your wireless network? if so, you could try connecting to it with:
```
sudo iwconfig [device] essid any
```
and
```
sudo iwconfig [device] ap auto
```

the ubuntu wiki also has a great page about wireless troubleshooting : [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

---

### Post by Austin_KW on 2007-08-27
OK, Again your router is irrelevant.

The chipset in your card is an rt2500. The default driver is rt2500 (legacy driver) from serialmonkey.com and creates an interface called ra0. This should work but needs to be configured through the file /etc/network/interfaces. This driver does not support networkmanager.

You need to replace the ra0 section (from **iface ra0 inet dhcp** to **auto ra0**) in /etc/network/interfaces as follows. 
Use the comand "**gksudo gedit /etc/network/interfaces**" to edit the file
For WEP
```

auto ra0
iface ra0 inet dhcp
	pre-up ifconfig ra0 up
	pre-up iwconfig ra0 essid Milkbone
	pre-up iwconfig ra0 key b6c8c4291e

```

After you make the and save edits, enter the command "**sudo ifup --f ra0**" (note the double '-'). This command will force ra0 to come up using the changes.


**NOTE: your scan is reporting your encryption as OFF; If that is the case then instead use**
```

auto ra0
iface ra0 inet dhcp
	pre-up ifconfig ra0 up
	pre-up iwconfig ra0 essid Milkbone
**	pre-up iwconfig ra0 key OFF  **

```

Later, If you decide to use WPA-PSK encryption (recommended as WEP is junk) then just insert your WpaPsk in the following.
```

auto ra0
iface ra0 inet dhcp
    pre-up ifconfig ra0 up
    pre-up iwconfig ra0 mode managed
    pre-up iwconfig ra0 essid Milkbone
    pre-up iwpriv ra0 set EncrypType=TKIP
    pre-up iwpriv ra0 set AuthMode=WPAPSK
    pre-up iwconfig ra0 essid Milkbone
    pre-up iwpriv ra0 set  WPAPSK="**ReplaceYourWpaPskHere**"
    pre-up iwconfig ra0 essid Milkbone

```

---

### Post by Austin_KW on 2007-08-27
Noticed something else on you WEP key you are setting a sting "s:"
But your example key is Hex b6c8c4291e (ie. 10 hex digits -> 40 bit WEP); So remove the s: and just use b6c8c4291e

---

### Post by jamesmurphy1234 on 2007-08-27
Thanks for all the responses! I think I am starting to make some progress, but not quite there yet.

I have pinged the router, but no response.

I tried trying "sudo iwconfig ra1 essid any" and then "sudo iwconfig ra1 ap auto" in the command prompt. No error messages, but still no internet.

I made revisions to the interface file, but it says it cannot find device wlan0 (the revised file and terminal output are below). I included the wireless key because, for some strange reason even though it is unencrypted, the GUI wireless utility in the top right corner will not tell me it is connected to the network if I leave it out. Seems strange, does ubuntu require encyption?

When I started this process, my wireless network(card) was "ra0". Somewhere along the line it got changed to "ra1".

Is it possible that by me screwing around wlan0 got saved as something else? its not wlan1, maybe wlan2 wlan3 or even higher?

What is wlan0? My wireless network? My internet connection? Where can I find out more information about it?

I attached my interfaces file & terminal output. Any suggestion appreciated,

James
----------
Command output:
------------

murphy@murphy:~$ gksudo gedit /etc/network/interfaces

murphy@murphy:~$ sudo ifup --f ra1

Error for wireless request "Set ESSID" (8B1A) :

    SET failed on device wlan0 ; No such device.

Failed to bring up ra1.

murphy@murphy:~$ 

---------
Interfaces file:
---------

auto lo 
iface lo inet loopback 

auto eth0 
iface eth0 inet dhcp 

auto eth1 
iface eth1 inet dhcp 

auto eth2 
iface eth2 inet dhcp 

auto ath0 
iface ath0 inet dhcp 

auto wlan0 
iface wlan0 inet dhcp 

auto ra1 
iface ra1 inet dhcp 
	pre-up ifconfig ra1 up 
	pre-up iwconfig wlan0 essid Milkbone 
	pre-up iwconfig wlan0 key s:b6c8c4291e 

	wireless-essid Milkbone 
	wireless-key s:b6c8c4291e

---

### Post by jamesmurphy1234 on 2007-08-27
thanks i changed that, noticed after. though i doubt it would matter since the network is not encrypted.  i did it my wep code showed up as a bunch of dots for security. thats a good sign, i guess

---

### Post by Austin_KW on 2007-08-27
Sorry the wlanX was a cut and paste error from my interfaces file. (I have multiple interfaces ra0, wlan0, wlan1 and I cut and paste from different parts of the file)

I edited my post, You should change everything to ra0 or ra1 whichever is reported by ifconfig.

If your network is not encrypted use "	pre-up iwconfig ra1 key OFF  " and remove the "wireless-key s:b6c8c4291e"


**It may be quicker to test these commands from the command line**
TRY the following sequece in a terminal, assuming ra1
```

sudo ifconfig ra1 down                              # take down interface
sudo ifconfig ra1 up                                # bring it back up
sudo iwconfig ra1 essid Milkbone                        # set the essid
sudo iwconfig ra1 key OFF                        # Clear the encryption
sudo dhclient ra0                                   # Try to get an IP address from router

```

---

### Post by jamesmurphy1234 on 2007-08-28
sweet! it's working! hope I can be on the other side of these support chats soon! thank you so much for posting your suggestions!

one last question: i saw some old posts marked "resolved". can I mark this one as resolved? or was that a figment of my imagination?

---

### Post by jamesmurphy1234 on 2007-08-28
ok there we go

---

