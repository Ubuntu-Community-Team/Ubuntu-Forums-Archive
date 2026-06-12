---
title: "Atheros 5418 Wireless not working"
date: 2008-01-05
forum: Apple Intel Users
---

### Post by cvasilak on 2008-01-05
Hi there, i am running ubuntu gutsy with the generic kernel supplied
cvasilak@euphoria:~$ uname -a
Linux euphoria 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux

on a macbook core 2 duo machine. The machine comes with an atheros 5418 chipset. I have downloaded the latest svn version of madwifi drivers. Installation is done successfully, the interface ath0 brings up. I set the essid to my network. I then to dhclient but it can't acquire an IP address. It seems that it cannot associate with the access point.

root@euphoria:/home/cvasilak# iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"linksys"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:14 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:564  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@euphoria:/home/cvasilak# lspci
03:00.0 Network controller: Atheros Communications, Inc. AR5418 802.11a/b/g/n Wireless PCI Express Adapter (rev 01)

root@euphoria:/home/cvasilak# dmesg

[ 1407.056000] ath_hal: 0.9.30.13 (AR5210, AR5211, AR5212, AR5416, RF5111, RF5112, RF2413, RF5413, RF2133)
[ 1407.072000] wlan: svn r3114
[ 1407.080000] ath_pci: svn r3114
[ 1407.080000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[ 1407.080000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[ 1407.208000] ath_pci: switching rfkill capability off
[ 1407.220000] ath_rate_sample: 1.2 (svn r3114)
[ 1407.220000] ath_pci: switching per-packet transmit power control off
[ 1407.220000] wifi0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[ 1407.220000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[ 1407.220000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[ 1407.220000] wifi0: turboG rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[ 1407.220000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[ 1407.220000] wifi0: mac 12.10 phy 8.1 radio 12.0
[ 1407.220000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[ 1407.220000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[ 1407.220000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[ 1407.220000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[ 1407.220000] wifi0: Use hw queue 8 for CAB traffic
[ 1407.220000] wifi0: Use hw queue 9 for beacons
[ 1407.236000] wifi0: Atheros 5418: mem=0x98100000, irq=17

---

### Post by cyberdork33 on 2008-01-05
why are you configuring manually? Use network-manager in the toolbar.

---

### Post by cvasilak on 2008-01-05
Well network-manager works perfectly with the wired connection but doesn't see the wireless network thus i cann't configure it :(

---

### Post by GeneralSunTzu on 2008-01-05
I would be surprised if it would see it, with a signal as weak as yours...
To confirm di the following:
1. fire up MacOS X and load AirGrapher;
2. note signal level of your network, channel number and strength if the signal;
3. see by yourself or report here the results.

Either your signal is insufficient or a neighbouring network is whacking the signal of the net you want to climb aboard on.

BTW, as cyberdork33 correctly pointed out, even when the signal is very weak, it usually will be shown by Network-manager.

---

### Post by cvasilak on 2008-01-05
Thanks for the reply,
the thing is that the wireless router is near my computer so i assume this is not a signal problem

---

### Post by GeneralSunTzu on 2008-01-05
> **cvasilak said:**
> Thanks for the reply,
the thing is that the wireless router is near my computer so i assume this is not a signal problem

I am afraid your assumption is wrong.
Look, -90 dB means  0.000000001 mW on a 50 Ohm load.
Cosmic background radiation is stronger...
I repeat, either there is a serious problem of intensity or you have a wireless telephone (which is also on the 2.4 GHz band) base station within a few inches, or your neighbour is the BBC, as far as irradiated power is concerned.
Kindly use AP Grapher (freeware) and then we'll have data, not unwarranted speculation.

---

### Post by cvasilak on 2008-01-06
Hi there,

i fired up macosx and ap grapher and here is the results:

[IMG]http://cvasilak.angelfire.com/grapher.png[/IMG]

---

### Post by cvasilak on 2008-01-06
sorry angelfire screwed it up

a screenshot:

[IMG]http://users.forthnet.gr/her/gvasilakis/grapher.png[/IMG]

---

### Post by GeneralSunTzu on 2008-01-06
All right, thank you.

Now we know, with absolute certainty, that:
1. your signal is strong enough;
2. there is no rogue WiFi net nearby;
3. noise level seems very low as well.

However: when AP Grapher says that security is "unknown", usually it means either nothing or WPA/WPA2, because AP Grapher recognizes WEP and no security.

My suggestion: from Mac OS X configure the router so that you are sure that it is open (no secuirty whatsoever). Ensure then that with Mac OS X you can get onto this network.
Reboot then and check what happens with Ubuntu.

Pay attention! 

If, after installing madwifi, you installed any update which required a kernel re-compile, then madwifi is "forgotten", and you have to re-install it.
I keep in fact, to avoid this problem, always the sources of the latest trunk madwifi, which I re-compile, should the need present itself (it has happened twice).

Good luck!

---

### Post by cvasilak on 2008-01-06
Hi there,
I don't use any wep or wpa. security is disabled on the router. It's open to everyone :)

Yeap I know that I need to recompile the madwifi sources after a kernel upgrade. I Just installed the current trunk  madwifi just to be sure but didn't help.

Thanks for your help

---

### Post by GeneralSunTzu on 2008-01-06
You're welcome.
Here is the last chance, after which I am afraid I may have to give up...

Look at this thread and compare the firmware release of your Linksys router:

[http://ubuntuforums.org/showthread.php?t=68820](http://ubuntuforums.org/showthread.php?t=68820)

Again, good luck!

---

### Post by cyberdork33 on 2008-01-07
I think when he said it doesn't show in network-manager, he meant the card is not even available... which likely means you have a driver problem, and has nothing to do with your router...

can you do 'iwlist' at the terminal and see i the card is listed there?

---

### Post by cvasilak on 2008-01-07
lspci
03:00.0 Network controller: Atheros Communications, Inc. AR5418 802.11a/b/g/n Wireless PCI Express Adapter (rev 01)

iwconfig
ath0      IEEE 802.11g  ESSID:"linksys"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:14 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:412  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

dmesg
[  921.680000] ath_hal: 0.9.30.13 (AR5210, AR5211, AR5212, AR5416, RF5111, RF5112, RF2413, RF5413, RF2133)
[  921.696000] wlan: 0.8.4.2 (svn r2717)
[  921.700000] ath_pci: 0.9.4.5 (svn r2717)
[  921.700000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[  921.700000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[  921.832000] ath_pci: switching rfkill capability off
[  921.852000] ath_rate_sample: 1.2 (svn r2717)
[  921.852000] ath_pci: switching per-packet transmit power control off
[  921.852000] wifi0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[  921.852000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[  921.852000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[  921.852000] wifi0: turboG rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[  921.852000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[  921.852000] wifi0: mac 12.10 phy 8.1 radio 12.0
[  921.852000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[  921.852000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[  921.852000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[  921.852000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[  921.852000] wifi0: Use hw queue 8 for CAB traffic
[  921.852000] wifi0: Use hw queue 9 for beacons
[  921.892000] wifi0: Atheros 5418: mem=0x98100000, irq=17

---

### Post by cyberdork33 on 2008-01-07
well your card is obviously enabled to the system, but it looks as though you have tried to set the essid manually which can confuse network-manager. Make sure that Roaming mode is enabled in the network config applet (System > Administration > Network)

---

### Post by cvasilak on 2008-01-07
I checked and roaming is enabled in System->Administration->Network

Network-manager doesn't list "linksys" in the wireless section that's why i set the essid manually. 

Also I don't use any wep or wpa, the router is open

---

### Post by cyberdork33 on 2008-01-07
> **cvasilak said:**
> Network-manager doesn't list "linksys" in the wireless section that's why i set the essid manually. if that is the case it may be interference or an issue such as was already suggested. You might try changing the essid of your router as well (since that is the default), as it might be interfering with another router nearby with the same essid.

> Also I don't use any wep or wpa, the router is openI would suggest changing that in the future, but it really makes no difference to getting connected with network-manager.

---

### Post by mabovo on 2008-01-07
I am now writing from my MacBook 2,1 with Hardy 8.04 through the wireless card AR5418 without any networking security.

Is there some workaround on how to implement WPA-PSK security with this card ?

Thanks.

---

### Post by cyberdork33 on 2008-01-08
> **mabovo said:**
> I am now writing from my MacBook 2,1 with Hardy 8.04 through the wireless card AR5418 without any networking security.

Is there some workaround on how to implement WPA-PSK security with this card ?

Please start a new thread for a new question. I don't really understand what you mean by workaround... if you need encryption to connect to an AP, you have to use it, if it is not setup with encryption, then you can't try to use it anyway.

---

### Post by mabovo on 2008-01-09
Sorry for disturbing this thread but I have the same situation of "cvasilak"
I am stuck on how to make AR5418 works and don't know how to do it.

I read the posts of wireless setup on MacBooks but I am missing a little trick to conclude this task.

Can You help me, please ?

---

### Post by cyberdork33 on 2008-01-09
> **mabovo said:**
> Sorry for disturbing this thread but I have the same situation of "cvasilak"
I am stuck on how to make AR5418 works and don't know how to do it.

I read the posts of wireless setup on MacBooks but I am missing a little trick to conclude this task.

Can You help me, please ?

Then I am confused because you just said your card was working in the last post. What exactly is the issue? what have you already done to try to fix it?

---

### Post by mabovo on 2008-01-09
Yes, it was functioning with madwifi driver but only accessing the access point essid manually and without enable security WEP or WPA.
I've got a windows driver from here [http://ubuntuforums.org/showthread.php?t=651205](http://ubuntuforums.org/showthread.php?t=651205) and installed it using ndiswrapper.
After that my wireless card was disabled in network-manager and I can't even scan the essid to show the name of wireless networking.

If this help I have this:

mabovo@macbook:~$ iwconfig ath0
ath0      IEEE 802.11g  ESSID:"linksys"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:14 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=4/70  Signal level=-92 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

mabovo@macbook:~$ sudo iwlist ath0 scan
[sudo] password for mabovo: 
ath0      Scan completed :
          Cell 01 - Address: 00:18:39:40:3F:A8
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=7/70  Signal level=-88 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:15:E9:79:52:9E
                    ESSID:"bovo"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-63 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

mabovo@macbook:~$

---

### Post by cyberdork33 on 2008-01-10
> **mabovo said:**
> Yes, it was functioning with madwifi driver but only accessing the access point essid manually and without enable security WEP or WPA.
I've got a windows driver from here [http://ubuntuforums.org/showthread.php?t=651205](http://ubuntuforums.org/showthread.php?t=651205) and installed it using ndiswrapper.
After that my wireless card was disabled in network-manager and I can't even scan the essid to show the name of wireless networking.

Please use the code tags to make your output more legible.

I can see one issue for you is the fact that you are not actually using ndiswrapper, but are still using madwifi... madwifi causes the card to be called ath0, but ndiswrapper does not use that nomenclature (unless you manually change a lot..). Usually, it shows up as 'wlan0' and the like. If you want to use ndiswrapper, you need to remove madwifi first, and vice-versa.

However, your scan output shows that you can see several APs, so you really do not need to use ndiswrapper as the madwifi driver seems to work. Make sure that you set the card to roaming mode in System > Administration > Network. It must be in this mode for network-manager to configure it.

---

### Post by cvasilak on 2008-01-10
The driver is now working! :)

I downloaded the svn version [http://snapshots.madwifi.org/madwifi-ng/madwifi-ng-r3122-20080109.tar.gz](http://snapshots.madwifi.org/madwifi-ng/madwifi-ng-r3122-20080109.tar.gz) from madwifi which seems that they have corrected the problem

Anyways, thanks a lot for your helps

Christos

---

### Post by mabovo on 2008-01-18
I removed security on my network and get this result.

```

mabovo@macbook:~/mac_drivers/isight$ sudo iwlist ath0 scan
[sudo] password for mabovo: 
ath0      Scan completed :
          Cell 01 - Address: 00:15:E9:79:52:9E
                    ESSID:"bovo"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=64/70  Signal level=-31 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100

mabovo@macbook:~/mac_drivers/isight$ 

```

---

### Post by cyberdork33 on 2008-01-20
> **mabovo said:**
> I removed security on my network and get this result.

There doesn't seem to be anything wrong with that.

---

### Post by hardawayd on 2008-02-20
I keep getting these errors when trying to make the madwifi module. Do you know what's wrong?


hardaway@ubuntu:~/Desktop/madwifi-ng-r3358-20080215$ sudo make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-8-generic/build SUBDIRS=/home/hardaway/Desktop/madwifi-ng-r3358-20080215 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-8-generic'
  CC [M]  /home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath/if_ath.o
  CC [M]  /home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath/if_ath_radar.o
  CC [M]  /home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath/if_ath_pci.o
  LD [M]  /home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath/ath_pci.o
  CC [M]  /home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/ah_os.o
  HOSTCC  /home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c: At top level:
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c: In function 'main':
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal/uudecode] Error 1
make[2]: *** [/home/hardaway/Desktop/madwifi-ng-r3358-20080215/ath_hal] Error 2
make[1]: *** [_module_/home/hardaway/Desktop/madwifi-ng-r3358-20080215] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-8-generic'
make: *** [modules] Error 2
hardaway@ubuntu:~/Desktop/madwifi-ng-r3358-20080215$

---

### Post by cyberdork33 on 2008-02-20
> **hardawayd said:**
> I keep getting these errors when trying to make the madwifi module. Do you know what's wrong?Please use the code tag to make output more legible.

You need to install the build-essential package before you can compile.
```
sudo aptitude install build-essential
```

---

### Post by mabovo on 2008-02-20
Hi, it's me again !  

Using nm-0.6.5 is possible to connect for a short period of two or three hours then it disconnects.

Now I am testing Hardy A4 and nm-0.7 with madwifi-ng-r3358-20080215.
Although tne nm-applet shows the AP signal strength in fact it can't connect on WPA/WPA2 OR OPEN wireless. Devs are investigating this (I hope so).

My question is about Madwifi 0.9.4 new driver release !

Do I need install it on kernel 2.6.24-8 or if I only install the current madwifi-ng from snapshots.madwifi.org is enough  ?

---

### Post by cyberdork33 on 2008-02-20
> **mabovo said:**
> My question is about Madwifi 0.9.4 new driver release !

Do I need install it on kernel 2.6.24-8 or if I only install the current madwifi-ng from snapshots.madwifi.org is enough  ?There is no support for the AR5418 in 0.9.4 so I would stick with what you have.

---

