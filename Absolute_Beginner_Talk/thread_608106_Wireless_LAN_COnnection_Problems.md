---
title: "Wireless LAN COnnection Problems"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by sjk44 on 2007-11-09
I am a new user trying to convert from Windows and am trying to bring up the newest version (Gutsy Gibbon) of Ubuntu on an old ThinkPad equipped with a Linksys Wireless-G model WPC54G version 3.1 PCMCIA card for a WLAN connection.  I cannot get the WLAN connection to work.  I have installed a package called Wicd instead of Network Manager.  Wicd says it cannot find any wireless connections.  When I do an IWCONFIG command the following appears: 

ubuntu-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth3      IEEE 802.11b/g  ESSID:"1dcq"  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

How can I get the wireless connection to work?

---

### Post by Pumalite on 2007-11-09
Maye this helps?:

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/)

---

