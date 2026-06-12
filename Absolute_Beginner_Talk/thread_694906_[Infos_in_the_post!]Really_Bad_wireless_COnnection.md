---
title: "[Infos in the post!]Really Bad wireless COnnection!!! Drops and never reconnect!!!"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by pinkkiss110 on 2008-02-12
I realize that there is many other post that resembles my prob but none has the solution...

_Basically my wireless connection goes dead_, and the wicd still thinks that I am connected.
Can NEVER Reconnection! I have to replug usb, or restart!!!

I is really frustrating!! (Sorry for my complaining tone)
I post all the infos from my last post, Hopefully something good turns up this time!!

[COLOR="Indigo"]================================================[/COLOR]

_[COLOR="Red"]lspci[/COLOR]_
> 00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 430 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 Communication controller: Conexant HSF 56k Data/Fax Modem
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 430 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 Communication controller: Conexant HSF 56k Data/Fax Modem

_[COLOR="Red"]sudo lshw -C network[/COLOR]_
>   *-network               
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1c:10:6c:df:d5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.101 multicast=yes wireless=IEEE 802.11g


[COLOR="Red"]_iwconfig_[/COLOR]
> lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"XiaoWang"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:16:B6:3B:FD:E0   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"XiaoWang"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:16:B6:3B:FD:E0   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


[COLOR="Red"]_susudo iwlist scan_[/COLOR]
> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:16:B6:3B:FD:E0
                    ESSID:"XiaoWang"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz
                    Signal level=-64 dBm  
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (2) : TKIP WEP-40
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (2) : TKIP WEP-40
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000b91d804c7c


---

### Post by Het Irv on 2008-02-12
Do you know where on the line the connection is being dropped? (e.g. access point, modem, USB, Computer.)

---

### Post by gimfred on 2008-02-14
I've had the problem pinkkiss110 is talking about. Basically sometimes it seems to be my computer, sometimes it seems to be the AP and others it seems to be the dsl modem. What happens is you will be on the internet and one page will take for ever to load. 

So you ifconfig. all the cards and ip's are still there, so you ping the modem (ip 192.168.1.1) Can't find it. Ping the AP; yep that is there. You log into the AP, (ip 192.168.1.4) yep, that is working. Then you make the AP ping .1 !!! It is there! So you try google. no go. so you faithfully reset ( x amount of times.) and eventually it will start working again. In the mean time you have checked that you haven't lost your gateway and dns server info. no it is still there... just dropped out. It looks like it is the AP or the modem losing connection, but it is the computer you have to reset. (ifconfig ath0 down, then up.) But the dns and gateway info is still all there! 

So how do we check which is dying? Ping all three continuously? heck I'm going to try it just for the sake of it!.

---

### Post by gimfred on 2008-02-14
Okay. just did the ping test, that is I pinged 192.168.1.8 (computer) 192.168.1.4 (AP) and 192.168.1.23 (modem), each in their own terminal. Went along quite nicely till the modem stopped responding. route displays:```
~$ route
Kernel IP routing table
Destination        Gateway         Genmask           Flags Metric Ref    Use     Iface
zandergraph.loc     *               255.255.255.255  UH     0      0        0        ath0
192.168.1.0           *               255.255.255.0      U      0      0        0         ath0
default            192.168.1.23    0.0.0.0                UG     0      0        0        ath0
```
ifconfig displays: ```
~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:11:95:C3:0D:7D
          inet addr:192.168.1.8  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::211:95ff:fec3:d7d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:126312 errors:0 dropped:0 overruns:0 frame:0
          TX packets:94294 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:153408940 (146.3 MB)  TX bytes:8990688 (8.5 MB)

ath0:0    Link encap:Ethernet  HWaddr 00:11:95:C3:0D:7D
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:16:17:BD:22:A1
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:23 Base address:0xf800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5432 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5432 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:473616 (462.5 KB)  TX bytes:473616 (462.5 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-11-95-C3-0D-7D-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:365472 errors:0 dropped:0 overruns:0 frame:88161
          TX packets:96488 errors:44 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199
          RX bytes:189885689 (181.0 MB)  TX bytes:11172445 (10.6 MB)
          Interrupt:18

```(I don't know what the ath0:0 is about, but the problem has been the same longer than ath0:0 has been there. I got it when I installed wicd. It used to be just ath0)

lshw 
```
*-network
       description: Wireless interface
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications, Inc.
       physical id: 5
       bus info: pci@0000:05:05.0
       logical name: wifi0
       version: 01
       serial: 00:11:95:c3:0d:7d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.1.8 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g

```


hmmm... this is making a liar out of me. I had to reboot the AP....

---

### Post by Het Irv on 2008-02-14
What kind of equipment are you using.  I have had this problem before with my Linksys wireless router and the best way I have found to fix it is to unplug everything...wait...wait some more. Then plug the modem back in, once it comes up fully, plug the AP back up, let it come up fully, then turn the computer back on.  My problem doesn't happen very often though, so this might be to much of a hassel.

---

### Post by gimfred on 2008-02-14
I personally am using a DI-624 wireless router. Since I last posted, rebooting via their webadmin controls seems to work reliably. It seems to be somewhat random length of time and that doesn't exceed 4 hours personally.

Pinkkiss110. Can you log into the AP or modem? Normally they are 192.168.1.1 or 192.168.0.1 though that can be changed fairly easily. Reboot then ping your AP. Works every time now for me, and means a drop out of 10 - 20 seconds.

I'll have to get onto DLink to see if they have a patch for this.

---

### Post by gimfred on 2008-02-18
Can someone confirm whether the workaround is only for myself, only for Dlink, or is it universal to Atheros AR5212/5213 chipsets? I can't rag out Dlink unless I at least have several anecdotes.

---

