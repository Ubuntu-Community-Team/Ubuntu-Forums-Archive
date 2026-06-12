---
title: "wireless Networking"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by SupremeSpike on 2006-06-08
I go into networking under adminstration, and my wireless connection shows up as eth1.  I activate it and setup all my network options such as SSID and WEP keyIt is a broadcom wireless chip I recieved with my laptop zx5000.  After I click activate it activates, the only problem is I am not conntected to the wireless.  I exit the networking screen, and reopen it and it says my network connection is not active.  I'm confused.

---

### Post by carlosqueso on 2006-06-08
What happens when you type ```
sudo ifup eth1
``` in a terminal?

---

### Post by SupremeSpike on 2006-06-08
ifup: interface eth1 already configured

---

### Post by SupremeSpike on 2006-06-08
no luck yet...have to use windows to connect wirelessly...

---

### Post by maddbaron on 2006-06-08
your having the same issue i am. i have done everything i have found to fix it. sadly still gotta use windows to connect wirelessly. but once i get this fixed bye bye windows...if u get a solution can u put it back in this forum or pm me please?

---

### Post by harishg on 2006-06-08
I also had a similar problem when i got my dsl connection.I looked at the id and realised i selected ascii when my id was in hexadecimal format.Try changing them and it may work.

---

### Post by maddbaron on 2006-06-08
i had that set. i didnt help me either. i really hope someone finds a solution to the broadcom airforce one problem.

---

### Post by nalmeth on 2006-06-08
Isn't the wireless supposed to be setup was wlan0?
Have you read through the Wireless Troubleshooting Guide?
Click Wireless Help in my signature for the link.

---

### Post by SupremeSpike on 2006-06-09
Yea i read through the wireless help.  I have also tried the ndiswrapper and several other work arounds.  I have a broadcoam chip in this HP, nothing has worked i can sometimes get the wireless light to display near the keyboard of my lappy if I play around with the eth1 by enabling and disabling it.  Damn!  Nothing seems to work I may just reinstall Ubuntu with all the stuff I did to it I may have messed up the drivers.  For now if I am downstair I use windows xp, I am dling the new vista beta while i research this problem.  I wish it would work.  Thanks for the help so far!

---

### Post by sherlock-holmes on 2006-06-09
[QUOTE=SupremeSpike]Yea i read through the wireless help.  I have also tried the ndiswrapper and several other work arounds.  I have a broadcoam chip in this HP, nothing has worked i can sometimes get the wireless light to display near the keyboard of my lappy if I play around with the eth1 by enabling and disabling it.  Damn!  Nothing seems to work I may just reinstall Ubuntu with all the stuff I did to it I may have messed up the drivers.  For now if I am downstair I use windows xp, I am dling the new vista beta while i research this problem.  I wish it would work.  Thanks for the help so far![/QUOTE]


4  things that come to mind...

1. is it the only network card that is active? it might not work when two network cards (eth1, eth0 for eg.) are active at the same time... the default goes to the most preferred one , in my experience the one which we select during install ... (or the one which is connected at that time)

2. which router do u use? try making the keyindex = 1. 

then 
```
sudo /etc/init.d/dbus restart
```

3. do u have the latest firmware for the card installed? that could be a factor..



4. do you have network-manager-gnome installed? ifyou have wired connection you can do this by
```
sudo apt-get install network-manager-gnome
```

if you cannot connect with wired, then use xp to download the deb and somehow transfer it and install the deb by 
```
sudo dpkg -i network-manager-gnome-something.deb
```

then comment out all network interfaces except that of 'lo' from 
```
sudo gedit /etc/network/interface
```
and then restart by the previous command (dbus restart)

see if these helps...good luck..

---

### Post by Dragonfire on 2006-06-09
[QUOTE=nalmeth]Isn't the wireless supposed to be setup was wlan0?
Have you read through the Wireless Troubleshooting Guide?
Click Wireless Help in my signature for the link.[/QUOTE]


Actually the wireless can be nearly anything. My laptop has multiple wireless cards inserted to allow me to run it as a wireless server.

one card appears as wlan0
another as ath0
yet another as eth0
and the final card as eth1

so it's quite possible for it to take nearly any name.

---

### Post by nanotube on 2006-06-09
hi
after you activate the card, open the terminal, and run the command "ifconfig"
and also run the command "iwconfig"
and post the output of these two commands here so that we may have a look.

---

### Post by SupremeSpike on 2006-06-09
```
sudo /etc/init.d/dbus restart
```
After that my little connection manager shows my wireless options.  I have a linksys wrt54g and now the it won't connect to the router.  Odd, I have tried changing the key numbers for the WEP both on the lappy and the router, no luck.  I even have tried WPA.  Still no luck it will not connect.  Thanks for getting me this far guys! :grin:

---

### Post by SupremeSpike on 2006-06-09
ryan@ryan-laptop:~$ ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:0A:DB:1B
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:201 Base address:0xc800

eth1      Link encap:Ethernet  HWaddr 00:90:4B:5F:FF:F3
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:182 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:6118 (5.9 KiB)
          Interrupt:5

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

```
ryan@ryan-laptop:~$ iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"linksys"  Nickname:"Broadcom 4301"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid
          Bit Rate=11 Mb/s   Tx-Power=16 dBm
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

---

### Post by nanotube on 2006-06-09
well, from the output, looks like all is ok, except you dont get an ip address.
check if dhclient is running 
```
ps ax |grep dhc
```
if not, run
```
dhclient eth1
```
hell, even if yes, try running it anyway :)

---

### Post by SupremeSpike on 2006-06-09
ok well here is what I got:
```
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:90:4b:5f:ff:f3
Sending on   LPF/eth1/00:90:4b:5f:ff:f3
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

---

### Post by maddbaron on 2006-06-09
[QUOTE=nanotube]hi
after you activate the card, open the terminal, and run the command "ifconfig"
and also run the command "iwconfig"
and post the output of these two commands here so that we may have a look.[/QUOTE]


I have same problem. can you help me too?
> maddbaron@alchemist:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:A3:21:48
          inet addr:192.168.1.38  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fea3:2148/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:886142 errors:0 dropped:0 overruns:0 frame:0
          TX packets:665752 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1217757550 (1.1 GiB)  TX bytes:53448822 (50.9 MiB)
          Interrupt:169 Base address:0x1800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1468 (1.4 KiB)  TX bytes:1468 (1.4 KiB)

maddbaron@alchemist:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"baronnet"  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


> maddbaron@alchemist:~$ ps ax |grep dhc
 4512 ?        Ss     0:00 /sbin/dhcdbd --system
 4902 ?        S      0:00 /sbin/dhclient -1 -lf /var/lib/dhcp3/dhclient.eth0.leases -pf /var/run/dhclient.eth0.pid -q -e dhc_dbus=31 -d eth0
14771 ?        Ss     0:00 /sbin/dhclient3 -pf /var/run/dhclient.eth1.pid eth1
maddbaron@alchemist:~$ dhclient eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

can't create /var/lib/dhcp3/dhclient.leases: Permission denied
Can't create /var/run/dhclient.pid: Permission denied
drop_privileges: could not set group id: Operation not permitted


---

### Post by nanotube on 2006-06-09
[QUOTE=SupremeSpike]ok well here is what I got:
```
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:90:4b:5f:ff:f3
Sending on   LPF/eth1/00:90:4b:5f:ff:f3
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```[/QUOTE]

one question: is your wired ethernet unplugged?

---

### Post by nanotube on 2006-06-09
[QUOTE=maddbaron]I have same problem. can you help me too?[/QUOTE]
from your output, it looks like your wired ethernet is connected properly. since ubuntu only plays with one net connection at a time, i am guessing if you unplug your ethernet wire, the wireless should start working for you. give it a try.

---

### Post by maddbaron on 2006-06-09
nope doesnt work. i uninstalled and nothing happened and my light didnt come on. i dont know what to do.

---

### Post by Jagot on 2006-06-09
I have a Dell with a Broadcom 4318.  The only way I can get it working is to use ndiswrapper, however Dapper comes with Broadcom drivers already (but they didn't work for me), so I had to blacklist them to ensure ndiswrapper had complete control of the driver situation:

```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

sudo rmmod bcm43xx

sudo rmmod ndiswrapper

sudo modprobe ndiswrapper
```

Works perfectly now.

---

### Post by maddbaron on 2006-06-09
after u typed that it worked perfect for u? i use an acer mite not work for me. 

confused.

---

### Post by Jagot on 2006-06-09
I installed the driver with ndiswrapper first, then issued those commands in my previous post to make sure that the drivers that come with Ubuntu don't take over - it stops them from starting up, so ndiswrapper is just left to handle the wireless.

It may or may not work for you, I don't know, but it's just another possibility.  But as I say, worked for me.

---

### Post by maddbaron on 2006-06-09
ok i have the 2 needed drivers on my desktop how may i install them please? what do i type in terminal?

---

### Post by Jagot on 2006-06-09
Tthis assumes your driver is put on the desktop and bcmwl5.inf happens to be the driver for my card - if it isn't on the desktop then just change according to wherever you've dumped the driver:

```
sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
```

Then, to check it is installed properly:

```
sudo ndiswrapper -l
```

Now we need to probe the module:

```
sudo modprobe ndiswrapper
```

And finally:

```
sudo ndiswrapper -m
```

Then run the code in my previous post.

---

### Post by maddbaron on 2006-06-09
IT WORKED!!!!!! thank you!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! but question i dont see a strength indicator next to the time thing at the top, i see the wired connection icon  with the x in it since i am not wired to my dsl anymore. how can i change that to another icon?

when i hover over it says no network connection but i am online.

i want to make sure its my network its connected too. how do i check?

and once again THANK YOU!

---

### Post by SupremeSpike on 2006-06-09
Still no luck for me.  I am going to just reinstall ubuntu and try this all over again.  Let me first wait on vista beta 2 to finish installing.  Thanks for the help so far!

---

### Post by eltaito on 2006-06-10
Dapper is the first version of Ubuntu to recognize Broadcom chipsets out of the box...HOWEVER due to reasons I don't understand (probably legal ones) you still need to provide Dapper with the drivers to get the card working. Ndiswrapper used to be the only way to do it but since Dapper recognizes your card you can use bcm43xx-fwcutter method now.  Check out this tutorial if you have been having problems with Ndiswrapper:

[http://ubuntuforums.org/showthread.php?t=185174]("http://ubuntuforums.org/showthread.php?t=185174")

This works great on my Broadcom 4306 chipset and more importantly it isn't causing problems after kernel upgrades like Ndiswrapper used to. Hope this helps somebody.

Edit:  I should also note that this really only works well with the 4306 chipset....it is working with the 4318 as well but with very limited success....I'd recomend sticking with Ndiswrapper if you have the 4318 chipset.

---

### Post by SupremeSpike on 2006-06-10
I tried that but also no help, so that is why I tried the ndiswrapper.

---

### Post by tartarian on 2006-06-10
I had loads of wireless problems also - but I fixed them! Did you say that Ubuntu doesn't seem to be connecting to your router/access point??? Happend to me aswell. I got it to recognise it by setting the physical address of the router and now it works fine! You can set your physical address by:

sudo iwconfig [wireless device e.g eth0] ap [physical address of router]

You should be able to find your physical address on either the back of the router or by typing 192.168.1.1 into a browser (with a connection) and finding it on there.

If that doesnt work then you could type ```
sudo iwconfig man
``` to get a list of other options that you could try!

---

### Post by sherlock-holmes on 2006-06-10
[QUOTE=SupremeSpike]Still no luck for me.  I am going to just reinstall ubuntu and try this all over again.  Let me first wait on vista beta 2 to finish installing.  Thanks for the help so far![/QUOTE]


paste ur /etc/network/interface file here..

---

