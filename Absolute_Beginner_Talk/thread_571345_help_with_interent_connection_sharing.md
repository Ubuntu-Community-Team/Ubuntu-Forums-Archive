---
title: "help with interent connection sharing"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by Schinoble on 2007-10-09
Presently i have win xp on my main machine with internet through a network card and has a wifi card connected to it that i use to share internet to a ubuntu machine, I'm trying get rid of winXP all together but cant get ubuntu to create an internet connection sharing. any help would be much appreciated. 

i've tried bringing up an ad-hoc connection on moth machines with ubuntu running but cant seem to ping one machine from another

---

### Post by Schinoble on 2007-10-09
anyone ? 

i've used 

modprobe -r ath_pci
modprobe ath_pci autocreate=adhoc
iwconfig ath0 essid laptop channel 2 key s:12345 rate 11M
ifconfig ath0 192.168.0.1
ifconfig ath0 up

and 

iwconfig ra1 mode ad-hoc essid laptop channel 2 key s:12345 rate 11M
ifconfig ra1 192.168.0.2
ifconfig ra1 up

when i iwconfig and iwlist scan they settings seem to be the same even down to matching the cell: but i cant ping each computer from one another 

any help would be much appreciated

---

### Post by rmockler on 2007-10-09
Do you also have Ubuntu installed on the main machine so you can dual-boot with XP?  Seems like that would be a logical first step toward getting rid of XP.   Then you could more easily recognize any problem areas, and take steps to resolve them.

---

### Post by Schinoble on 2007-10-09
yup the main machine is dual booted with xp, when its running XP i can get ubuntu to connect to the XP machine and share its internet fine, its when i get ubuntu booted on the main machine i cant seem to create the network, 

Iwlist scan results

          Cell 01 - Address: 02:16:E3:24:78:8E
                    ESSID:"laptop"
                    Mode:Ad-Hoc
                    Frequency:2.417 GHz (Channel 2)
                    Quality=54/94  Signal level=-41 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100


iwconfig results

        ath0      IEEE 802.11g  ESSID:"laptop"  Nickname:""
          Mode:Ad-Hoc  Frequency:2.417 GHz  Cell: 02:16:E3:24:78:8E   
          Bit Rate=11 Mb/s   Tx-Power:16 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=29/94  Signal level=-62 dBm  Noise level=-91 dBm
          Rx invalid nwid:11  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

both from the laptop

Any ideas why i cant ping one computer from the other ?

---

### Post by Schinoble on 2007-10-09
i have once, while playing with iptables, dmnasq (i think) and firestarter managed to get the connection working where the laptop running Windows XP or Ubuntu could connect to the Ubuntu machine which would re-assign it an IP address from dhcpd3 (i think) and share its internet connection, but once i rebooted the computer it broke again i've spent the last 2 days going through everything to get it back up, presently i cant even get one computer to ping another let alone share the internet.

could it be something to do with the firewall thats stopping the connection from connecting ?

when i try and setup an ad-hoc connection from Ubunto i can find it through windows and connect to it pending i fill in the IP address, default gateway and whatnot in windows (or it takes forever to connect with a random IP address and no default gateway address) windows says that the connection is active and when i try and ping it from the ubuntu side i can see that the windows is receiving data but the ping fails, same with the windows side the connection is there, but cant seem to ping the other computer. 

please please all you linux guru's lend us a hand. i've spent the last whole week constantly trecking through the net and ubuntu forums trying to find a fix, getting close to a stage of giving up trying to replace the win XP main machine with ubuntu

---

