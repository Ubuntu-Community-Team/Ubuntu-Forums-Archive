---
title: "Wireless WPC54G Ver 3 problem"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by nistaani on 2006-11-27
Hi there everyone.  I'm totally new to Ubuntu - 3days and counting but loving it so far.

Have an issue getting wireless to work and its the last hurdle.

Running a dell inspiron 5100 with Ubuntu 6.10 & a Linksys WPC54G ver3.0 wireless card.

I've had a read through a few relevant posts here and proceeded with the ndiswrapper option.  The driver installed fine (as far as I'm aware) Power light is on and the wireless link light is blinking intermittently.  Installed KWiFiManager which detects the card but can't find the network.  My xp box finds the network with no problem.

Below are all the things I know relevant to the issue.  if anyone can help, i'd be very grateful.

_iwconfig_

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


_iwlist scan_

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

eth1      No scan results


_sudo gedit /etc/network/interfaces_

auto lo
iface lo inet loopback


iface eth0 inet dhcp


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

:confused: 

auto wlan0
iface wlan0 inet dhcp

---

### Post by ]Nbx*cmD[ on 2007-04-20
Hmmm

i strongly recommend you to install feisty and check out this howto, i've got exactly the same card as you and it was a piece of cake for me :)

[http://ubuntuforums.org/showthread.php?t=405990&highlight=wpc54g+v3]("http://http://ubuntuforums.org/showthread.php?t=405990&highlight=wpc54g+v3")

Good luck!

---

### Post by thirstygerry on 2007-07-19
> **']Nbx*cmD[ said:**
> Hmmm

i strongly recommend you to install feisty and check out this howto, i've got exactly the same card as you and it was a piece of cake for me :)

[http://ubuntuforums.org/showthread.php?t=405990&highlight=wpc54g+v3]("http://http://ubuntuforums.org/showthread.php?t=405990&highlight=wpc54g+v3")

Good luck!

The link was malformed :)

[http://ubuntuforums.org/showthread.php?t=405990&highlight=wpc54g+v3]("http://ubuntuforums.org/showthread.php?t=405990&highlight=wpc54g+v3")

---

