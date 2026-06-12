---
title: "Help with ADSL setup please"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by Theo Venter on 2008-01-07
I'm getting realy frustrated now. This is the second forum I've tried to get some help with no success.
Maybe I should stay with windows cause I cant get any support anywhere. No one wants to help this  Linux wanabe!!!!!!!!!!!!!!!!!!!!!!!!!

I Previously asked:
***************

Hi to all,

I'm obvsly a newbe to Linux. I hate windows to the max. Was still better the old DOS  way with Windows3.11 ect. Lost control and stability over my PC. Want to be FREE
:lolflag:
Anyway I need help getting connected. Got Ubuntu 7.10 From PC World. Running live CD and trying to c if I can connect to the internet first before installing Ubuntu.
I have a ADSL Router DSL-502T
pppoeconf dont work. It sees the eth0 but cant find any router. Complains about some Access Concentrater.
Please help me step by step how to config everything PLEASE:confused:
This is what I get with ifconfig:
ubuntu@ubuntu:~$ sudo ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:15:F2:95:0E:B2  

          inet addr:10.1.1.3  Bcast:10.255.255.255  Mask:255.0.0.0

          inet6 addr: fe80::215:f2ff:fe95:eb2/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:38 errors:0 dropped:0 overruns:0 frame:0

          TX packets:132 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:5345 (5.2 KB)  TX bytes:15340 (14.9 KB)

          Interrupt:19 Base address:0xb000 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by kleo skywalker on 2008-01-07
This might work:

Go to System-->Administration-->Network. Click on the "Properties" button next to "Wired Connection". Uncheck the "Enable roaming mode" box, set Configuration to "Static IP". Set the IP Address, Subnet Mask, Gateway Address. Back in the "Network Settings" menu, set DNS servers (primary and secondary). OR the DHCP setting might work for you (didn't for me.)

Then run ```
sudo pppoeconf
```

As far as I remember, it does say stuff about an access concentrator, but once you let the whole thing run and reboot, internet seems to work.

---

### Post by laidback on 2008-01-07
I've only ever used Network settings, never pppoeconf from CLI. As above disable Roaming , my netmask is 255,255,255,0 or 255,255,254,0 works just as well. Gateway is the address of my Router. Also; make sure you TICK the box on the LHS of the Wired Connection line. Once you commit your setting it should reconfigure and work immediately.
If you still get problems delete eveything in Network dialogue and retype. Sometimes an unseen error creeps in. It does and WILL work...so your desires will be met.

---

### Post by Theo Venter on 2008-01-07
Thanx for the reply,

I tried all the above with no success. Can u please specify (looking at my* ifconfig*) which ip, subnet,etc. I should use. Also DNS primary and secondary please. Should I restart after each change and how? Sorry for all the Q's. But I need A's. :confused:

I am realy struggling here. Networking is not my strong point. I am  so new to Linux as well. I am realy interested in this. ](*,)

Thank you so much.

What is the *lo*? My router? I know* eth0* is my onboard ethernet

---

### Post by p_quarles on 2008-01-07
Can we see your interfaces config file? You can get the text by typing this:
```
cat /etc/network/interfaces
```

---

### Post by Theo Venter on 2008-01-07
Output of cat /etc/network/interfaces =

auto lo
iface lo inet loopback
iface eth0 inet dhcp
auto eth0

---

### Post by ugm6hr on 2008-01-07
@Theo:
Is this your ADSL modem router?
[http://www.dlink.com.au/Products.aspx?Sec=1&Sub1=1&Sub2=2&PID=48](http://www.dlink.com.au/Products.aspx?Sec=1&Sub1=1&Sub2=2&PID=48)

If so, I would *strongly* urge you to get an ethernet (CAT5e or CAT6) patch cable to connect to it, rather than USB.

If you are already connected with ethernet cable, then post the output from:
```
lspci
lshw -C network
```

PS: Can you connect with Windows?

PS2: Which version of Ubuntu are you using?

---

### Post by Theo Venter on 2008-01-07
Im not connected through USB,
will get uotput for you, but must go to work now
cheers for now

---

### Post by Theo Venter on 2008-01-07
yes in XP internet works fine and uses DHCP only.

---

### Post by Theo Venter on 2008-01-07
And yes, thats the exact model of my router!!!

thanx :)

---

### Post by Theo Venter on 2008-01-07
I,m using Ubuntu 7.10 & I boot with the cd. did not instaal yet. Want to make sure I can connect to the internet before I install Ubuntu (maybe dual boot, just incase)

---

### Post by p_quarles on 2008-01-07
Just a couple other things to try, in addition to what ugm6hr suggested. 

First, find out if the interface is fully up:
```
sudo ifup eth0
```
Then, try pinging your router. You'll need to know the precise network address of the router in order to do this:
```
ping -c 8 *router-ip-address*
```

---

### Post by ugm6hr on 2008-01-07
If that is your router - you do not need to use pppoeconf.

The ADSL **modem** **router** makes the DSL connection for you.  If it is on DHCP, then Network Manager should automatically pick it up.

When you turn the computer on and plug into modem, does the light on the modem for the ethernet cable light up?  Do you have any lights on the back of the ethernet card that light up in Windows?

The possibilities are:
1. Your ethernet card is not supported in Ubuntu - *very* unlikely unless you bought a cheap Chinese copy ethernet card (lspci will tell you whether this is true).
2. Windows power-save function is turned on, so Windows disables the card before shutting down, leaving it unaccessible by Ubuntu - see this for more information:
[http://ubuntuforums.org/showpost.php?p=4077372&postcount=14](http://ubuntuforums.org/showpost.php?p=4077372&postcount=14)

---

### Post by ugm6hr on 2008-01-07
> ```

eth0      Link encap:Ethernet  HWaddr 00:15:F2:95:0E:B2  

          inet addr:10.1.1.3  Bcast:10.255.255.255  Mask:255.0.0.0

          inet6 addr: fe80::215:f2ff:fe95:eb2/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:38 errors:0 dropped:0 overruns:0 frame:0

          TX packets:132 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:5345 (5.2 KB)  TX bytes:15340 (14.9 KB)

          Interrupt:19 Base address:0xb000
```


I've just read this again.

It looks like DHCP has assigned an IP (10.1.1.3), and it looks like it is transmitting with no errors.

Are you sure you are not connected?

Pinging your router is a good idea.  Or at least try to access the DLink modem setup page with Firefox.

---

### Post by Theo Venter on 2008-01-08
yes etho is up:

ubuntu@ubuntu:~$ sudo ifup eth0

There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120

Internet Systems Consortium DHCP Client V3.0.5

Copyright 2004-2006 Internet Systems Consortium.

All rights reserved.

For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)



Listening on LPF/eth0/00:15:f2:95:0e:b2

Sending on   LPF/eth0/00:15:f2:95:0e:b2

Sending on   Socket/fallback

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7

DHCPOFFER from 10.1.1.1

DHCPREQUEST on eth0 to 255.255.255.255 port 67

DHCPACK from 10.1.1.1

bound to 10.1.1.3 -- renewal in 1637 seconds

---

### Post by Theo Venter on 2008-01-08
no problem connecting with windows
lspci output:

ubuntu@ubuntu:~$ lspci

00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge

00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge

00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge

00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge

00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge

00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]

00:0c.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)

00:0d.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)

00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)

00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

---

### Post by Theo Venter on 2008-01-08
My ethernet is an onboard one, no pci card

If I ping 10.1.1.1, the ethernet light on my adsl router flash with every ping.
with 10.1.1.3 no flashing and no errors.

is 10.1.1.1 my router or ethernet?

thanx so much

---

### Post by Theo Venter on 2008-01-08
When I enter an url it does not connect but gives an time out error.

---

### Post by Theo Venter on 2008-01-08
I have no powersaving enabled in windows so I don't think that is the problem.

---

### Post by kvonb on 2008-01-08
-

---

### Post by Theo Venter on 2008-01-08
Output of ipconfig :

Windows IP Configuration
Hostname................................:venter
Primary Dns Suffix......................:
Node Type...............................: Unknown
IP Routing Enabled......................: No
WINS Proxy Enabled....................: No

Ethernet adaptor Local Area Connection:
Connection-specific DNS Suffix.......: 
Description..............................: VIA Rhine II Fast Ethernet Adapter
Physical Address........................: 00-15-F@-95-OE-B2
Dhcp Enabled.............................: Yes
Autoconfiguration Enabled.............: Yes
IP Address................................: 10.1.1.3
Subnet Mask.............................: 255.0.0.0
Default Gateway.......................: 10.1.1.1
DHCP Server............................: 10.1.1.1
DNS Servers............................: 10.1.1.1
Lease obtained ..........................etc.
Lease expires................................etc.

---

### Post by Theo Venter on 2008-01-08
No, this is an always on broadband connection(24hr). I just open my browser to get on the net.
No passwords or usernames (only for checking my mail). And no dialup numbers. My connection to the internet (as I understand) is when I switch on my ADSL Router.

Thanx for trying to help me.

I read on another post (launchpad) that there seems to be still unresolved bugs concerning networking in Ubuntu. It seems like Ubuntu doesnt know how to communicate via the router to the internet?:confused:

---

### Post by kvonb on 2008-01-08
-

---

### Post by rkd on 2008-01-08
kvonb: 

The subnet mask of 255.0.0.0 is correct. You just aren't used to seeing it. So don't let that distract you.

The address range 192.168.x.x is the more commonly-used range for private addresses to be used behind firewalls, but the range 10.x.x.x is also a valid private address. If you want to learn more about that, see the article at:

[http://en.wikipedia.org/wiki/Private_network](http://en.wikipedia.org/wiki/Private_network)


Theo: 

So your DHCP stuff seems to be working correctly, as far as I can see. I don't think it is a good idea to try to get the router to change the address range it is using -- it is using valid private addresses already.

I'd say the next test is to ping an outside numeric IP address, for instance:
```
ping -c 4 208.67.222.222
```
If that ping works, then you have connectivity to the outside. Next try to ping an IP name, for instance:
```
ping -c 4 www.google.com
```
If that works, DNS lookup is working.

So try those two experiments and post the results.

---

### Post by Theo Venter on 2008-01-08
Thanx RKD

Funny thing, Sometimes the ping works and sometimes not. I managed to finally getting connected to google.com but no other websites. Sometimes I cant connect to google either.
Whats strange is, I can ping a website and then try to connect with firefox with no success. Its like it connects only when it wants to.
How is it that sometimes I can connect and sometimes not. Success rate is very slim. Only stie I could connect to was google.com, I could search & get search results, but clicking on one of the results and that page just does not want to load.

I seems it may be an Ubuntu problem or perhaps Firefox? Or could this be because I run (boot from ubuntu cd) livecd of Ubuntu? Will this problem disapear when I install Ubuntu?

Secondly, can anyone tell me if I will get an option to create a dual boot when installing Ubuntu 10.7

Thanx
Theo

---

### Post by p_quarles on 2008-01-08
This could be an IPv6 problem. Was there any difference in results between pinging "google.com" and pinging the numeric IP address (72.14.207.99)?

---

### Post by rkd on 2008-01-08
It is hard to say what is causing that erratic behaviour. I have no idea whether it would go away if you installed to the hard disk. I can tell you that when I have been running a live CD, I've not seen that kind of problem, but I'm just one case.

As p_quarles says, it might be an IPv6 problem. There have been some cases of network problems that were cured by turning off IPv6. (IPv6 the upgrade of IPv4, which is the way computers communicate over the Internet -- IPv6 is Internet Protocol version 6. IPv4 is still usable, so you aren't turning off the internet.). I've seen a number of different instructions about how to turn off IPv6. This might work, but I've not tried it (you can use your favorite editor in place of nano):
```
sudo /etc/inet.d/networking stop
sudo modprobe -r ipv6
sudo nano /etc/modprobe.d/aliases

Find this line:

alias net-pf-10 off

and replace with:

alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off
#alias net-pf-10 ipv6

Save the file and exit.

sudo echo "blacklist ipv6" >> /etc/modprobe.d/blacklist

sudo nano /etc/hosts

Find these lines:

::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

and replace with:

#::1 ip6-localhost ip6-loopback
#fe00::0 ip6-localnet
#ff00::0 ip6-mcastprefix
#ff02::1 ip6-allnodes
#ff02::2 ip6-allrouters
#ff02::3 ip6-allhosts

sudo depmod -a
sudo /etc/inet.d/networking start

```

Another possible explanation is that there is a long-standing problem with the VT6102 Rhine II ethernet controller, which is the one your computer has. The reports of this problem usually mention the computer locking up, but it might give other problems in some computers. To try the workaround for this problem, when booting the live CD, push F6 when the boot menu appears. A line of text will appear below the boot menu. Use the left arrow key to backspace over the two hyphens then type acpi=noirq and push Enter. The boot will continue with that extra option in effect. It might not help, but it seems easy to try.

Here is the bug report, in case you are interested:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/48263](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/48263)                  

and here is an article that shows how to put that option in the GRUB menu, should you decide to install to the hard disk:

[http://www.lockergnome.com/linux/2007/11/27/ubuntu-wired-networking-woes-read-this-closely/](http://www.lockergnome.com/linux/2007/11/27/ubuntu-wired-networking-woes-read-this-closely/)

It might be that neither of the above problems is what is affecting you. Maybe someone else will post another possible fix.

---

### Post by Theo Venter on 2008-01-09
Thanx rdk,

Will try and let you know what happened.

Cheers

---

### Post by KRTW on 2008-01-11
Hi all... I'm new.

I've been following this thread Theo, I'm having the exact same problem. I have the same router but Ubuntu 7.10 is installed. So maybe that clears up the issue with the LiveCD. As of a few days ago, I had windows on this machine and had no problems. Once I installed Ubuntu, I couldn't get on the internet but successful pinging (sometimes). I'm doing all the tests recommended for Theo and getting the same output.

Keep it up, this is great!

Let me know if I can help

has to be the stupid dlink router right????

---

### Post by Theo Venter on 2008-01-12
[QUOTE=rkd;4098754]

and replace with:

#::1 ip6-localhost ip6-loopback
#fe00::0 ip6-localnet
#ff00::0 ip6-mcastprefix
#ff02::1 ip6-allnodes
#ff02::2 ip6-allrouters
#ff02::3 ip6-allhosts

sudo depmod -a
sudo /etc/inet.d/networking start
[/CODE]

Hi rdk, 

These line you want me to replace with exact same lines? or did you make a mistake?

Thanx
Theo

---

### Post by rkd on 2008-01-12
The intended change is to add the "#" character to the beginning of each of those lines.  The "#" is the comment character -- it makes the software ignore the remainder of the line. Yes, it is a little hard to notice when you aren't used to such things.

Something similar was done with one of the lines in the change to the aliases file. Please make sure you didn't overlook the "#" on that one.

This is a fairly common technique when someone wants to remove some commands from a file, but leave a record of what was there originally.

Please remember that I don't really have any idea why your network connection is so erratic, so I don't know whether the changes suggested in that thread I copied these from will do you any good. But they seem worth trying.

---

### Post by smurphy_it on 2008-01-31
With ADSL you normally have to tell it your username / password to gain access to their network.  I'm not sure how to go about this in Ubuntu but I'm sure you'd be using some kind of a pppoe connection.  I use cable, so I've never had to figure it out up to this point.

Did you try the PclinuxOS liveCD ?  It runs the network configuration wizard out of the gate when you are launching the liveCD.  So you should be able to browse the internet, etc fairly quickly.

---

### Post by bumanie on 2008-01-31
I too suspect it is the ipv6 issue, however, as far as I can recollect, this can only be rectified by actually installing ubuntu onto your hard drive (I think earlier in the thread you said you were using the live cd - sorry only skimmed over the four pages, viewing what hasn't helped so far).
90% of the time when the internet will not work on 7.10, it is due to the ipv6 issue. If it ipv6 causing your connection problems, it's easily fixed, but I fairly sure it can only be configures once the OS is installed onto a hard drive. (When I installed 7.1, blacklisting ipv6 was the only way I could get the internet working).

---

