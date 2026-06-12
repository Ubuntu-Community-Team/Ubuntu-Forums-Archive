---
title: "Belkin USB adapter works until reboot"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by spittal on 2007-10-21
I am very new to Ubuntu and Linux. I could not get my Belkin USB adapter to work with Feisty Fawn but saw that the upgrade to Gutsy should do the trick. After upgrade I find that the USB adapter worked perfectly until I need to reboot. I then had to go to fiddle with system/administration/network. I found that if I enabled roaming mode and then disabled roaming mode again  the "upgrading network configuration" box pops up and I am back online. How do I make my computer remember. It works perfectly all day until I need to switch off and then its the same procedure again. I have read a few posts which I am afraid I dont fully understand. I have added output from a command suggested in another post. I hope someone can help.
Dave :)

 *-network               
       description: Ethernet interface
       product: RTL-8110SC/8169SC Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: eth0
       version: 10
       serial: 00:01:6c:18:7d:2f
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=64 maxlatency=64 mingnt=32 module=r8169 multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:17:3f:5f:c9:4e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.64 multicast=yes wireless=IEEE 802.11g

---

