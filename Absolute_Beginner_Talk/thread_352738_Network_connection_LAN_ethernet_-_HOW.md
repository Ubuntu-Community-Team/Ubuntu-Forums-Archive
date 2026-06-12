---
title: "Network connection LAN ethernet - HOW?"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by smnbrrtt on 2007-02-03
My first time with Ubuntu and getting nowhere fast.

I have tried the FAQs and HOWTOs - regarding a LAN ethernet connection it says 'You will have to enter IP adress, subnet, DNS etc' but it doesn't say how.

I've tried entering this info in the Networking control panel:

IP Address
Subnet Mask
Default Gateway

And in DNS tab 2 DNS addresses

But nothing happens. I don't have a username or password so i'm assuming the above way is what i should use.
What am i doing wrong?

---

### Post by moshuptrail on 2007-02-03
Did you just install Ubuntu?
Usually if you have an ethernet connection Ubuntu will configure it first time out of the gate.

Do you have an ethernet connection (or wireless)?  It's plugged in, and you know it works?  Good.
From your post I'm assuming you know you need a fixed IP address.  Is that correct?

If you're okay up to here, click on System > Administration > Networking.

Then in the box make sure to highlight the correct network device - if there are more than one.  Then click properties. Make sure the connection is enabled.  If you can choose DHCP.  That's generally easier.  If not, make sure your IP address is still there. Then click okay.  That should save it.  There is no separate save like Windows.

Okay, still a problem?

---

### Post by thenetduck on 2007-02-03
So you are trying to connect to the Internet? Or are you trying to set up a lan? Or both? For the internet connection do you have a dynamic IP address from your ISP ? Or do you have a static? Also, are you connected to a router or straight into your modem/cable box or whatever you call it? If you are using a router, what kind of router are you using? 

For setting up a LAN connection. I suggest just using ssh (find more information about ssh on google etc) because Ubuntu doesn't have a very good file sharing system set up yet. This is something that I am looking forward to for the next release. I hope it's fix. 

 The Net Duck

---

### Post by geezerone on 2007-02-03
Run a Terminal and type "ifconfig" and paste the info here. Also, do you use an ADSL modem router and if so what is the ip address of that?

---

### Post by smnbrrtt on 2007-02-03
> **moshuptrail said:**
> Did you just install Ubuntu?

If you're okay up to here, click on System > Administration > Networking.

Then in the box make sure to highlight the correct network device - if there are more than one.  Then click properties. Make sure the connection is enabled.  If you can choose DHCP.  That's generally easier.  If not, make sure your IP address is still there. Then click okay.  That should save it.  There is no separate save like Windows.



The connection works fine in XP Pro. I've done the above, but doesn't seem to work (Firefox won't connect to any site and i don't see any other sign of connection).

In XP I connect my inputting the following info:

IP Address
Subnet Mask
Default Gateway
Preferred DNS Server
Alternate DNS Server

---

### Post by smnbrrtt on 2007-02-03
> **geezerone said:**
> Run a Terminal and type "ifconfig" and paste the info here. Also, do you use an ADSL modem router and if so what is the ip address of that?

Can't do that cos to get online i have to reboot in Windows (I'm using LiveCD).
Sorry, don't know what a router is. I only have a User IP Address

---

### Post by geezerone on 2007-02-03
With regards to connecting to the internet, do you use a dial-up modem with your XP system or not? Alot of people use routers nowadays (they dial-up when powered on so just have to click on Firefox or IE). You need to be sure of your connection method before any of this becomes relevant.

Terminal: (from Live CD)

Applications > Accessories > Terminal

At the prompt type **ifconfig** and press return. Post that info here.

---

### Post by smnbrrtt on 2007-02-03
The modem is a Siemens SpeedStream 4100 Ethernet ADSL Modem - the network control panel calls it a Local Area Connection, don't know if that helps. How do i find out how it connects?

This is what i got for ifconfig:

lo   Link encap: Local Loopback
     inet addr: 127.0.0.1 Mask: 255.0.0.0
     inet6 addr: :: 1/128 Scope: Host
     UP LOOPBACK RUNNING MTU: 16436 Metric:1
     RX packets:18 errors:0 dropped:0 overruns:0 frame:0
     TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen:0
     RX bytes: 1284 (1.2KiB) TX bytes: 1284 (1.2KiB)

---

### Post by iulian on 2007-02-03
Hello,

I have the same problem as smnbrrtt. I posted my ifconfig feedback here. Now I go out to the internet through a router, that's why the gw for eth0 is 192.168.1.1. I want to connect to the internet directly through Linux machine. Example: modem -> eth1 -> eth0 -> switch -> other machines.

```
eth0      Link encap:Ethernet  HWaddr 00:0E:2E:A9:64:4B
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:2eff:fea9:644b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3163 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2658 errors:0 dropped:0 overruns:0 carrier:0
          collisions:54 txqueuelen:1000
          RX bytes:787980 (769.5 KiB)  TX bytes:579931 (566.3 KiB)
          Interrupt:193 Base address:0xc000

eth1      Link encap:Ethernet  HWaddr 00:04:61:54:D5:02
          inet addr:xxx.xxx.xxx.xxx  Bcast:xxx.xxx.xxx.xxx  Mask:255.255.255.0
          inet6 addr: fe80::204:61ff:fe54:d502/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:9436 errors:0 dropped:0 overruns:0 frame:0
          TX packets:142 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:567690 (554.3 KiB)  TX bytes:13796 (13.4 KiB)
          Interrupt:185 Base address:0xc400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:74 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:7360 (7.1 KiB)  TX bytes:7360 (7.1 KiB)
```

---

### Post by smnbrrtt on 2007-02-04
Any more help, anyone???

---

### Post by KentS on 2007-02-04
> **smnbrrtt said:**
> The modem is a Siemens SpeedStream 4100 Ethernet ADSL Modem - the network control panel calls it a Local Area Connection, don't know if that helps. How do i find out how it connects?


When in network control panel, is there a name for the connection (three letters followed by number)? Is the connection configured? Is it active?

Does the command 'ifconfig -a' give you information about something else than 'lo'? (Like 'eth0', 'eth1', 'wlan0', 'ath0'?)

Typing 
```
cat /etc/network/interfaces
```
in a terminal, do you find the name of the connection you want to use?

> This is what i got for ifconfig:

lo   Link encap: Local Loopback
     inet addr: 127.0.0.1 Mask: 255.0.0.0
     inet6 addr: :: 1/128 Scope: Host
     UP LOOPBACK RUNNING MTU: 16436 Metric:1
     RX packets:18 errors:0 dropped:0 overruns:0 frame:0
     TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen:0
     RX bytes: 1284 (1.2KiB) TX bytes: 1284 (1.2KiB)

You can't connect to the internet using that. So that's not what you want to configure. My guess is that the Live CD doesn't have the drivers needed for the card you're trying to connect with. You might have to install Ubuntu to HD to get it working, but I'm not sure.

---

### Post by moshuptrail on 2007-02-04
Are you ready to learn a lot?   Problems like yours will inevitably lead to learning.  :) 

From your ifconfig output it is evident that Ubuntu has not configured or recognized eth0, your ethernet port.
lo is the "local" loopback port and that's the only thing in the output posted.  Look at iulian's output and compare.  iulian has two ethernet ports, eth0 and eth1.

You should be seeing eth0 both in the ifconfig output and in the Networking dialog.  That's the one you need to be configuring.  If it's not there, no amount of fiddling will make it work!

We need to figure out what kind of ethernet connection your PC has.  It may require a driver that is not expected in the standard Ubuntu install.  Is it a laptop with built-in ethernet, or a desktop with an ethernet card?

If you don't have eth0, this command will scan your PCI bus (internal to PC) devices and identify them.  It's a good bet your ethernet is on the PCI bus.  Post the output here and lets see what devices are there: lspci  (just type it at the $ prompt)

One more thing: KentS has a good thought.  Also post the output of: cat /etc/network/interfaces

---

### Post by KentS on 2007-02-04
[QUOTE=iulian;2102791]Hello,

I have the same problem as smnbrrtt. I posted my ifconfig feedback here. Now I go out to the internet through a router, that's why the gw for eth0 is 192.168.1.1. I want to connect to the internet directly through Linux machine. Example: modem -> eth1 -> eth0 -> switch -> other machines.

[QUOTE]

I don't quite understand what you want to do, so sorry for the following stupid questions.

The router you don't want to use, it's not the router provided by your internet provider? Cause I don't think that's possible.

I assume the problem is you don't receive an IP adress when not using the router. Have you tried typing 'sudo dhclient' in a terminal?

---

### Post by moshuptrail on 2007-02-04
> **iulian said:**
> Hello,

I have the same problem as smnbrrtt. I posted my ifconfig feedback here. Now I go out to the internet through a router, that's why the gw for eth0 is 192.168.1.1. I want to connect to the internet directly through Linux machine. Example: modem -> eth1 -> eth0 -> switch -> other machines.


iulian - what you want to do is to configure Linux as a router.  I suggest a separate post with that as title - you will get more response.

---

### Post by smnbrrtt on 2007-02-04
Thanks for all the help so far. I hope this info helps:

In Network settings the "Wired Connection" is ticked. Its properties box is called "Settings for interface eth0". I have configured the information i said in previous post and it is enabled.

When i try 'sudo pppoeconf' it says "found 1 ethernet device eth0" it then scans but returns "sorry Access Concentrator did not respond...check cables etc....maybe another pppoe process controls modem"

When i try 'lspci' it detects ethernet controller: Realtek Semiconductor RTL 8139/8139C/8139/C+ (rev10)

When i try 'cat/etc/network/interfaces' it says:
"bash: cat/etc/network/interfaces: no such file or directory"

ps How can i tell the connection is active (other than the browser connects)?

---

### Post by shareMenaPeace on 2007-02-04
Retry
```

cat /etc/network/interfaces
```
note after teh "cat" is a space.

---

### Post by Patrick-Ruff on 2007-02-04
if the same thing happened to you that happened to me, the network settings shortcut is missing GKSUDO.

did you get prompted for a password when you launch it?

---

### Post by smnbrrtt on 2007-02-04
> **KentS said:**
> 

did you get prompted for a password when you launch it?

No

---

### Post by KentS on 2007-02-04
A suggestion if you're normally a lucky person:

Open a terminal and type
```
ifconfig
```
Does the 'eth0' connection show up?
If not type
```
ifconfig -a
```
to see all connections. Does eth0 show up?
If so type
```
sudo ifconfig eth0 up
```
Again, type
```
ifconfig
```
Does eth0 show up now?
If it does you really are lucky. Then you can try to configure eth0 by editing /etc/network/interfaces (That's what I had in mind when I first asked you the question. cat is a program that shows you the file, like 'more' or 'less'. Type ' whatis cat ' without the ' in a terminal.) Or you can probably use the ifconfig to feed in the necessary information.

---

### Post by smnbrrtt on 2007-02-04
So...

After 'cat...' it returns:

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dchp
auto eth1
iface eth1 inet dchp
auto eth2
iface eth2 inet dchp
auto ath0
iface ath0 inet dchp
auto wlan0
iface wlan0 inet dchp


After 'ifconfig -a' it returns

eth0
 Link encap: Ethernet HWaddr 00:17:31:CF:16:5B
inet6 addr: fe80 ::217:31ff:fecf:165b/64 Scope: Link
UP BROADCAST RUNNING MULTICAST MTU: 1500 Metric:1
RX packets:17953 errors:0 dropped:0 overruns:0 frame:0
TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes: 1140957 (1.0MB) TX bytes: 3204 (3.1KiB)
Interrupt: 169 Base address: 0x4000


lo 
Link encap: Local Loopback
inet addr: 127.0.0.1 Mask: 255.0.0.0
inet6 addr: :: 1/128 Scope: Host
UP LOOPBACK RUNNING MTU: 16436 Metric:1
RX packets:18 errors:0 dropped:0 overruns:0 frame:0
TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes: 12388 (12.0KiB) TX bytes: 12388 (12.0KiB) 

Sit0

lo Link encap: IPv6-n-IPv4
NOARP MTU: 1480Metric:1
RX packets:0errors:0 dropped:0 overruns:0 frame:0
TX packets:0errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0


I had to copy all that down and type it in - could be a mistake or 2...

---

### Post by moshuptrail on 2007-02-04
Holy cow!  You typed all that in?  You can highlight and then click edit > copy.  Then edit > paste in the browser.

The fact that eth0 is there indicates that it's not a driver or hardware not recognized kind of issue.

A couple things bother me:
1.  I see an IPv6 address and no IP address for eth0.
    Most people have problems with IPv6 because it's not well supported yet.
    There are posts here with instructions on how to disable IPv6 because it causes so many problems.
    IPv6 is an advanced form of IP address.  If a device between you and the internet doesn't support it you will have problems.

2. You mentioned trying to configure pppoe.  I think that needs more explanation for folks to help.
   I don't know much about it myself.  But the error message you got is interesting - as if it's already running or something.  Like, what are the "standard" procedures for setting up pppoe?

If it's the pppoe config that's a problem it might be helpful to start a new post with that in the title - to get the right folks to look at your post.

---

### Post by smnbrrtt on 2007-02-04
> > **moshuptrail said:**
> Holy cow!  You typed all that in?  You can highlight and then click edit > copy.  Then edit > paste in the browser.

But i have to reboot in Windows to get online.

[QUOTE]2. You mentioned trying to configure pppoe.  I think that needs more explanation for folks to help.
   I don't know much about it myself.  But the error message you got is interesting - as if it's already running or something.  Like, what are the "standard" procedures for setting up pppoe?

If it's the pppoe config that's a problem it might be helpful to start a new post with that in the title - to get the right folks to look at your post.[/QUOTE]

I just ran sudo pppoeconf, and got the result i posted above. Doesn't this need a username and password anyway? (which i don't have)

---

### Post by darrenm on 2007-02-05
Yup your router seems to be ethernet only. Therefore it should just work.

The problem is your ethernet adapter is set to DHCP and if you had to type stuff into Windows to get it to work then you obviously have DHCP turned off in the router.

Can you tell us the IP information you had to type into Windows and I'll post the information you need to type in to get it to work.

---

### Post by smnbrrtt on 2007-02-05
Thanks, the information i use is:

IP Address
Subnet Mask
Default Gateway
Preferred DNS Server
Alternate DNS Server

---

### Post by darrenm on 2007-02-05
No I mean the actual information. Unless its a public IP you won't be identifiable so dont worry about posting it.

---

### Post by smnbrrtt on 2007-02-05
IP Address 087.105.129.039
Subnet Mask 255.255.255.000
Default Gateway 087.105.129.001
Preferred DNS Server 217.30.129.149
Alternate DNS Server 217.30.137.200

I'm even more puzzled now - i tried the 6.06 LiveCD (was trying 6.10 before) and using the dchp it is saying that eth0 is active. When i use static IP address and enter the above info it says there is an error and won't activate eth0.

According to system info there is network activity, both sending and receiving, but Firefox is still not connecting to anything.

---

### Post by darrenm on 2007-02-05
type:
```
sudo gedit /etc/network/interfaces
```
Then make sure it looks like this:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 87.105.129.39
netmask 255.255.255.0
gateway 87.105.129.1
```

Then 

```
sudo gedit /etc/resolv.conf
```
and make sure it looks like this
```
search localdomain
nameserver 217.30.129.149
nameserver 217.30.137.200
```

then

```
sudo ifdown eth0 && sudo ifup eth0
```
I think you're confusing the network-admin program with the extra 0's that shouldn't be there.

---

### Post by smnbrrtt on 2007-02-05
Buy that man a pint!!

It worked - i just configured the network settings as you had written without the zeros and Bob's your uncle, and also the browser runs incredibly faster. 
Thanks darrenm and everyone.

---

### Post by darrenm on 2007-02-05
> **smnbrrtt said:**
> Buy that man a pint!!

It worked - i just configured the network settings as you had written without the zeros and Bob's your uncle, and also the browser runs incredibly faster. 
Thanks darrenm and everyone.

No worries. It shouldn't matter, Ubuntu should just ignore the 0's so its more a bug than anything. Like try pinging 127.0.0.1 then try pinging 127.1 ...

---

### Post by rahulthewall3000 on 2007-02-06
Hi!
I am facing the same problems. I have a dell latitude D520 and I reinstalled my ubuntu. Now, I realized that my internet just doesn't work. I have a dual boot system and my internet works fine on windows but for some strange reason it doesn't work in Ubuntu. The internet connection doesn't even work with the live CD and that is surprising because it worked previously with the Live CD perfectly.
The internet connection that I have is a LAN connection and I am at a university so there is a common LAN connection. Can someone out their suggest as to why my internet connection is not working now with Ubuntu as it was working previously. Please help, I don't want to use the net on Windows.
What is more strange is that I see the eth0 icon on the taskbar and if I click on it, it shows that I am connected to the net, even then firefox can't open any sites. I am obtaining the DNS settings automatically. 
So, reading the entire thread it seems that I have to post the outputs of my ifconfig file, I will do that right away, but if you think there is any other problem, then just please reply! 

Many thanks in advance
Rahul Jain

---

### Post by rahulthewall3000 on 2007-02-06
Ha Ha Ha!

I just typed in ifconfig in the terminal and my internet connection works again. What can I say?

---

### Post by Quinton007 on 2007-02-07
I also have a similar version of this problem, except my system is not ready the onboard ethernet 10/100.  All I get is the local option.

---

### Post by Quinton007 on 2007-02-07
I have tried everything you have listed for the other people having my problem, but I think that I need to find a driver for my onboard ethernet connection.  Any ideas where to look?

---

### Post by darrenm on 2007-02-07
Can you do ```
sudo ifconfig -a
``` and post the output. ifconfig alone only shows the configured devices.

---

### Post by Quinton007 on 2007-02-07
quin@Odin:~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:172 errors:0 dropped:0 overruns:0 frame:0
          TX packets:172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13500 (13.1 KiB)  TX bytes:13500 (13.1 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by KentS on 2007-02-08
Quinton007, it looks like you're missing a driver. Type
```
lspci
```
in a terminal and see if you can find the name of your ethernet card. Then you can check if there are available drivers by searching on the web.

---

### Post by Quinton007 on 2007-02-08
00:00.0 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:09.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
00:09.1 Input device controller: Creative Labs SB Audigy MIDI/Game port (rev 03)
00:09.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
01:00.0 VGA compatible controller: ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)] Secondary

---

