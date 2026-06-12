---
title: "wireless card hell"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by mwanafunzi on 2006-07-31
I have installed ubuntu and re-installed ubuntu just so that I can get my wireless card working. To elaborate here is what i did.

I installed Dapper. Then i installed my wireless card windows driver with the help of ndiswrapper ( sudo ndiswrapper -i rt2400.INF, sudo ndiswrapper -l, sudo ndiswrapper -m, sudo modprobe ndiswrapper). After this process I was able to get online. The problem came in after I updated my system then restarted my computer. I was not able to get online again. I was not sure what the problem was, so I re-installed ubuntu. 

I went through the process mentioned above and managed to get back online. But after an upgrade I and a restart I am not able to go online. 

When I upgrade I also notice that I know have two kernels to choose from 
2.6.15-26-386 and 2.6.15-23-386. 

can someone please help..

---

### Post by bensexson on 2006-07-31
Did you compile ndiswrapper from source or did you get the ndiswrapper-utils package from apt?

---

### Post by cantormath on 2006-07-31
> **mwanafunzi said:**
> I have installed ubuntu and re-installed ubuntu just so that I can get my wireless card working. To elaborate here is what i did.

I installed Dapper. Then i installed my wireless card windows driver with the help of ndiswrapper ( sudo ndiswrapper -i rt2400.INF, sudo ndiswrapper -l, sudo ndiswrapper -m, sudo modprobe ndiswrapper). After this process I was able to get online. The problem came in after I updated my system then restarted my computer. I was not able to get online again. I was not sure what the problem was, so I re-installed ubuntu. 

I went through the process mentioned above and managed to get back online. But after an upgrade I and a restart I am not able to go online. 

When I upgrade I also notice that I know have two kernels to choose from 
2.6.15-26-386 and 2.6.15-23-386. 

can someone please help..

What wireless card are you using?

---

### Post by mwanafunzi on 2006-07-31
I used apt-get ndiswrapper-utils; and this is the card that I am using 
"PCMCIA (MNW2BPCM) & PCI Wireless Card (MNW2BPCI)". 
The driver is the rt2400 driver.

---

### Post by cantormath on 2006-07-31
> **mwanafunzi said:**
> I used apt-get ndiswrapper-utils; and this is the card that I am using 
"PCMCIA (MNW2BPCM) & PCI Wireless Card (MNW2BPCI)". 
The driver is the rt2400 driver.

Im really suprised you cant get that card working natively (without ndiswrapper) with ubuntu.  Does the card show up when you iwconfig or ifconfig?

---

### Post by mwanafunzi on 2006-07-31
Yes it shows up with iwconfig, i have not used ifconfig. Sorry I cannot give a more detailed answer than this as I am currently on windows..

---

### Post by cantormath on 2006-07-31
> **mwanafunzi said:**
> Yes it shows up with iwconfig, i have not used ifconfig. Sorry I cannot give a more detailed answer than this as I am currently on windows..

So the card is showing up in iwconfig. Thats good.
what does it say in the terminal after you type iwconfig?

ie)
[I]
cantormath-laptop:/$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11g  ESSID:"virusdownloader.dll"  Nickname:"virusdownloader.dll"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:E0:98:52:34:76
          Bit Rate:36 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=23/94  Signal level=-72 dBm  Noise level=-95 dBm
          Rx invalid nwid:688268  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:36  Invalid misc:36   Missed beacon:0

sit0      no wireless extensions.
[/I]

my wireless card is showing up as ath0.  Yours should be ath0 or wlan0, etc.

Also, copy what your ifconfig says. 
ie)
mine says,
[I]

cantormath-laptop:/$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:90:96:CB:AC:64
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:96ff:fecb:ac64/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:11772472 errors:1516238 dropped:0 overruns:0 frame:1516238
          TX packets:10536019 errors:36 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:2476198645 (2.3 GiB)  TX bytes:452277763 (431.3 MiB)
          Interrupt:209 Memory:dcac0000-dcad0000

eth0      Link encap:Ethernet  HWaddr 00:02:3F:D6:34:DC
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:201 Base address:0x4800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:549 errors:0 dropped:0 overruns:0 frame:0
          TX packets:549 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:41144 (40.1 KiB)  TX bytes:41144 (40.1 KiB)[/I]

---

### Post by mwanafunzi on 2006-07-31
Before i reboot and go into ubuntu, there was one difference with the output when it was working as opposed to when it wasnt. When it was working iwconfig displayed my access point. 
It looked very much like your iwconfig. Anyway, I will boot in and get the info and post it up.

---

### Post by cantormath on 2006-07-31
> **mwanafunzi said:**
> Before i reboot and go into ubuntu, there was one difference with the output when it was working as opposed to when it wasnt. When it was working iwconfig displayed my access point. 
It looked very much like your iwconfig. Anyway, I will boot in and get the info and post it up.

k

---

### Post by mwanafunzi on 2006-07-31
kitabu@floonie:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2400PCI  ESSID:"default"
          Mode:Managed  Channel=1  Access Point: 00:80:4B:1A:6C:80
          Bit Rate:11 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:78  Signal level:45  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

sit0      no wireless extensions.

kitabu@floonie:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:71 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6441 (6.2 KiB)  TX bytes:6441 (6.2 KiB)

ra0       Link encap:Ethernet  HWaddr 00:08:A1:69:71:A9
          inet addr:192.168.0.166  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::208:a1ff:fe69:71a9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:210 errors:0 dropped:0 overruns:0 frame:0
          TX packets:362 errors:106 dropped:106 overruns:0 carrier:0
          collisions:108 txqueuelen:1000
          RX bytes:74540 (72.7 KiB)  TX bytes:58073 (56.7 KiB)
          Interrupt:177 Base address:0x4000

it seems that when i checked the settings this time round i was getting my access point. But there still was to the net.

---

### Post by cantormath on 2006-07-31
what does it say when you type
sudo dhclient

does it renew your IP.  and if it does, do you have access to the net.

it looks like you are getting an ip address.

---

### Post by gn2 on 2006-07-31
-

---

### Post by gn2 on 2006-07-31
Had similar problems myself recently with D-Link DWL650+
Eventual cure was to set-up networking during Ubuntu install.
Had decided to skip this first time round installing, selected the set-up later option then spent hours googling for a cure when it didn't work. 
Tried all suggestions. No joy.
Decided to re-install.
Second time network set-up failed during install even after giving the correct SSID and WEP key.
Being a persistent type I had another go, this time the network set-up correctly then the install continued.
Once install completed Wireless was working correctly internet was accessible, and I have to say the hassle was worth it Ubuntu is ace.
My desktop is getting the (dual-boot) treatment next, (wife refuses to try new OS and office apps)

As in fishing, skill is when it works, luck is when it won't.

---

### Post by mwanafunzi on 2006-08-01
here are y dhclient results...

Listening on LPF/eth0/00:40:f4:7a:66:f2
Sending on   LPF/eth0/00:40:f4:7a:66:f2
Listening on LPF/ra0/00:08:a1:69:71:a9
Sending on   LPF/ra0/00:08:a1:69:71:a9
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I still had no access to the net after doing this.

---

### Post by mwanafunzi on 2006-08-01
I have decided to try and install ndiswrapper from source. I am having a slight problem cause I do not understand what 

Prerequisites 
=============

You need a recent kernel, at least 2.6.6 or 2.4.26, with header filesfor the kernel. Make sure there is a link to the kernel source fromthe modules directory. The command

  > ls /lib/modules/`uname -r`/build

should have at least 'include' directory and '.config' file.

When I type in that command I get 

> kitabu@floonie:/lib/modules/2.6.15-26-386$ ls /lib/modules/`uname -r` /build
ls: /build: No such file or directory
/lib/modules/2.6.15-26-386:
initrd      modules.alias        modules.inputmap   modules.seriomap
kernel      modules.ccwmap       modules.isapnpmap  modules.symbols
madwifi     modules.dep          modules.ofmap      modules.usbmap
madwifi-ng  modules.ieee1394map  modules.pcimap     volatile

I am not sure if i should create the build directory or if it should already be there. 

When I then 'make uninstall' and 'make' I get the following errors -

make uninstall
> NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /lib/modules/2.6.15-26-386/kernel/drivers/net/ndiswrapper
/bin/rm: cannot remove `/lib/modules/2.6.15-26-386/kernel/drivers/net/ndiswrapper': Permission denied
make: *** [uninstall] Error 1

make
> make -C driver
make[1]: Entering directory `/home/kitabu/Desktop/ndiswrapper-1.21/driver'
Can't find kernel build files in /lib/modules/2.6.15-26-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/kitabu/Desktop/ndiswrapper-1.21/driver'
make: *** [all] Error 2

Any advice

---

### Post by cantormath on 2006-08-01
Have you tried setting up the card through the gui, via clicking on 
System>Administration>Networking

activate the card, deactivate the eth0 card, unless you are using it.

Click on the wireless card and click configure.
set the configurations to dhcp.
see if you can select the network you want to connect to.
Also,
make sure that if you have security on the router, ie wep or mac filtering, that you either turn it off the security or add the mac address if you are filtering.

you may also want to try wifi-radar, its a pretty good wifi gui (add universe repo).
and you should have network manager installed from the Applications>Add/remove.

from you iwconfig/ifconfig, it seems that you card is being picked up.  I generally dont use Ndiswrapper unless there is abolutely no choice.

lastly, make sure that if you are connected to the net through lan, that you have done the updates.

---

