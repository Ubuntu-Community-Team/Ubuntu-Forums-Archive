---
title: "Wireless pci WMP54G   2.4GHz  802.11g"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by acefx on 2007-02-27
I just installed Kubuntu 6.10 on my slightly older box, I installed a  Linksys Wireless pci WMP54G be for I installed Kubuntu when I pull up wlassistant and click on my icon it will say 'connecting to 'default' or 'linksys' depending up on the network I chose.  Other computers are connecting to the wireless network under DHCP.

After wlassistant fails to connect, '  Connection failed.   Would you like to review settings for this network?  '

I click yes, and it is on DHCP, I am vary new to linux and would like to know where to start.

The websites below are where I have started to look but was not sure what to do when it said the the drivers are already installed for Dapper  (Dapper by default installs rt2400, rt2500, and rt2570 driver modules. )

[http://doc.gwos.org/index.php/LinksysWireless](http://doc.gwos.org/index.php/LinksysWireless)

[http://doc.gwos.org/index.php/RalinkDrivers](http://doc.gwos.org/index.php/RalinkDrivers)

If it can see the wireless network card and the network just, fails on connection where do I start...


miller@obone:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz
          RTS thr:off   Fragment thr=2346 B

wlan0     IEEE 802.11g  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:11:95:74:14:C2  
          RTS thr:off   Fragment thr=2346 B

sit0      no wireless extensions.

acefx

---

### Post by siciliancasanova on 2007-03-13
what are your outputs for

lspci
iwlist
arp
netstat -nr

?

---

