---
title: "Wifi doesn't work on HP laptop"
date: 2018-08-30
forum: Arch and derivatives
---

### Post by tackskull on 2018-08-30
Hi there, I am not able to let wifi wrk on my laptop, can you guys help me?

---

### Post by chili555 on 2018-08-30
Please open a terminal and run and post:```
lspci -nnk | grep 0280 -A3
rfkill list all
```

---

### Post by tackskull on 2018-08-30
```
lspci -nnk | grep 0280 -A3
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Hewlett-Packard Company RTL8723BE PCIe Wireless Network Adapter [103c:804c]
    Kernel driver in use: rtl8723be
    Kernel modules: rtl8723be

```


rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by chili555 on 2018-08-30
Good news! Nothing wrong so far. Please show us:```
dmesg | grep -i rtl
dmesg | grep wl
```

---

### Post by tackskull on 2018-08-30
```
dmesg | grep -i rtl
[    7.802109] r8169 0000:03:00.0 eth0: RTL8106e at 0xffffafaac08f9000, fc:3f:db:a5:9e:ed, XID 04900000 IRQ 120
[    8.543511] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=8723
[    8.543516] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_config.bin
[    8.570588] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723b_config.bin failed with error -2
[    8.570596] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[    9.235424] rtl8723be: Using firmware rtlwifi/rtl8723befw_36.bin
[    9.252622] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    9.253214] rtlwifi: rtlwifi: wireless switch is on
[   10.193043] rtl8723be 0000:02:00.0 wlp2s0: renamed from wlan0
  
```


```
  
```
dmesg | grep wl
[   10.193043] rtl8723be 0000:02:00.0 wlp2s0: renamed from wlan0
[   16.033461] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   16.824875] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   17.347026] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   18.653363] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[  335.075933] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[  651.038340] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[  967.037649] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 1283.041655] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 1599.039274] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 1915.041292] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready

---

### Post by chili555 on 2018-08-30
Weird. Still nothing wrong! Let's see:```
cat /etc/NetworkManager/NetworkManager.conf
cat /etc/network/interfaces
```Also, does it scan?```
sudo iwlist wlp2s0 scan
```We needn't see the whole list, just tell us if it does or does not see networks.

When you click the Network Manager icon, do you see your network? What happens when you click on it and try to connect? Are you challenged for a password? Or what happens?

---

### Post by tackskull on 2018-08-30
Going on the network connection on the lower right part of the system I can see my wired connection but any of the wifi connections saying "Wifi connections disconnected" but if I right click "enable wifi is marked".
The commands you gave me are not working, maybe because I am using manjaro on this specific laptop?
Looking on the internet some people modified the [B]/etc/modprobe.d/rtl8723be.conf trying this options:

[/B]options rtl8723be fwlps=0 ant_sel=2 ips=0 swlps=0 swenc=1 disable_watchdog=1
options rtl8723be swenc=1 fwlps=0 ips=0

but any of this works (I am not good with pc stuff so don't really know what I am doing)

This is about your commands:

[CODE cat /etc/NetworkManager/NetworkManager.conf
# Configuration file for NetworkManager.
# See "man 5 NetworkManager.conf" for details.][/CODE]

```
cat /etc/network/interfaces
cat: /etc/network/interfaces: No such file or directory
```

```
sudo iwlist wlp2s0 scan
[sudo] password for tackskull: 
sudo: iwlist: command not found 
```

---

### Post by chili555 on 2018-08-30
>  maybe because I am using manjaro on this specific laptop?[https://manjaro.org/](https://manjaro.org/)

Manjaro is based on Arch. It has many, many differences from Ubuntu. I can offer no suggestions as I am unfamiliar with either Manjaro or Arch. Sorry.

---

### Post by tackskull on 2018-08-30
Oh sorry, thanks a lot for your time

---

### Post by wildmanne39 on 2018-08-30
*Thread moved to **Arch and derivatives for a more appropriate fit**.*

---

