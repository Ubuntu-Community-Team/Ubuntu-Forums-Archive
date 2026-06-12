---
title: "wifi wpa problems"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by oldelfy on 2008-02-28
I'm having problems connecting to a wpa encrypted wifi network, i managed to connect to it fine without encryption.

sudo wpa_supplicant -w -Dwext -ieth1 -c/etc/wpa_supplicant.conf -dd 
gets going but pauses at EAPOL: startWhen --> 0
it seems to connect lan-side (i can ssh into it) but internet-side not so much
gabby@tick:~$ ping google.com
connect: Network is unreachable


interfaces:
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet static
wireless-essid TheFinn
wireless-channel 1
wireless-mode managed
address 192.168.0.50
gateway 192.168.0.1
dns-nameservers 192.168.0.1
netmask 255.255.255.0

wpa_supplicant.conf
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1

network={
        ssid="TheFinn"
        scan_ssid=0
        key_mgmt=WPA-PSK
        proto=WPA
        pairwise=TKIP
        group=TKIP
        psk=4eb2125bb73295f1509ea9578acf2c9fc136422332b52d040a0204a96a8cc4f0
}

---

### Post by oldelfy on 2008-02-28
eth1      Scan completed :
          Cell 01 - Address: 00:14:7F:D7:A2:15
                    ESSID:"TheFinn"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:70/100  Signal level:-51 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:17:3F:AA:44:3D
                    ESSID:"Heroes"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:25/100  Signal level:-80 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK

gabby@tick:~$

---

### Post by wieman01 on 2008-02-28
What hardware/chipset have you got? Please do:
> sudo lshw -C network

---

### Post by oldelfy on 2008-02-28
gabby@tick:~$ sudo lshw -C network
  *-network:0 DISABLED
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 90
       serial: 00:13:8f:ee:a3:e1
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=32 link=no maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth1
       version: 03
       serial: 00:11:50:1b:da:e4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.45+Broadcom,03/23/2006, 4.40.1 ip=192.168.0.50 latency=32 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11g
gabby@tick:~$

---

### Post by wieman01 on 2008-02-28
Wouldn't it be best to remove all that stuff from "/etc/network/interfaces" and use either Network Manager or [WICD]("http://wicd.sourceforge.net/") for wireless networking? WICD can handle static IP addresses as well. Your card seems to be fine ("ndiswrapper" with Broadcom Windows driver).

---

### Post by oldelfy on 2008-02-28
sorry, this is ubuntu server version, running apache etc not desktop at all so network manager is a nono wanna get the wpa sorted so i can stick it in a corner and ignore it ;)

---

### Post by wieman01 on 2008-02-28
Alright, then take a look at my WPA tutorial (signature) for more. Could not say more. :-) Please try WPA1 (TKIP) first, then continue with WPA2. Post here for support.

---

### Post by oldelfy on 2008-02-28
tis only wpa1 so i'll start and stop with that ;)

i'll .bck my two files and have a go (i tried yours before but that's when i was trying todo the initial driver stuff

---

### Post by wieman01 on 2008-02-28
No issues, you are a fast poster by the way.

Let me know if you need a hand. Post this if you get stuck:
> sud ifdown -v eth1
sudo ifup -v eth1

---

### Post by oldelfy on 2008-02-28
sudo /etc/init.d/networking restart
*reconfiguring network interfaces
Ignoring unknown interface eth1=eth1.

and thus she did die

---

### Post by oldelfy on 2008-02-28
hahahaha ignore my last post, i forgot to change one of the things to eth1
all working now, thanks a bunch guys :D

---

### Post by wieman01 on 2008-02-28
Excellent! See you around.

---

### Post by oldelfy on 2008-02-28
ok slight problem

the little script you wrote n the second post for your guide do you actually have to log in for it to run? or will it run just on boot?

---

### Post by wieman01 on 2008-02-28
The script will run on boot, no problem. You just have to press the power button, that's all. No log-in required.

---

### Post by oldelfy on 2008-02-29
hey ok it all seems to work, but i think my wireless keeps getting disconnected any idea why? happened twice so far and i keep having to restart the comp (no keyboard or monitor attached)

---

### Post by wieman01 on 2008-02-29
That could be an issue with 'ndiswrapper' or the router settings.

Does the router have a settings called "beacon interval"? What is the current value? What other settings are there for the physical network?

---

### Post by oldelfy on 2008-03-01
i definitly haven't seen an option like that, it's just a manky bthomehub at the moment. some sugested i try a different wireless channel so i switched the router to 13, restarted the networking and all i got was an error messahe :/ SIOCDELRT no such process so no idea what's going on there

Wireless Access Point - TheFinn	

	Configuration
			
Interface Enabled:	Yes
Physical Address:	00:14:7F:D7:A2:15
Network Name (SSID):	TheFinn
Interface Type:	802.11g
ActChannel Selection:	Manual
Region:	Europe
Channel:	1
Allow multicast from Broadband Network:	No
WMM:	enabled

	Security
			
Broadcast Network Name:	Yes
Allow New Devices:	New stations are allowed (automatically)
Security Mode:	WPA-PSK
WPA-PSK Preshared Key:	xxxxxxxxx
WPA-PSK Encryption:	TKIP
WPA-PSK Version:	WPA

not sure if i want that multicast thing on or not but that' all the settings i have for the wireless on the router

---

### Post by wieman01 on 2008-03-01
It well be interference with other networks. Some wireless adapters/drivers do not support channel 13, so try 11 instead.

What wireless router have you got and what GUI does it come with? Is a PDF manual available that I could go through?

---

### Post by oldelfy on 2008-03-01
trying it on a different channel so hopefully it'll work out :)

---

### Post by oldelfy on 2008-03-01
hmm no that didn't help, it's a bthomehub
[http://en.wikipedia.org/wiki/BT_Home_Hub](http://en.wikipedia.org/wiki/BT_Home_Hub)
i dunno why it looses connection tbh, silly thing

---

### Post by wieman01 on 2008-03-01
I do not have access to Wikipedia from here... it's blocked, sort of. 

The user manual is not available, either, but I found this:

[http://www.littlehome.co.uk/homehub/homehub2.html]("http://www.littlehome.co.uk/homehub/homehub2.html")

Apparently there is such a thing as beacon interval:
> {admin}=>:wireless ifconfig
State                                   : enabled
Network name (SSID)       : LittleHome
Public network (any)        : disabled
Channel                 : 7 [manual]
RTS Threshold           : 2347
Short Retry Limit       : 7
Long Retry Limit        : 4
[COLOR="Red"]**Beacon Period           : 100**[/COLOR]
Rate                    : 54 Mbps
Interoperability        : 802.11g
Protection              : never
Protection Mode         : rtscts
Protection Trigger      : local&overlap
Shortslot               : always
Framebursting           : disabled
Regulatory Domain       : Europe
Rate Set                : 1(b) 2(b) 5.5(b) 6(b) 9 11(b) 12(b) 18 24(b) 36 48 54  
Dtim interval           : 3 (every 300 msec)
I would reduce the value to '40' and see how you go... if that does not help, try '10'. Can you do that?

---

### Post by oldelfy on 2008-03-02
ok i've managed to telnet in but i can't seem to figure out what the actuall command is for changging the beacon period, i've tried :wireless ifconfig beacon/beacon period/beaconperiod/beaconper/ = 40 but always this

{admin}=>wireless ifconfig period = 40
Invalid option => period
{admin}=>:wireless ifconfig beacon period = 40
Invalid option => beacon
{admin}=>:wireless ifconfig beaconperiod = 40
Invalid option => beaconperiod
{admin}=>:wireless ifconfig beaconper = 40
Invalid option => beaconper

---

### Post by wieman01 on 2008-03-02
Wow, I guess I cannot help you there. Is there no GUI? It should give you the same option in a more... convenient manner.

---

### Post by bollix47 on 2008-03-02
Not sure if this is what you're looking for but from [this page]("http://www.frequencycast.co.uk/homehubfaq.html") I've quoted some of the info:

To make changes to your BT Home Hub setup, you need to 'log on' to the Home Hub, from where you'll be able to access settings and diagnostic screens. You can do this from a desktop or laptop that has a working connection to the Home Hub. From a connected machine, use the web browser (Internet Explorer, Firefox, etc) and from the web browser address bar, enter the address: [http://bthomehub.home](http://bthomehub.home) and press Enter. If for any reason this doesn't work, you can also enter the IP address for the Home Hub (sometimes known as the gateway IP address) into a web browser. The default IP address for the BT Home Hub is 192.168.1.254.

Once connected, you will be prompted for a username and password. The default username is 'admin', and the default password is either 'admin' (for software before v6.2.6E), or for later versions, the password is your unique Home Hub serial number. Once you've logged on, you'll see the main configuration screen.

...


Hope it helps.  :)

---

### Post by wieman01 on 2008-03-02
Thanks, bollix47. That is very right. This is the GUI I was referring to but I must have assumed that everybody knows what I am talking about. :-) Bad things assumptions can be. Time to go to bed for me... Lol. Sometimes you don't see the wood for the trees.

---

### Post by oldelfy on 2008-03-02
unfortunatly the gui doesn't have that option, it only appear to be in the telnet session that its shown

---

