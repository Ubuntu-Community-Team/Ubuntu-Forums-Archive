---
title: "Madwifi-hal macbook"
date: 2007-05-30
forum: Apple Intel Users
---

### Post by omax on 2007-05-30
Hi everyone. New to this forum...

I got my macbook a week ago and instantly installed Xubuntu.

Then I got my wlan to work with madwifi-hal.


After I crashed some things I had to reinstall Xubuntu.

Now I can't get madwifi to work.

I installed it and I get ouput on:
iwlist ath0 scan

I can connect to my network and in my routers interface it says that I'm connected but no IP is asigned.

I configured ath0 to use dhcp.


But I only get and IPv6-address which my router does not support.

dmesg:
ATH0: No IPv6 routers available

Any fix? And why doesnt it work since I updated my kernel?

Using 2.6.20-16-generic

---

### Post by ronocdh on 2007-05-30
Thanks for the info. Please post your exact wireless chipset, though. Use **sudo update-pciids** and then **lspci** and look near the bottom.

Are you sure you're using the same version of madwifi as you originally did? It updates very, very often and support often fluctuates depending on the version number. Widemos [put up a how-to]("http://ubuntuforums.org/showthread.php?t=429641&highlight=widemos+ndiswrapper") a while back for madwifi. It's a little old now, but hopefully it will at least point you in the right direction. Hope this helps.

---

### Post by omax on 2007-05-31
Here is some output...

```
$lspci -v:

02:00.0 Network controller: Atheros Communications, Inc. AR5418 802.11a/b/g/n Wireless PCI Express Adapter (rev 01)
        Subsystem: Apple Computer Inc. Unknown device 0087
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at 50100000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

```

```
$sudo iwconfig ath0:

ath0      IEEE 802.11g  ESSID:"My ESSID"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:17:9A:46:90:03   
          Bit Rate:36 Mb/s   Tx-Power:14 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:6361-6C76-BLABLA-MY-KEY-CENSORED   Security mode:restricted
          Power Management:off
          Link Quality=30/94  Signal level=-66 dBm  Noise level=-96 dBm
          Rx invalid nwid:2288  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
$sudo ifconfig ath0:

ath0      Link encap:Ethernet  HWaddr 00:19:E3:D6:E0:B2  
          inet6 addr: fe80::219:e3ff:fed6:e0b2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:172 errors:0 dropped:0 overruns:0 frame:0
          TX packets:107 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7434 (7.2 KiB)  TX bytes:15728 (15.3 KiB)

```

```
$sudo iwlist ath0 scan:

ath0      Scan completed :
          Cell 01 - Address: 00:17:9A:46:90:03
                    ESSID:"My ESSID"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/94  Signal level=-66 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f202010100000364000027a4000041435e0061322f00

```

As you see it works until it wants an IP. It requests for an IPv6-address when I want an IPv4

---

