---
title: "How do you use WPA with laptop broadcom 4306?"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by iceman0304 on 2008-01-16
Using Gutsy 7.10 Ubuntu 32bit     the wireless was working, but doesn't with the WPA or WPA2 security

> **stchman said:**
> What I believe you are referring to is the installation of Network Manager.  NM is installed by default on Feisty and later.  What Ubuntu are you running.

Whatever version of Ubuntu you are running then follow the instructions.

For Feisty follow the instructions I have on my page for getting the ndiswrapper up and running.  For Gutsy follow these instructions:

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Broadcom_wireless_driver](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Broadcom_wireless_driver)

I wish that Broadcom would make Linux drivers for their cards.

Remember, Network Manager is installed by default on Feisty and later and NM is capable of connecting to WEP/WPA/WPA2 points.


here is what I got with this when I tried it, any suggestions?



matt@matt-laptop:~$ lspci | grep Broadcom
00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
matt@matt-laptop:~$ gksu gedit /etc/apt/sources.list


This is what opens: gedit

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe main multiverse restricted #Added by software-properties
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse


matt@matt-laptop:~$ deb [http://ubuntu.cafuego.net](http://ubuntu.cafuego.net) gutsy-cafuego bcm43xx
bash: deb: command not found
matt@matt-laptop:~$

---

### Post by Hightide on 2008-01-19
have a look at Dark Noobs thread 
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

and  Weiman01's tutorial

[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

they might help

:guitar:

---

### Post by iceman0304 on 2008-01-19
Yeah I have looked at them but wasn't sure if It'd work, the last one I wasn't sure about doing the static IP.

Can you answer this about the static IP? Of course I use dhcp for my internet connection, and wasn't sure if this is going to work with this situation.

:confused:

---

### Post by iceman0304 on 2008-01-19
I did both of the sites and haven't had any luck



matt@matt-laptop:~$ sudo gedit /etc/network/interfaces 
[sudo] password for matt:


auto lo
iface lo inet loopback

auto eth1                           _<--------- I lost my wired lan with this in had to remove_ 
iface eth1 inet dhcp                                   _it to get connected via wired lan._
wpa-ap-scan 1
wpa-pairwise TKIP
wpa-group TKIP
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid linksys

auto eth1


matt@matt-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1C:10:49:EE:97
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managedmatt@matt-laptop:~$ sudo gedit /etc/network/interfaces 
[sudo] password for matt:

                    Frequency:2.437 GHz (Channel 6)
                    Quality:78/100  Signal level:-46 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


iface eth0 inet dhcp                                                            _<--------is this OK_

auto eth0                                                                           _<-------is this OK_



matt@matt-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

:confused:

---

