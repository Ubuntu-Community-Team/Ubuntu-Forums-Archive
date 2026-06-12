---
title: "Gutsy Wireless..Careful what u wish 4!"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by k8fox1 on 2008-01-25
I finally got my wireless working with Gutsy. NDISwrapper, BCM43xx-firmware and and bOOm- blazing wireless on my Dell D820. Even WEP secured networks, it works!

B-U-T

Now my wired connection is broken. When I attempt to switch to eth0 I get "Not configured" though it is. Ughh....ideas?

Careful what you wish 4 in Ubuntu-land!!

---

### Post by wieman01 on 2008-01-25
> **k8fox1 said:**
> I finally got my wireless working with Gutsy. NDISwrapper, BCM43xx-firmware and and bOOm- blazing wireless on my Dell D820. Even WEP secured networks, it works!

WEP isn't secure... That's an oxymoron.

What makes you think it does not work? What are the symptions? Please post:
> sudo lshw -C network

---

### Post by k8fox1 on 2008-01-25
Well WEP keeps my freeloading neighbors from using my network so thats good enough for me! :)

Here what I see:

  *-network               
       description: Wireless interface
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:19:7e:5b:08:46
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic ip=172.16.161.31 latency=0 link=yes module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:75:e8:cb
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.77 duplex=full firmware=5752-v3.19 latency=0 link=no module=tg3 multicast=yes port=twisted pair speed=1GB/s

Thanks!

---

### Post by wieman01 on 2008-01-25
> **k8fox1 said:**
> Well WEP keeps my freeloading neighbors from using my network so thats good enough for me! :)

No issues, just be aware of the constraints.

Looks perfect in fact. So what exactly does not work? Do you use Network Manager to connect to your local network? What steps do you perform?

---

### Post by k8fox1 on 2008-01-25
Forgive my beginner-ness but..............

When I attempt to switch to eth0:avahi via the connection properties icon on the top tool bar i get the error message "The interface Does Not Exist" 

Network Manager-Should I be using it and if so do you have any tips?

---

### Post by wieman01 on 2008-01-25
Hope you are a bit familiar with the terminal. Please open a terminal window and issue the following command:
> sudo gedit /etc/network/interfaces
Post the contents here.

---

### Post by k8fox1 on 2008-01-25
I love the terminal. Beats the pant off a DOS prompt!!!

Ok here you go.

auto lo
iface lo inet loopback

iface eth1 inet dhcp
wireless-essid CaseGuest

auto eth1

iface eth0 inet dhcp

auto eth0

---

### Post by wieman01 on 2008-01-25
Good. :-)

So I hope you use Network Manager. Please update the file so that it reads:
> auto lo
iface lo inet loopback
Then restart the PC and try again. Don't worry, it's save. You should be able to connect now.

---

### Post by k8fox1 on 2008-01-25
The file reads:

auto lo
iface lo inet loopback

iface eth1 inet dhcp
wireless-essid CaseGuest

auto eth1

iface eth0 inet dhcp

auto eth0

Which line am i changing?

Regarding network manager. I get that as a synaptic download right. Once loaded where do I access it from?

---

### Post by wieman01 on 2008-01-25
The file should only read:
> auto lo
iface lo inet loopback
No more, no less. The restart the computer.

NM should be somewhere in the menu... I use KDE so I cannot tell exactly where it is. Isn't there a network icon in the tray?

---

### Post by seventhc on 2008-01-25
look under system>administration it might just be called network in the menu, but you can change the interface there.
you should see network and network tools have a look at both. :)

---

### Post by wieman01 on 2008-01-25
> **seventhc said:**
> look under system>administration it might just be called network in the menu, but you can change the interface there.
you should see network and network tools have a look at both. :)
Thanks. :-)

---

### Post by k8fox1 on 2008-01-25
Oh man I made the change and it killed everything. No network at all.


 I am attempting to restore........

Posted from a Vista machine....ughhhhh:(

---

### Post by wieman01 on 2008-01-25
You can restore by copy & pasting from here. 

Thing is, network manager should now be able to establish a connection. Have you tried it?

---

### Post by k8fox1 on 2008-01-25
Ok I restored sudo gedit /etc/network/interfaces to it original config and everything is back. Under network tools I see the following choices:

lo
eth0
eth1
eth0:avahi

I am thinking lo is my ethernet and eth1 is my wireless?

---

### Post by seventhc on 2008-01-25
if you open a terminal and put
```
ifconfig
```
It should show you all of your different network devices.
and I think 
```
iwconfig
``` should show your wireless

---

### Post by akniss on 2008-01-25
> **k8fox1 said:**
> Ok I restored sudo gedit /etc/network/interfaces to it original config and everything is back. Under network tools I see the following choices:

lo
eth0
eth1
eth0:avahi

I am thinking lo is my ethernet and eth1 is my wireless?

eth0 is your ethernet.
eth1 is your wireless.
lo is the loopback (the computer's way of talking to itself).

In the upper right of your desktop, on the panel, do you have an icon for your networking?  If you left-click on the icon, what options does it give you?  How about if you right-click?

---

### Post by k8fox1 on 2008-01-25
$ iwconfig
lo        no wireless extensions.

eth0    no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"CaseGuest"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:0F:34:53:8E:00   
          Bit Rate=24 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=46/100  Signal level=-78 dBm  Noise level=-72 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

------
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:B9:75:E8:CB  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:19:7E:5B:08:46  
          inet addr:172.16.161.31  Bcast:172.16.161.255  Mask:255.255.254.0
          inet6 addr: fe80::219:7eff:fe5b:846/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9997 errors:0 dropped:418 overruns:0 frame:0
          TX packets:4739 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3713849 (3.5 MB)  TX bytes:694931 (678.6 KB)
          Interrupt:3 

eth0:avah Link encap:Ethernet  HWaddr 00:19:B9:75:E8:CB  
          inet addr:169.254.10.130  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by k8fox1 on 2008-01-25
In the upper right corner I have a network icon. By right clicking it the options are:

Properties
Help
About
Remove from panel
Move
Lock to panel

Currently I am using my wireless connection

---

### Post by seventhc on 2008-01-25
looks like eth1 is your wireless. But your connected now so its working right?
You can also left click on that icon if you want a manual configuration but then you lose the wireless icon and it changes into like netwoked computers. not sure how to change it back but I personally have my wireless set up manually.
If it's working I'd leave it as is. :)

---

### Post by wieman01 on 2008-01-25
Can somebody post a screenshot of NM? I don't have Gnome so I cannot do it myself. It might help to show k8fox1 the options it has.

---

### Post by k8fox1 on 2008-01-25
Yea seems to be working, I manually type in eth0 and i get my wired network. What is eth0:avahi? It would be nice to get a drop down of available wireless networks on the tool bar but I guess we'll just go the manual route for now.

Thanks for all your suggestions and help!

---

### Post by k8fox1 on 2008-01-25
I installed NM from Synaptic but fail to see it anywhere?

---

### Post by k8fox1 on 2008-01-25
Ok folks I'm good thanks for the assistance!

---

