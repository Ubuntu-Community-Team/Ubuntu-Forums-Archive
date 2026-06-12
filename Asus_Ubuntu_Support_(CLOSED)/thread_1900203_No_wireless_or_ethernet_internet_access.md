---
title: "No wireless or ethernet internet access"
date: 2011-12-25
forum: Asus Ubuntu Support (CLOSED)
---

### Post by mogsmar5 on 2011-12-25
Hi all,

I recently installed Ubuntu on my ASUS K53TA laptop Ubuntu is installed in its own partition, with Win7 on another. Since the Oneiric disk wouldn't work I used my old Hardy disk and planned to upgrade via update manager.

Unfortunately, the resulting setup has absolutely no internet access - there are no wireless networks listed, and plugging in an ethernet cable has no effect (it works fine on my other laptop, and wifi is working in Win7).

I've looked about a bit on Google and followed various instructions. I've booted into windows and got my IP address and default gateway and copied them into the 'Manual configuration > wireless connections > static IP' dialogue box. No idea whether this was supposed to work or not, but it didn't. I've also turned of ipv6. I've also installed a windows driver installer, but I can't find the wireless driver for an ASUS K53TA anywhere on the internet. The online documentation is very unhelpful. I downloaded a couple of drivers that may or may not be for my laptop and installed them, but it's still not working.

Could someone please help!

---

### Post by drdos2006 on 2011-12-25
What do you get when you type "ifconfig" ?
Can you ping your gateway/router ?

regards

---

### Post by mogsmar5 on 2011-12-25
ifconfig gives:


eth0      Link encap:Ethernet  HWaddr 14:da:e9:9f:9a:57  
          inet addr:192.168.1.142  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:219 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1492 (1.4 KB)  TX bytes:1492 (1.4 KB)


I doubt I could ping my router - there are no networks available so I don't think my computer's aware there is one.

---

### Post by benpack101 on 2011-12-25
Try following these directions in the terminal to connect.

[http://www.youtube.com/watch?v=KIK48qHA_RaY](http://www.youtube.com/watch?v=KIK48qHA_RaY)

---

### Post by drdos2006 on 2011-12-25
Well you are getting an IP from somewhere.....

eth0 Link encap:Ethernet HWaddr 14:da:e9:9f:9a:57
inet addr:192.168.1.142 Bcast:192.168.1.255 Mask:255.255.255.0
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:219 Base address:0xa000

Am assuming an ethernet cable is connected to you machine.
Go back to receiving a DHCP address from Network Manager settings.
Run "ifconfig" again.
What is the IP address of your router ? 
Can you "ping IP-address-of-router" ?

regards

---

### Post by mogsmar5 on 2011-12-26
Ah I think the IP was artificial - I'd entered the IP of my windows system under 'Manual Configuration > static IP'. I've set 'Manual configuration' back to its default setting of 'Roaming Enabled' and now get this output from ifconfig:


eth0      Link encap:Ethernet  HWaddr 14:da:e9:9f:9a:57  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4212 (4.1 KB)  TX bytes:4212 (4.1 KB)

Here is the output from lspci:


00:00.0 Host bridge: Advanced Micro Devices [AMD] Unknown device 1705
00:01.0 VGA compatible controller: ATI Technologies Inc Unknown device 9648
00:01.1 Audio device: ATI Technologies Inc Unknown device 1714
00:02.0 PCI bridge: Advanced Micro Devices [AMD] Unknown device 1707
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Unknown device 1709
00:05.0 PCI bridge: Advanced Micro Devices [AMD] Unknown device 170a
00:10.0 USB Controller: Advanced Micro Devices [AMD] Unknown device 7812 (rev 03)
00:11.0 SATA controller: Advanced Micro Devices [AMD] Unknown device 7801 (rev 40)
00:12.0 USB Controller: Advanced Micro Devices [AMD] Unknown device 7807 (rev 11)
00:12.2 USB Controller: Advanced Micro Devices [AMD] Unknown device 7808 (rev 11)
00:14.0 SMBus: Advanced Micro Devices [AMD] Unknown device 780b (rev 13)
00:14.2 Audio device: Advanced Micro Devices [AMD] Unknown device 780d (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] Unknown device 780e (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] Unknown device 780f (rev 40)
00:14.7 SD Host controller: Advanced Micro Devices [AMD] Unknown device 7806
00:18.0 Host bridge: Advanced Micro Devices [AMD] Unknown device 1700 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Unknown device 1701
00:18.2 Host bridge: Advanced Micro Devices [AMD] Unknown device 1702
00:18.3 Host bridge: Advanced Micro Devices [AMD] Unknown device 1703
00:18.4 Host bridge: Advanced Micro Devices [AMD] Unknown device 1704
00:18.5 Host bridge: Advanced Micro Devices [AMD] Unknown device 1718
00:18.6 Host bridge: Advanced Micro Devices [AMD] Unknown device 1716
00:18.7 Host bridge: Advanced Micro Devices [AMD] Unknown device 1719
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 6741
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
03:00.0 Network controller: Atheros Communications Inc. Unknown device 002b (rev 01)

Here is the output from sudo lshw -C network:

*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: 14:da:e9:9f:9a:57
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0


Here is the output from nm-tool:

NetworkManager Tool

State: connected

- Device: eth0 ----------------------------------------------------------------
  NM Path:           /org/freedesktop/NetworkManager/Devices/eth0
  Type:              Wired
  Driver:            r8169
  Active:            no
  HW Address:        14:DA:E9:9F:9A:57

  Capabilities:
    Supported:       yes
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Settings
    Hardware Link:   no

---

### Post by drdos2006 on 2011-12-27
Looks like you are receiving IPv6 IP address and not an IPv4 IP ddress.
Disabling IPv6 and enabling IPv4 might fix the problem.

From the terminal:
cat /proc/sys/net/ipv6/conf/*/disable_ipv6
They should all be 1.

Disabling IPV6 is best done via sysctl. Need to add extra commands to /etc/sysctl.conf

First copy sysctl.conf to a backup with :
sudo cp /etc/sysctl.conf   /etc/sysctl.conf.backup

Next type :
sudo gedit /etc/sysctl.conf
Highlight the commands below from your browser, edit, copy.

# Disable IPV6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

Add the commands to the bottom of /etc/sysctl.conf, save and reboot.

From a terminal type : ifconfig
ifconfig should not mention an IPV6 address on any interface after you have rebooted and you should now have IPv4 address for your computer.

regards

---

### Post by mogsmar5 on 2011-12-27
> **drdos2006 said:**
> Looks like you are receiving IPv6 IP address and not an IPv4 IP ddress.
Disabling IPv6 and enabling IPv4 might fix the problem.

From the terminal:
cat /proc/sys/net/ipv6/conf/*/disable_ipv6
They should all be 1.

Disabling IPV6 is best done via sysctl. Need to add extra commands to /etc/sysctl.conf

First copy sysctl.conf to a backup with :
sudo cp /etc/sysctl.conf   /etc/sysctl.conf.backup

Next type :
sudo gedit /etc/sysctl.conf
Highlight the commands below from your browser, edit, copy.

# Disable IPV6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

Add the commands to the bottom of /etc/sysctl.conf, save and reboot.

From a terminal type : ifconfig
ifconfig should not mention an IPV6 address on any interface after you have rebooted and you should now have IPv4 address for your computer.

regards

Thanks very much for such detailed help. I've run all the commands except the first, since it seems I have no ipv6 directory, only a ipv4 one, so it wouldn't run. Unfortunately nothing seems to have changed! Here's the output of ifconfig:


eth0      Link encap:Ethernet  HWaddr 14:da:e9:9f:9a:57  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:593 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:47389 (46.2 KB)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:106 errors:0 dropped:0 overruns:0 frame:0
          TX packets:106 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5548 (5.4 KB)  TX bytes:5548 (5.4 KB)

Thanks for your help.

---

### Post by drdos2006 on 2011-12-27
When you run the first command, what do you get ?
Can you ping your router IP gateway address ?

regards

---

### Post by mogsmar5 on 2011-12-27
I get no such file or directory (I've checked, there isn't). Perhaps this is because I'm running Hardy Heron? (Only had an old disk, planned to update when internet was running)

Well it runs through the ping command, but gets no response from each port it tries.

---

### Post by drdos2006 on 2011-12-27
From your toolbar, go to :
System -> Preferences -> Network Connections -> Wired -> Auto eth0 -> Edit -> IPv4 Settings. Make sure you have Automatic DHCP selected.
Go to IPv6 settings. Make sure you have Ignore selected.

Try a new ethernet cable to your router. Is your router set up to supply DHCP to your machines ?


From the terminal type :
ifconfig

Is there any change ?

regards

---

### Post by sandy8925 on 2012-04-23
i have the same laptop.

hardy heron is ooooooooolllllllllllldddddddd............

try installing precise pangolin when it releases. oneiric won't work out of the box because there was a bug in linux kernel 3.0 where the graphics card doesn't display stuff (screen is blank - the backlight is switched off). this was fixed in kernel 3.2 though and was backported into 3.0.somenumber so if you get the latest updates then everything should work fine.

---

### Post by jblock312 on 2012-04-24
shot in the dark here...
I tried installing 10.10 and 11.04 on my Asus 1001pxd with windows 7. Hardly the same computer as yours, but had the same problem with no lan access.
Just installed Mint 11 on it from a dvd, and both ethernet and wireless work.

---

### Post by twodogs on 2012-04-25
I have asus u53e and had no internet too. I installed 11.10 and did this and it now works great!
Follow the link and read my answer. _Dave

 [http://askubuntu.com/questions/104651/cant-get-into-wifi-on-my-asus-notebook-u56e/114585#114585](http://askubuntu.com/questions/104651/cant-get-into-wifi-on-my-asus-notebook-u56e/114585#114585)

---

