---
title: "eth problem"
date: 2013-03-24
forum: Asus Ubuntu Support (CLOSED)
---

### Post by nfkengineer on 2013-03-24
hello  my brothers,

I am new on ubuntu. I install ubuntu to my asus laptop.
But there are no eth stuff :(

here some outs,

root@bt:~# ifconfig eth0
eth0: error fetching interface information: Device not found
  
it is the same when &#305; use ifconfig -a

root@bt:~# dmesg | grep eth
[    0.644406] i2c-core: driver [aat2870] using legacy suspend method
[    0.644409] i2c-core: driver [aat2870] using legacy resume method
[   16.598602] Loading kernel module for a network device with CAP_SYS_MODULE (deprecated).  Use CAP_NET_ADMIN and alias netdev-eth0 instead
[   16.960213] Loading kernel module for a network device with CAP_SYS_MODULE (deprecated).  Use CAP_NET_ADMIN and alias netdev-eth0 instead



I did "[COLOR=#000000][FONT=courier new]sudo start-network[/FONT][/COLOR]" but it does not work.


PLEAASSSEEEEE HELP ME , I AM GETTING CRAZY :)

---

### Post by schragge on 2013-03-24
Please post the output of *lspci -nn*

---

### Post by nfkengineer on 2013-03-24
here [COLOR=#000000]output of [/COLOR][I]lspci -nn
[/I]root@bt:~# lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
00:14.0 USB Controller [0c03]: Intel Corporation Panther Point USB xHCI Host Controller [8086:1e31] (rev 04)
00:16.0 Communication controller [0780]: Intel Corporation Panther Point MEI Controller #1 [8086:1e3a] (rev 04)
00:1a.0 USB Controller [0c03]: Intel Corporation Panther Point USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation Panther Point High Definition Audio Controller [8086:1e20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 1 [8086:1e10] (rev c4)
00:1c.1 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 2 [8086:1e12] (rev c4)
00:1c.3 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 4 [8086:1e16] (rev c4)
00:1d.0 USB Controller [0c03]: Intel Corporation Panther Point USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation Panther Point LPC Controller [8086:1e59] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation Panther Point 6 port SATA AHCI Controller [8086:1e03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation Panther Point SMBus Controller [8086:1e22] (rev 04)
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)
03:00.0 Ethernet controller [0200]: Atheros Communications Device [1969:1091] (rev 10)
root@bt:~#

---

### Post by schragge on 2013-03-24
Have a look at [post=12018542]this post[/post].

---

### Post by nfkengineer on 2013-03-24
i downloaded driver from "[COLOR=#000000]Have a look at [/COLOR][this post]("http://ubuntuforums.org/showthread.php?p=12018542#post12018542")[COLOR=#000000].[/COLOR]"

then &#305; did ;

root@bt:~/Desktop# sudo tar compat-drivers-2013-03-04-u.tar.bz2
tar: You may not specify more than one `-Acdtrux' option
Try `tar --help' or `tar --usage' for more information.
how can &#305; install driver ?

---

### Post by nfkengineer on 2013-03-24
root@bt:~/Desktop# sudo tar** jxpf** compat-drivers-2013-03-04-u.tar.bz2 
root@bt:~/Desktop#make
root@bt:~/Desktop#make install
root@bt:~/Desktop#reboot

---

### Post by nfkengineer on 2013-03-24
[B][COLOR=#000000]
[/COLOR][/B][COLOR=#000000]thank you so much [SIZE=4][B]schragge  

it woks :)
[/B][/SIZE][/COLOR]root@bt:~# ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 50:46:5d:2e:f2:b8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 


[COLOR=#000000][SIZE=4][/SIZE][/COLOR][COLOR=#000000][/COLOR]

---

