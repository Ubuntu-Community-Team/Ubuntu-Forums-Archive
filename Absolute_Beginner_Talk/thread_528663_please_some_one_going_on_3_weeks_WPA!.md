---
title: "please some one going on 3 weeks WPA!"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by Tlingit on 2007-08-18
im almost there it says that im connected i do not have a wired network i only have wireless some one help i dont know what to do i have been all over try ed a lot help please i would appreciate it

---

### Post by ugm6hr on 2007-08-18
I have noticed that you seem to have posted multiple times everywhere in this forum:
[http://ubuntuforums.org/showthread.php?p=3176596#post3176596](http://ubuntuforums.org/showthread.php?p=3176596#post3176596)
[http://ubuntuforums.org/showthread.php?p=3210102#post3210102](http://ubuntuforums.org/showthread.php?p=3210102#post3210102)
[http://ubuntuforums.org/showthread.php?p=3210239#post3210239](http://ubuntuforums.org/showthread.php?p=3210239#post3210239)

This will just be confusing for both you and people helping, so I would suggest you stick to one thread.

And start from the beginning:
Your label states Ubuntu 4.10 - is that true?  If so - I would suggest upgrading to a more recent version (6.06 or 7.04 depending on preference), and trying again.
Does your internet work with an Open / WEP network?

---

### Post by Tlingit on 2007-08-18
sorry no one answers me ok i am using 7.04 it sees the connection i manually enabled wpa it says that i am connected but im not using 
[http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136)
every one pointed me there i have been at it for weeks every one pointed me there i have searched around and i dont know what to do now

---

### Post by Tlingit on 2007-08-18
I dont know about wep my landlord set the network up as a wpa it sees all of the connections but no option for wpa i enabled wpa using that guid now it says im connectid but im not

---

### Post by Tlingit on 2007-08-18
> **Tlingit said:**
> sudo wpa_supplicant -w -Dwext -i eth0 -c/etc/wpa_supplicant.conf -dd

Initializing interface 'eth0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'

Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'

Reading configuration file '/etc/wpa_supplicant.conf'

ctrl_interface='var/run/wpa_supplicant'

Line: 3 - start of a new network block

ssid - hexdump_ascii(len=6):

     62 72 61 6e 63 68                                 xxxxxx          

scan_ssid=1 (0x1)

proto: 0x1

key_mgmt: 0x2

pairwise: 0x8

PSK - hexdump(len=32): [REMOVED]

Line 10: removed CCMP from group cipher list since it was not allowed for pairwise cipher

Priority group 0

   id=0 ssid='branch'

Initializing interface (2) 'eth0'

EAPOL: SUPP_PAE entering state DISCONNECTED

EAPOL: KEY_RX entering state NO_KEY_RECEIVE

EAPOL: SUPP_BE entering state INITIALIZE

EAP: EAP entering state DISABLED

EAPOL: External notification - portEnabled=0

EAPOL: External notification - portValid=0

ioctl[SIOCSIWMODE]: Operation not supported

Could not configure driver to use managed mode

ioctl[SIOCGIWRANGE]: Operation not supported

WEXT: Operstate: linkmode=1, operstate=5

Own MAC address: 00:02:3f:3e:a4:d9

wpa_driver_wext_set_wpa

ioctl[SIOCSIWAUTH]: Operation not supported

WEXT auth param 7 value 0x1 - Driver does not support WPA.

wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0

ioctl[SIOCSIWENCODEEXT]: Operation not supported

Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE

ioctl[SIOCSIWENCODE]: Operation not supported

wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0

ioctl[SIOCSIWENCODEEXT]: Operation not supported

Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE

ioctl[SIOCSIWENCODE]: Operation not supported

wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0

ioctl[SIOCSIWENCODEEXT]: Operation not supported

Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE

ioctl[SIOCSIWENCODE]: Operation not supported

wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0

ioctl[SIOCSIWENCODEEXT]: Operation not supported

Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE

ioctl[SIOCSIWENCODE]: Operation not supported

wpa_driver_wext_set_countermeasures

ioctl[SIOCSIWAUTH]: Operation not supported

WEXT auth param 4 value 0x0 - wpa_driver_wext_set_drop_unencrypted

ioctl[SIOCSIWAUTH]: Operation not supported

WEXT auth param 5 value 0x1 - Setting scan request: 0 sec 100000 usec

mkdir[ctrl_interface]: No such file or directory

Failed to initialize control interface 'var/run/wpa_supplicant'.

You may have another wpa_supplicant process already running or the file was

left by an unclean termination of wpa_supplicant in which case you will need

to manually remove this file before starting wpa_supplicant again.



Failed to add interface eth0

State: DISCONNECTED -> DISCONNECTED

t this is what i get when i enter this command (sudo wpa_supplicant -w -Dwext -i eth0 -c/etc/wpa_supplicant.conf -dd)

---

### Post by ugm6hr on 2007-08-18
That guide is unnecessary for Feisty. Network Manager is able to manage WPA without manual configuration of wpa-supplicant.  The other option is Wicd (see my signature link).

Start from the beginning:
```
lspci -nn | grep Ethernet
lspci -nn | grep Network
lshw -C network
iwconfig
iwlist scan
```
Post the output from these commands.

---

### Post by Tlingit on 2007-08-18
lspci -nn | grep Ethernet

02:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)

i am not sure how to post the code like you do but here is the first one

---

### Post by Tlingit on 2007-08-18
lspci -nn | grep Network
```

03:00.0 Network controller [0280]: Texas Instruments ACX 111 54Mbps Wireless Interface [104c:9066]

 lshw -C network

WARNING: you should run this program as super-user.

  *-network               

       description: Ethernet interface

       product: RTL-8139/8139C/8139C+

       vendor: Realtek Semiconductor Co., Ltd.

       physical id: 1

       bus info: pci@02:01.0

       logical name: eth0

       version: 10

       serial: 00:02:3f:3e:a4:d9

       width: 32 bits

       clock: 33MHz

       capabilities: bus_master cap_list ethernet physical

       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 multicast=yes

       resources: ioport:3400-34ff iomemory:e8200800-e82008ff irq:10

  *-network

       description: Wireless interface

       product: ACX 111 54Mbps Wireless Interface

       vendor: Texas Instruments

       physical id: 0

       bus info: pci@03:00.0

       logical name: wlan0

       version: 00

       serial: 00:14:bf:03:c0:70

       width: 32 bits

       clock: 33MHz

       capabilities: bus_master cap_list ethernet physical wireless

       configuration: broadcast=yes driver=acx_pci latency=64 multicast=yes wireless=IEEE 802.11b+/g+

       resources: iomemory:28020000-28021fff iomemory:28000000-2801ffff irq:11
```

---

### Post by Tlingit on 2007-08-18
iwconfig

```
lo        no wireless extensions.



eth0      no wireless extensions.



wlan0     IEEE 802.11b+/g+  ESSID:""  Nickname:"acx v0.3.36"

          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   

          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3  

          Retry min limit:7   RTS thr:off   

          Power Management:off

          Link Quality=32/100  Signal level=5/100  Noise level=0/100

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by Tlingit on 2007-08-18
```
 iwlist scan

lo        Interface doesn't support scanning.



eth0      Interface doesn't support scanning.



wlan0     Scan completed :

          Cell 01 - Address: 00:12:17:03:CB:FE

                    ESSID:"branch"

                    Mode:Master

                    Frequency:2.437 GHz (Channel 6)

                    Quality=49/100  Signal level=28/100  Noise level=0/100

                    Encryption key:on

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s

                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s

                              48 Mb/s; 54 Mb/s

          Cell 02 - Address: 00:1A:70:78:16:BE

                    ESSID:"Dweidner"

                    Mode:Master

                    Frequency:2.437 GHz (Channel 6)

                    Quality=31/100  Signal level=4/100  Noise level=0/100

                    Encryption key:on

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s

                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s

                              48 Mb/s; 54 Mb/s

          Cell 03 - Address: 00:13:46:D1:A9:54

                    ESSID:"-=FLAT=-"

                    Mode:Master

                    Frequency:2.437 GHz (Channel 6)

                    Quality=36/100  Signal level=11/100  Noise level=0/100

                    Encryption key:on

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s

                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s

                              48 Mb/s; 54 Mb/s

          Cell 04 - Address: 00:11:24:29:96:91

                    ESSID:"Apple Network 299691"

                    Mode:Master

                    Frequency:2.457 GHz (Channel 10)

                    Quality=31/100  Signal level=4/100  Noise level=0/100

                    Encryption key:off

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s

                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s

                              48 Mb/s; 54 Mb/s

          Cell 05 - Address: 00:17:3F:95:45:43

                    ESSID:"CVAPM"

                    Mode:Master

                    Frequency:2.462 GHz (Channel 11)

                    Quality=31/100  Signal level=3/100  Noise level=0/100

                    Encryption key:on

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s

                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s

                              48 Mb/s; 54 Mb/s

          Cell 06 - Address: 00:18:39:E4:A7:87

                    ESSID:"number 1"

                    Mode:Master

                    Frequency:2.412 GHz (Channel 1)

                    Quality=31/100  Signal level=3/100  Noise level=0/100

                    Encryption key:on

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s

                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s

                              48 Mb/s; 54 Mb/s

          Cell 07 - Address: 00:11:95:19:1E:6E

                    ESSID:"Big Balloo"

                    Mode:Master

                    Frequency:2.437 GHz (Channel 6)

                    Quality=30/100  Signal level=2/100  Noise level=0/100

                    Encryption key:on

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s

                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s

                              48 Mb/s; 54 Mb/s

          Cell 08 - Address: 00:18:F8:DE:CF:8E

                    ESSID:"linksys"

                    Mode:Master

                    Frequency:2.437 GHz (Channel 6)

                    Quality=29/100  Signal level=1/100  Noise level=0/100

                    Encryption key:off

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s

                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s

                              48 Mb/s; 54 Mb/s


```

---

### Post by ugm6hr on 2007-08-18
> **Tlingit said:**
> 
       product: [COLOR="#ff0000"]ACX 111[/COLOR] 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 0
       bus info: pci@03:00.0
       logical name: wlan0
       version: 00
       serial: 00:14:bf:03:c0:70
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes [COLOR="Red"]driver=acx_pci[/COLOR] latency=64 multicast=yes wireless=IEEE 802.11b+/g+
       resources: iomemory:28020000-28021fff iomemory:28000000-2801ffff irq:11[/code]

I think this is your problem.  The ACX linux drivers don't support WPA, as discussed here: [http://sourceforge.net/tracker/index.php?func=detail&aid=950561&group_id=75380&atid=543748](http://sourceforge.net/tracker/index.php?func=detail&aid=950561&group_id=75380&atid=543748)

If the network doesn't belong to you (i.e. it is your landlord's), then your only option is to use ndiswrapper:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
Just remember to blacklist the *acx_pci* driver (instead of bcm43xx).
I think it will work with the Windows XP driver for your device (or probably any of the ACX111 drivers listed here: [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/) (just search for *104c:9066*)

---

### Post by caricc on 2007-08-20
Try using wicd. This worked for me and i have had no problem with wireless since installing this app.

---

### Post by yogo on 2007-08-20
> **caricc said:**
> Try using wicd. This worked for me and i have had no problem with wireless since installing this app.


I like wicd also BUT that alone will not solve his problem.

ugm6hr has the right advice,using ndiswrapper to install the correct driver for his device and blacklisting the other.

Then he can decide to use a different manager for his wireless if so inclined.

In simple terms what I did was install the driver on my window box and then copied the folder over from program files and used NDISwrapper to install the inf driver file.

Do these correctly and you should be up and going in no time.

Also once you do these post the results of (sudo dhclient eth0)

---

