---
title: "A solution for ADSL router detection in Gutsy"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by debajit on 2007-10-28
I am from Kolkata, India. My ISP is Tata Indicom. I am connected to it through ADSL modem and router. The connection is wired(ethernet). They support both PPPoE and RFC 1483 bridge. The network can be reached either through DHCP or ISP supplied IP-gateway-DNS configuration. My hardware configuration is AMD Sempron 64 bit, 256(240+16shared) MB DDR, 80 GB SATA with dual boot (Windows XP SP2 32 bit + Ubuntu 7.10 64 bit).
I am a noobish and faced a problem which I solved in my own way. I want to share it.


PROBLEM:
My initial OS was Windows. My on board LAN was inactivated after a nearby lightning. Now I use a Realtek based PCI ethernet card. I use PPPoE with ISP configurations. After I installed Gutsy 64 bit from alternate install CD, I could not get the internet to work on it with either DHCP, ISP configuration or roaming mode(what is roaming mode?). Neither could I access the router with the browser("problem loading page" was displayed). I tried ping with different IP addresses and domain names but it failed totally, although my LAN card was detected as eth0. I tried "sudo pppoeconf" at the terminal but it displayed PADO timeout(what is PADO?) and access concentrator failure(what is access concentrator?).

SOLUTION:
Finally I succeeded. At first I removed GRUB(by "fdisk /mbr" from Windows 98 start-up floppy). Next I removed the swap and ext3 partitions for Ubuntu from within Windows. Next I removed my LAN card from PCI slot. Then I made a fresh installation of Gutsy. Then I replaced the LAN card on the PCI slot and started Ubuntu, and voila, I could get to the router as well as internet in roaming mode by default, but then also by DHCP and ISP configuration on manual configuration.

P.S. - Please let me know if anyone faces a similar problem and can solve it by this method. Those who have on board LAN can try disabling it from BIOS before installing Ubuntu, and then enabling it from BIOS before booting to Ubuntu again.

---

