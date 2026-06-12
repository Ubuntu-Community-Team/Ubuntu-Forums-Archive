---
title: "Intel Wireless 2200 BG without alternative internet connection"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by apradhan on 2007-05-19
Hi !

Im a new ubuntu user. I currently dual boot Ubuntu 6.10 and Win XP sp 2.  I have wireless internet at home and I cant access it using ubuntu. 

A lot of the instrutctions ive read about setting up the wireless on ubuntu assume pre-existence of an alternative internet connection. I dont have that luxury, though I can access the internet using win xp.

I was wondering if someone could help me manually set up my wireless connection using an Intel Wireless 2200 BG card from scratch. I've combed the forums for this but I cant even do simple stuff like build-essential as it cant connect to the internet.

Thanks guys

---

### Post by Buffalo Soldier on 2007-05-19
Been using a laptop with Intel Wireless 2200BG since 5.04 and it was detected properly since initial installation. There's no need to download or install additional drivers. But at that time it was a bit of a hassle to use WPA encryption.

Since the latest version (7.04) even WPA encryption has been working flawlessly. Here's my **lspci** output:
```
~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
01:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
[COLOR="Blue"]01:03.0 Network controller: **Intel Corporation PRO/Wireless 2200BG** Network Connection (rev 05)[/COLOR]
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)

```

Try typing iwconfig at the terminal. What's the output? Here's an example of mine:
```
~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"dlink"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:47:9B:FF:CB:AA   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=86/100  Signal level=-43 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:1
```

---

### Post by apradhan on 2007-05-19
hey,

thanks for the reply

device manager does ist my wireless card

when i type iwconfig it says :



sorry  i cant copy the text as im typing here from a different computer:-

lo              no wireless extensions

eth0         no wireless extensions

eth1       unassociated  ESSID: ' avinash'
              Mode: Managed channel = 0 Access Point not associated
             bit rate 0
            signal level 0 

and everything else is 0 

i'll try copying the exact text if you need it...but everything says 0

---

### Post by apradhan on 2007-05-19
lspci does list my correct wireless card so i guess its just a case of finding the network...........

02.02.0 Network controller: Intel Corporation PRO/Wireless 2200 BG Network Controller (rev5)

---

### Post by apradhan on 2007-05-19
ok...so my wireless card is installed and i can connect to the network and recognize the signal.

When I use the System -> Adminstration -> Network Connections options I put in the network name and ESSID and i can now get a 100% signal detection on the taskbar


iwconfig says

eth1      IEEE 802.11g  ESSID:"Avinash"  
         
 Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:39:5B:AE:AD   
        
  Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          
Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
         
 Link Quality=93/100  Signal level=-34 dBm  Noise level=-88 dBm
         
 Rx invalid nwid:0  Rx invalid crypt:24  Rx invalid frag:0
      
    Tx excessive retries:0  Invalid misc:0   Missed beacon:1
---------


but i still cant connect to the internet ........is there anything missing ?

---

### Post by apradhan on 2007-05-19
ok so i tried

adu@adu-laptop:~$ sudo ifconfig

Password:

eth0  
    Link encap:Ethernet  HWaddr 00:0A:E4:27:6B:73  
       
   UP BROADCAST MULTICAST  MTU:1500  Metric:1
         
 RX packets:0 errors:0 dropped:0 overruns:0 frame:0
        
  TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         
 collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  
TX bytes:0 (0.0 b)



eth1      Link encap:Ethernet  HWaddr 00:0E:35:4A:B5:11  
     
     inet6 addr: fe80::20e:35ff:fe4a:b511/64 Scope:Link
         
 UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
         
 RX packets:86 errors:83 dropped:83 overruns:0 frame:0
       
   TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
       
   collisions:0 txqueuelen:1000 
      
    RX bytes:0 (0.0 b)  TX bytes:7152 (6.9 KiB)
   
       Interrupt:11 Base address:0x8000 Memory:d0200000-d0200fff 

lo   
     Link encap:Local Loopback  
    
      inet addr:127.0.0.1  Mask:255.0.0.0
   
       inet6 addr: ::1/128 Scope:Host
         
 UP LOOPBACK RUNNING  MTU:16436  Metric:1
      
    RX packets:2 errors:0 dropped:0 overruns:0 frame:0
  
        TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
  
        collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)


does that help |

---

### Post by apradhan on 2007-05-19
I did it !!!!!!!!!!!!!!!!!!!!!

For those who might be having the same problem as me -

do this....its copied from a previous post by hamustar in [http://ubuntuforums.org/showthread.php?t=26623](http://ubuntuforums.org/showthread.php?t=26623)

this is what u do, in sudo / root mode,

Step 1
# iwconfig
-- u should see that u have IEEE802.11(B/G) under eth1 (or some other)

Step 2
# iwlist eth1 scan
-- this will scan for all available networks.
-- if there is something picked up, it means ubuntu is able to detect a network.
-- if nothing is detected, pls check your router.

Step 2a: if your wlan network is protected
# iwconfig eth1 essid YOURSSID
-- to define your SSID (access point name)
# iwconfig eth1 key xxxxxxxxxx
-- to define your WEP key, if any.

Step 3
# dhclient eth1
-- this will request a IP from your router, if successfull u will see some messages ending with " bound to 192.168.x.x..." 
-- u are connected to the internet !

hope this helps some of the newbies.


thanks for the great posts people............UBUNTU ROCKS

---

### Post by Buffalo Soldier on 2007-05-19
Glad that it worked out for you :)

Just in case you're looking for a GUI to manage your wireless networks, you might be interested in [NetworkManager](http://www.gnome.org/projects/NetworkManager/). There's a guide in the [Ubuntu Community Wiki](https://help.ubuntu.com/community/WifiDocs/NetworkManager) on how to set it up.

And yes... Ubuntu and it's [URL=http://www.ubuntu.com/community/processes/newmember]members[URL] rocks :)

---

