---
title: "Lost network in Ubuntu"
date: 2010-10-24
forum: Apple Hardware Users
---

### Post by WanderingOak on 2010-10-24
I have a new install of Lucid Lynx on an iMac7,1. Everything was working fine this morning, but about an hour ago, Ubuntu lost all internet connectivity. I was able to fix the problem temporarily on one account, under 'network settings' by telling it to configure IPv4 using DHCP. I tried to apply this across the system, but my other Ubuntu account was still not able to connect. After a few minutes of connectivity, all access was lost once again. An icon on the upper right corner of my monitor says 'network disabled'.

The issue started when I attempted to have my system 'hibernate'. The system became completely unresponsive, and I had to hold down the power switch and reboot. When I re-logged into Ubuntu, I had no network.


I am still able to connect with Snow Leopard.

---

### Post by WanderingOak on 2010-10-24
I just tried to connect directly to my DSL router with Ubuntu. However, for some reason, I am unable to even do that. All I got was the 'Firefox is unable to connect' message. Going into the router with my Mac, everything on the router looks good.

---

### Post by WanderingOak on 2010-10-24
I enabled logging in the router, and tried to connect with Ubuntu again. The router did not log any blocked connections, so I don't think the problem is there.

---

### Post by WanderingOak on 2010-10-25
Well, WIFI won't work either. I can't see my router (or any other networks), and entering everything by hand didn't work. My 'alternate' admin account was able to connect briefly but lost it less than a minute later. I am unable to ping my router from either account. Are there any alternate Ethernet drivers that I can download?

---

### Post by WanderingOak on 2010-10-25
After googling about a bit, I decided to try the following:
> 
  lspci | grep Ethernet  
which returned the following:

>   05:00.0 Ethernet controller: Marvell Technology Group Ltd. Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller (rev 13)  
 So, Ubuntu can see my ethernet card, but apparently it can't use it. 

Any ideas?

---

### Post by WanderingOak on 2010-10-26
I'm still trying to figure this out. 

lspci returns:

> 00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon HD 2400 XT
03:00.0 FireWire (IEEE 1394): Agere Systems FW643 PCI Express1394b Controller (PHY/Link) (rev 06)
04:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
05:00.0 Ethernet controller: Marvell Technology Group Ltd. Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller (rev 13)


Any ideas?

---

### Post by linuxopjemac on 2010-10-26
what does ifconfig tell you?
```
ifconfig
```

---

### Post by WanderingOak on 2010-10-26
ifconfig returned:

> lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

I ran ifconfig eth0 and got:

> eth0      Link encap:Ethernet  HWaddr 00:1f:5b:ee:d7:a9  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

I haven't run iwconfig yet (didn't know how to check wireless until just now). I will post the results in a few minutes.

---

### Post by WanderingOak on 2010-10-26
iwconfig returned:

> lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.


One of my alternate admin accounts was able to connect wirelessly, before I lost everything.

---

### Post by WanderingOak on 2010-10-26
Dug a bit deeper and read the man files for ifconfig and ifup. I tried:
> sudo ifconfig up eth0  and got nothing, even when I tried -v. 

I then ran > sudo ifup -v eth0 and got the following: > Ignoring unknown interface eth0=eth0.

going deeper, I looked inside /etc/network/interfaces to find:
> auto lo
iface lo inet loopback

while /var/run/network/ifstate returned: > lo=lo

So something is definitely broken. Can /etc/network/interfaces and /var/run/network/ifstate be edited by hand, or are they system generated?

---

### Post by linuxopjemac on 2010-10-27
this looks very weird to me:

```
sudo ifup -v eth0
Ignoring unknown interface eth0=eth0
```

I don't know what to do with that, other than to edit /etc/network/interfaces

```
sudo nano /etc/network/interfaces
```

and make the file look like this:

```
auto lo
iface lo inet loopback
allow-hotplug eth0
iface eth0 inet dhcp

```
Then:
```
sudo ifdown eth0
sudo ifup eth0
```

That should work.

Remark: in this way you don0t need a networkmanager like networkmanager or wicd to take care of eth0.

reference:
[http://www.debian.org/doc/manuals/reference/ch05.en.html#_the_basic_syntax_of_etc_network_interfaces](http://www.debian.org/doc/manuals/reference/ch05.en.html#_the_basic_syntax_of_etc_network_interfaces)

---

### Post by WanderingOak on 2010-10-27
Woooot!!!!

I'm posting this from within Ubuntu, so from the looks of things, everything is working. 
sudo ifdown eth0 returned 

> interface eth0 not configured
 and sudo ifup eth0 returned
>    Listening on LPF/eth0/00:1f:5b:ee:d7:a9 
 Sending on   LPF/eth0/00:1f:5b:ee:d7:a9 
 Sending on   Socket/fallback 
 DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4 
 DHCPOFFER of 192.168.1.45 from 192.168.1.1 
 DHCPREQUEST of 192.168.1.45 on eth0 to 255.255.255.255 port 67 
 DHCPACK of 192.168.1.45 from 192.168.1.1 
 bound to 192.168.1.45 -- renewal in 37505 seconds. 
  Now for the million dollar question- how did this happen, and how do I keep it from happening again?

Eventually, I am going to want wifi up and running so I can link to my droid tablet, but that can wait for now.

I'm going to reboot, just to make sure that the changes 'stuck'.

---

### Post by linuxopjemac on 2010-10-27
good old fashioned interfaces file...I am wondering though why Ubuntu doesn't even get a wired ethernet connection configured.

---

### Post by WanderingOak on 2010-10-27
Well, it worked- somwhat. I was able to get online from within Ubuntu. I posted the results here a few minutes ago, but I don't think they went through. Very odd, as I could see my response in this very thread. However, now it seems to be gone. It was almost as if my posting was on a local cache. Either that of the forums are wonky this morning.

Anyhow, thinking all was good, I rebooted to see if the changes 'stuck'. they didn't. The changes I made to /etc/network/interfaces remained, but eth0 was down. I had to sudo ifup eth0 in order to get my network up. That should be turned on at boot, shouldn't it? 

Anyhow, I have to get ready for work. I hope this goes through....

---

### Post by WanderingOak on 2010-10-27
D'oh!!!!

I was working from a cached version of the forums just now. FF was offline.....

---

### Post by linuxopjemac on 2010-10-27
if you want it automatic, add  the following line in /etc/network/interfaces:

```
auto eth0
```

---

### Post by WanderingOak on 2010-10-27
> **linuxopjemac said:**
> good old fashioned interfaces file...I am wondering though why Ubuntu doesn't even get a wired ethernet connection configured.
 Everything was working for the first few hours of the intallation, through several reboots, login/outs of both OS's, monkeying about with user accounts, etc. Then, I made the mistake to telling my iMac to 'hibernate'- I figured that was a low-power idle mode, akin to 'sleep' in OSX. After I did that, the screen darkened to a single blinking cursor and my computer wouldn't respond to keyboard or mouse inputs. Nothing I could do would wake it up, so I had to hold down the power switch for a forced reboot. When I logged back into Ubuntu, I had no network. Unfortunately, I have no idea what the interfaces file looked like before my hibernation...

---

### Post by WanderingOak on 2010-10-27
> **linuxopjemac said:**
> if you want it automatic, add  the following line in /etc/network/interfaces:

```
auto eth0
```
Well, ethernet comes up automaticly now. However, when I login, I still have a notification in the upper right corner that 'networking is offline'. Also, in the toolbar on the upper corner, there is an icon that says 'networking disabled'. Under 'network connections'. I don't have any wired connections listed. However, I can ping my router, and I can see it's status in Firefox. So, I am online, but the Gnome desktop thinks otherwise...

---

### Post by linuxopjemac on 2010-10-28
That's what I told you. If you force eth0 in this way, network-manager won't work anymore on this interface.

---

### Post by WanderingOak on 2010-10-28
Another issue is that I installed Dockey. Now, if I am trying to use a docklet that requires 'net access (such as streaming radio or weather), they are unalble to connect. I am also unable to sync up with Ubuntu One. So, I am probably going to have to un-bork the Network Connections utility at some point in time. How does that tool get it's information?

---

### Post by linuxopjemac on 2010-10-28
If you want to disable, just empty the eth0 part of /etc/network/interfaces (you can add a # in front of the entries).

---

### Post by WanderingOak on 2010-10-28
> **linuxopjemac said:**
> If you want to disable, just empty the eth0 part of /etc/network/interfaces (you can add a # in front of the entries).
 That would disable my ethernet, wouldn't it? I was just wondering where Gnome gets it's information from. Obviously, it doesn't rely on the interfaces file, because it would see my ethernet connection. Ubuntu One thinks my Mac is a standalone machine without any cnnectivity. There is still a disconnect somewhere in my system, and I was hoping that somebody could provide input.

---

### Post by linuxopjemac on 2010-10-28
In principle, wicd or network-manager should be able to setup a wired connection without the need to edit /etc/network/interfaces. I use Linux Mint 9 which is based on Lucid Lynx on my MacBook 2,1. Gnome's network-manager works out of the box for me.

My /etc/network/interfaces is not configured:
```
auto lo
iface lo inet loopback
```


You might want to try wicd, which is a better alterntive to network-manager to my opinion.

---

### Post by WanderingOak on 2010-10-28
> **linuxopjemac said:**
> 
You might want to try wicd, which is a better alterntive to network-manager to my opinion.
Well wicd did the trick as far as convincing Gnome and Ubuntu One that I was indeed online. I can also see my wireless network, so i am going to mark this as solved!

Thank you for your assistance linuxopjemac !!!!!

---

### Post by rsavage on 2011-03-03
I know this is an old thread, but I just came across this problem.  After hibernate the computer wouldn't restart properly and i had to power it off and restart.  Wireless networking then didn't work.  The solution to get wireless working was:

Right click on Network Manager Applet and select "Enable Networking"!!!

A simple solution that others may find useful!

Now, anybody got a way of making Hibernate work??

---

