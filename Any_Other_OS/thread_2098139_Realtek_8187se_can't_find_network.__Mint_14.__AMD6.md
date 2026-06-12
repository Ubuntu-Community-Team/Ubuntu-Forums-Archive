---
title: "Realtek 8187se can't find network.  Mint 14.  AMD64."
date: 2012-12-25
forum: Any Other OS
---

### Post by CityNight on 2012-12-25
(I'm posting in a Ubuntu forum because A) Before I switched to Mint, my Ubuntu 10.12 had the same problem.  B)  The systems are so similar -- one derived from the other -- that the solution for one should work for the other.  C) Ubuntu forums are the only ones on which I've found usable advice.  You guys have the better support, and I believe the system diff will not affect anything.  D) I plan to switch back to Ubuntu when and if they lose Unity Desktop).

Hello.  I'm a bit new at Linux, and after installing Mint 14 on my laptop, I am unable to use the wireless.  I have gone through every forum I could find; each of their answers revealed a problem I had not noticed, and helped me to correct it:  Network Manager had kept my WiFi Disabled, the correct module (rtl8187se) was not present (similarly-named and useless ones took its place), and ndiswrapper was faulty, as were its updates and patches.  And so here I am.  My problem at the moment is my card's inability to detect wifi networks.  All the drivers seem to be in working order, the card functions in Windows 7 (which I dual-boot), and currently picks up three high-strength networks nearby.  In Linux, the card is recognized, Wifi is "On", Airplane mode "Off", but recieves nothing.  I've tried to be as thourough as possible, listing everything that might be important.  Anything you guys could do would be greatly appreciated. Thanks!  (The Fn-F8 key combo is marked on my keyboard, but does nothing, even in Windows).

Toshiba Sattelite L455D-S5976 laptop
AMD64
Linux Mint 14 Nadia with Cinnamon
Card:  Realtek RTL8187se
Network Manager: WICD Network Manager, latest version.  (Replaced original Network Manager)
Drivers:  Windows XP 64-bit, downloaded from Realtek, operated via ndiswrapper 1.57; ndis originally proved faulty, attepted to follow repair instructions, all seems well (no errors on install of drivers/ compilation of ndis).

```
computer@computer ~ $ modprobe rtl8187se
FATAL: Module rtl8187se not found.
```(I assume this module is no longer necessary).

```
computer@computer ~ $ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Toshiba America Info Systems Device 9602
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS780MC [Mobility Radeon HD 3100 Graphics]
0e:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)
``````
computer@computer ~ $ lsusb
Bus 001 Device 002: ID 0baf:0303 U.S. Robotics 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
``````
computer@computer ~ $ lspci -nn | grep Realtek
0e:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller [10ec:8199] (rev 22)
``````
computer@computer ~ $ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:72.251.108.60  P-t-P:64.58.38.178  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:394 (394.0 B)  TX bytes:250 (250.0 B)

wlan0     Link encap:Ethernet  HWaddr e8:39:df:3d:3c:f7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Memory:f0300000-f0304000 
``````
computer@computer ~ $ iwconfig
ppp0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

``````
computer@computer ~ $ lsmod
Module                  Size  Used by
ppp_deflate            12950  1 
zlib_deflate           26914  1 ppp_deflate
bsd_comp               12921  0 
ppp_async              17413  1 
crc_ccitt              12667  1 ppp_async
cdc_acm                26935  3 
nls_utf8               12557  1 
udf                    89482  1 
crc_itu_t              12707  1 udf
dm_crypt               23011  1 
ip6t_REJECT            12574  1 
xt_hl                  12521  6 
ip6t_rt                12558  3 
nf_conntrack_ipv6      14054  7 
nf_defrag_ipv6         13158  1 nf_conntrack_ipv6
ipt_REJECT             12541  1 
xt_LOG                 17349  10 
xt_limit               12711  13 
xt_tcpudp              12603  18 
xt_addrtype            12635  4 
xt_state               12578  14 
joydev                 17457  0 
ip6table_filter        12815  1 
ip6_tables             27207  2 ip6t_rt,ip6table_filter
snd_hda_codec_realtek    77876  1 
nf_conntrack_netbios_ns    12665  0 
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
nf_nat_ftp             12649  0 
nf_nat                 25254  1 nf_nat_ftp
nf_conntrack_ipv4      14480  9 nf_nat
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
nf_conntrack_ftp       13359  1 nf_nat_ftp
nf_conntrack           82633  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12810  1 
ip_tables              26995  1 iptable_filter
x_tables               29711  13 ip6t_REJECT,xt_hl,ip6t_rt,ipt_REJECT,xt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
snd_hda_intel          33491  3 
snd_hda_codec         134212  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30512  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
microcode              22803  0 
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78734  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                95552  0 
soundcore              15047  1 snd
sp5100_tco             13697  0 
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
serio_raw              13215  0 
k10temp                13126  0 
i2c_piix4              13167  0 
ndiswrapper           283279  0 
toshiba_acpi           18726  0 
shpchp                 37108  0 
sparse_keymap          13890  1 toshiba_acpi
wmi                    19070  1 toshiba_acpi
rfcomm                 46619  0 
parport_pc             32688  0 
bnep                   18140  2 
ppdev                  17073  0 
bluetooth             209199  10 rfcomm,bnep
mac_hid                13205  0 
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
radeon                895653  3 
ttm                    83595  1 radeon
drm_kms_helper         46784  1 radeon
pata_atiixp            13204  0 
drm                   275528  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13413  1 radeon
video                  19335  0 
``````
computer@computer ~ $ sudo lshw -C network
[sudo] password for computer: 
  *-network               
       description: Wireless interface
       product: RTL8187SE Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: wlan0
       version: 22
       serial: e8:39:df:3d:3c:f7
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8187se driverversion=1.58rc1+Realtek Semiconductor Co latency=0 link=no multicast=yes wireless=IEEE 802.11g
       resources: irq:18 ioport:a000(size=256) memory:f0300000-f0303fff
``````
computer@computer ~ $ iwlist scan
ppp0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     No scan results

computer@computer ~ $ iwlist wlan0 scan
wlan0     No scan results

computer@computer ~ $ uname -mr
3.5.0-17-generic x86_64
``````
computer@computer ~ $ sudo /etc/init.d/networking restart
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service networking restart
Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) and then start(8) utilities,
e.g. stop networking ; start networking. The restart(8) utility is also available.
networking stop/waiting
networking start/running
``````
computer@computer ~ $ sudo service wicd restart
[sudo] password for computer: 
 * Restarting Network connection manager wicd                    [ OK ]
``````
computer@computer ~ $ dhcpcd wlan0
The program 'dhcpcd' can be found in the following packages:
 * dhcpcd
 * dhcpcd5
Try: sudo apt-get install <selected package>
```

---

### Post by CityNight on 2012-12-25
I used to have Ubuntu, and can find no difference besides desktop.
A new bit of text to chew on.  The server query at the bottom confused me until I realized my dialup is plugged in. :)  I'm also concerned about the lack of results from "* V. querying DHCP..."  Other people's always show something or other...

```
computer@computer ~ $ mintwifi
-------------------------
* I. scanning WIFI PCI devices...
  -- Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)
      ==> PCI ID = 10ec:8199 (rev 22)
-------------------------
* II. querying ndiswrapper...
net8187se : driver installed
    device (10EC:8199) present (alternate driver: r8187se)
-------------------------
* III. querying iwconfig...
ppp0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

-------------------------
* IV. querying ifconfig...
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 B)  TX bytes:200 (200.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:72.251.108.110  P-t-P:64.58.38.178  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:19038 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22716 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:10299286 (10.2 MB)  TX bytes:3990380 (3.9 MB)

wlan0     Link encap:Ethernet  HWaddr e8:39:df:3d:3c:f7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Memory:f0300000-f0304000 

-------------------------
* V. querying DHCP...
-------------------------
* VI. querying nslookup google.com...
Server:        64.136.173.5
Address:    64.136.173.5#53

Non-authoritative answer:
Name:    google.com
Address: 173.194.75.139
Name:    google.com
Address: 173.194.75.100
Name:    google.com
Address: 173.194.75.138
Name:    google.com
Address: 173.194.75.113
Name:    google.com
Address: 173.194.75.101
Name:    google.com
Address: 173.194.75.102

```I have also blacklisted the following modules (the first two to keep them from interfering with the new drivers, the last four on an explanation from a Mint user that, against all logic, blacklisting them cleared up his problem):

/etc/modprobe.d/blacklist.conf       (varies with system)

```
#This allegedly interferes with Realtek windows drivers.
blacklist rtl8187
blacklist r8187se
blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist ssb
```

I just discovered this as well:
```
computer@computer ~ $ sudo modprobe net8187se
[sudo] password for computer: 
FATAL: Module net8187se not found.

```

Should I be worried, or is the driver not implemented by ndiswrapper as a module?  Compare to:

```
* II. querying ndiswrapper...
net8187se : driver installed
    device (10EC:8199) present (alternate driver: r8187se)
```
under mintwifi

---

### Post by CityNight on 2012-12-25
A note on WCID's behavior (my reference to "Airplane Mode" in my first post was from the original, default Network Manager): The "Switch Off WiFi" button is clickable, but does not change when clicked.  I cannot find any evidence that it is functional.  Secondly, the "Refresh" button is seemingly functional, and the program gives every indication of actively searching for a network, even though none appear where there should be several.  I can't shake the feeling that the drivers are wrong, or the configuration is wrong.  To repeat myself, I'm a newbie, so I have no way but you folks to confirm my hunch, but I don't think it's the card or the manager, but what's inbetween.  Miss?  I only wish I'd posted all this before Christmas... ](*,)

Another note, before anyone asks me to download some monstrous patch:  most days my connection is 56kbits/s dialup.  Can only get WiFi in Windows, at the public library.

Thank you all in advance.  Merry Christmas, and a happy New Year!

---

### Post by Bakuda on 2012-12-26
im using ubuntu 10.04 on my asus leptap. and i have a airties modem. but unfortunately i can not access to internet via my wireless modem. i think there is a problem about dhcp. because when dhcp auto mode i cant connect to my modem neither. although when i sellect dhcp manuel and give my leptop a spesific ip it connects to modem. i can adjust modem settings with leptap but there is still no internet connection. in shortly i connect my modem but not internet. what should i do?

---

### Post by kurt18947 on 2012-12-26
Major bummer!  RealTek doesn't list a linux driver for the 8187SE chip, only a Windows driver.  Try emailing RealTek and see if another package will support your adapter?  Maybe go to your blacklist file and remove the 8187SE module, leaving the others?  Reboot and see what happens?   If you can't convince NDISwrapper to work, I'm not sure what else to try except to buy an adapter known to work.  I've had very good luck with the Edimax  ew-7811Un using Realtek's driver.  It's pretty tiny and unobtrusive.  The native driver in Ubuntu finds the device but is unreliable.

[http://www.amazon.com/Edimax-EW-7811Un-Wireless-Adapter-Wizard/dp/B005CLMJLU](http://www.amazon.com/Edimax-EW-7811Un-Wireless-Adapter-Wizard/dp/B005CLMJLU)

Edit:  I doubt the native driver has any chance of success while NDISwrapper is installed so maybe remove NDISwrapper and its associated windows stuff before removing rtl8187se from the blacklist?  That Realtek doesn't offer a linux driver for that chipset doesn't bode well IMO unless another rtl8187 driver will drive that device.

---

### Post by CityNight on 2012-12-26
That's the thing:  the current drivers, from what I have read, are  incorrect.  There are three altogether:  rtl8187, r8187se, and  rtl8187se.  The last one is not present, and apparently the other two do  not run.  The last is one of those things that you hear about but never  find a link to, and is the correct one.  If I could only find where to  download it, I would uninstall ndis, which I've heard bad things  about.   I have emailed Realtek, and wait on a response.  Would you  happen to know where I could find that driver?

P.S. As to buying a new adapter, money is an issue.  If I had a better income, I would've saved up for a Linux laptop long ago.  So much less trouble.  :neutral:

---

### Post by kurt18947 on 2012-12-27
> **CityNight said:**
> That's the thing:  the current drivers, from what I have read, are  incorrect.  There are three altogether:  rtl8187, r8187se, and  rtl8187se.  The last one is not present, and apparently the other two do  not run.  The last is one of those things that you hear about but never  find a link to, and is the correct one.  If I could only find where to  download it, I would uninstall ndis, which I've heard bad things  about.   I have emailed Realtek, and wait on a response.  Would you  happen to know where I could find that driver?

P.S. As to buying a new adapter, money is an issue.  If I had a better income, I would've saved up for a Linux laptop long ago.  So much less trouble.  :neutral:

Yes, I checked RealTek's site for that chip.  The only thing I saw was for Windows.  It's possible that another chip's driver will drive the 8187SE.  For instance, I installed the RealTek driver for the Edimax 8188CUs device and blacklisted the native rtl modules.  It appears out that the module r8712u for the Edimax 8188CUs device will also drive the Realtek 8192SU device (Dlink DWA-131).  It's possible that another Realtek 8187xx driver will work with your 8187SE device but I  have no idea if or which one.  It will be interesting to hear what Realtek has to say.   I've followed a couple threads about devices that require NDISwrapper.  I gather that the current version has 'issues', it's necessary to build from source.  But I'm certainly no expert on NDISwrapper related things.

I appreciate what you're saying about $$.  I don't know where you are but Amazon in the U.S. has the Edimax ew-7811Un for $9.99 with free shipping.

---

### Post by dwb814 on 2012-12-27
Hi guys,
Possible solution to your RTL8187se issue here:

[http://askubuntu.com/questions/214085/need-a-few-reboots-to-connect-to-wireless](http://askubuntu.com/questions/214085/need-a-few-reboots-to-connect-to-wireless) 

Start reading at the second post titled "**Overview**"

Hope that helps you out!

---

### Post by CityNight on 2013-02-14
Hey, guys.  The driver problem no longer affects me, as I received both a high-powered long-distance WiFi adapter and a new laptop for Christmas.  :guitar: \\:D/ :lolflag: Also, it seems that this problem has come to the attention of many other people, so fixing up the old one is now only a matter of searching.  Thanks for all your help... life is good.  Oh, and I never did get a response from Realtek...

---

