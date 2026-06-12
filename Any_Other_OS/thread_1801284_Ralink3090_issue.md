---
title: "Ralink3090 issue"
date: 2011-07-10
forum: Any Other OS
---

### Post by Flexo82 on 2011-07-10
I have a problem with my Ralink3090 wifi on my Acer Aspire Revo running XBMCLive. I cant get it to work and i dont know what is wrong

**lcpci -v:**
```

05:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe
	Subsystem: Lite-On Communications Inc Device 6622
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at febf0000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/5 Enable-
	Capabilities: [70] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
        Capabilities: [140] Device Serial Number 70-f1-a1-9f-47-d0-00-00
	Kernel driver in use: rt2860
	Kernel modules: rt3090sta, rt2860sta

```

**ifconfig:**
```

eth0      Link encap:Ethernet  HWaddr 90:fb:a6:df:bd:b1  
          inet addr:192.168.0.180  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::92fb:a6ff:fedf:bdb1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:400 errors:0 dropped:0 overruns:0 frame:0
          TX packets:300 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:41582 (41.5 KB)  TX bytes:49820 (49.8 KB)
          Interrupt:23 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

**iwconfig:**
```
wlan0     Ralink STA  ESSID:""  
          Mode:Auto  Frequency=2.412 GHz  
          Link Quality=10/100  Signal level:0 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

**lshw -C network:**
```
  *-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: 90:fb:a6:df:bd:b1
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.0.180 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
       resources: irq:23 memory:fae7d000-fae7dfff ioport:d080(size=8) memory:fae7e800-fae7e8ff memory:fae7e400-fae7e40f
  *-network DISABLED
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=0 multicast=yes wireless=Ralink STA
       resources: irq:19 memory:febf0000-febfffff
```

**ifconfig wlan0 up**
```
SIOCSIFFLAGS: Operation not permitted
```

**dmesg | grep -i RT3**
```
[   11.210751] rt3090sta: disagrees about version of symbol module_layout
[   15.423379] rt2860 0000:05:00.0: firmware: requesting rt3090.bin
[   15.497851] rt2860 0000:05:00.0: firmware file rt3090.bin request failed (-2)
[   15.542273] rt2860 0000:05:00.0: firmware: requesting rt3090.bin
[   15.546729] rt2860 0000:05:00.0: firmware file rt3090.bin request failed (-2)
[   15.547189] rt2860 0000:05:00.0: firmware: requesting rt3090.bin
[   15.553500] rt2860 0000:05:00.0: firmware file rt3090.bin request failed (-2)
[  533.902765] rt2860 0000:05:00.0: firmware: requesting rt3090.bin
[  533.906309] rt2860 0000:05:00.0: firmware file rt3090.bin request failed (-2)
```

**dmesg | grep -i RT2**
```
[   15.232922] rt2860 0000:05:00.0: PCI INT A -> Link[LN4A] -> GSI 19 (level, low) -> IRQ 19
[   15.232974] rt2860 0000:05:00.0: setting latency timer to 64
[   15.423379] rt2860 0000:05:00.0: firmware: requesting rt3090.bin
[   15.497851] rt2860 0000:05:00.0: firmware file rt3090.bin request failed (-2)
[   15.497876] rt28xx Initialized fail!
[   15.542273] rt2860 0000:05:00.0: firmware: requesting rt3090.bin
[   15.546729] rt2860 0000:05:00.0: firmware file rt3090.bin request failed (-2)
[   15.546755] rt28xx Initialized fail!
[   15.547189] rt2860 0000:05:00.0: firmware: requesting rt3090.bin
[   15.553500] rt2860 0000:05:00.0: firmware file rt3090.bin request failed (-2)
[   15.553524] rt28xx Initialized fail!
[  533.902765] rt2860 0000:05:00.0: firmware: requesting rt3090.bin
[  533.906309] rt2860 0000:05:00.0: firmware file rt3090.bin request failed (-2)
[  533.906972] rt28xx Initialized fail!
```

Can anyone help me out here?

---

### Post by Flexo82 on 2011-07-10
A little update.

i blacklisted the rt2860sta module, however i cannot modprode the rt3090sta module i get the following error:

```

WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Error inserting rt3090sta (/lib/modules/2.6.32-32-generic/updates/dkms/rt3090sta.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

**dmesg | grep RT3**
```
[   11.433315] rt3090sta: module license 'unspecified' taints kernel.
[   11.433383] rt3090sta: disagrees about version of symbol filp_open
[   11.433388] rt3090sta: Unknown symbol filp_open
[   11.434045] rt3090sta: disagrees about version of symbol skb_put
[   11.434050] rt3090sta: Unknown symbol skb_put
[   11.434279] rt3090sta: disagrees about version of symbol __netif_schedule
[   11.434284] rt3090sta: Unknown symbol __netif_schedule
[   11.434577] rt3090sta: disagrees about version of symbol unregister_netdev
[   11.434582] rt3090sta: Unknown symbol unregister_netdev
[   11.435227] rt3090sta: disagrees about version of symbol pskb_expand_head
[   11.435232] rt3090sta: Unknown symbol pskb_expand_head
[   11.435245] rt3090sta: disagrees about version of symbol wake_up_process
[   11.435250] rt3090sta: Unknown symbol wake_up_process
[   11.435386] rt3090sta: disagrees about version of symbol eth_type_trans
[   11.435391] rt3090sta: Unknown symbol eth_type_trans
[   11.435642] rt3090sta: disagrees about version of symbol __alloc_skb
[   11.435647] rt3090sta: Unknown symbol __alloc_skb
[   11.435777] rt3090sta: disagrees about version of symbol netif_device_detach
[   11.435782] rt3090sta: Unknown symbol netif_device_detach
[   11.435944] rt3090sta: disagrees about version of symbol netif_device_attach
[   11.435949] rt3090sta: Unknown symbol netif_device_attach
[   11.436121] rt3090sta: disagrees about version of symbol skb_copy_expand
[   11.436126] rt3090sta: Unknown symbol skb_copy_expand
[   11.436570] rt3090sta: disagrees about version of symbol dev_kfree_skb_any
[   11.436575] rt3090sta: Unknown symbol dev_kfree_skb_any
[   11.436704] rt3090sta: disagrees about version of symbol skb_pull
[   11.436709] rt3090sta: Unknown symbol skb_pull
[   11.437025] rt3090sta: disagrees about version of symbol dev_close
[   11.437032] rt3090sta: Unknown symbol dev_close
[   11.437195] rt3090sta: disagrees about version of symbol skb_push
[   11.437201] rt3090sta: Unknown symbol skb_push
[   11.437428] rt3090sta: disagrees about version of symbol wireless_send_event
[   11.437433] rt3090sta: Unknown symbol wireless_send_event
[   11.437566] rt3090sta: disagrees about version of symbol register_netdev
[   11.437571] rt3090sta: Unknown symbol register_netdev
[   11.437842] rt3090sta: disagrees about version of symbol free_netdev
[   11.437847] rt3090sta: Unknown symbol free_netdev
[   11.438307] rt3090sta: disagrees about version of symbol dev_alloc_skb
[   11.438312] rt3090sta: Unknown symbol dev_alloc_skb
[   11.438447] rt3090sta: disagrees about version of symbol alloc_etherdev_mq
[   11.438452] rt3090sta: Unknown symbol alloc_etherdev_mq
[   11.438714] rt3090sta: disagrees about version of symbol netif_rx
[   11.438718] rt3090sta: Unknown symbol netif_rx
[   11.438918] rt3090sta: disagrees about version of symbol skb_trim
[   11.438923] rt3090sta: Unknown symbol skb_trim
[   11.439484] rt3090sta: disagrees about version of symbol filp_close
[   11.439489] rt3090sta: Unknown symbol filp_close
[   11.439624] rt3090sta: disagrees about version of symbol netif_carrier_off
[   11.439629] rt3090sta: Unknown symbol netif_carrier_off
[   11.439785] rt3090sta: disagrees about version of symbol skb_clone
[   11.439789] rt3090sta: Unknown symbol skb_clone
[   11.439922] rt3090sta: disagrees about version of symbol dev_get_by_name
[   11.439927] rt3090sta: Unknown symbol dev_get_by_name
[   11.440086] rt3090sta: disagrees about version of symbol netif_carrier_on
[   11.440091] rt3090sta: Unknown symbol netif_carrier_on
[   11.440994] rt3090sta: disagrees about version of symbol register_netdevice
[   11.440999] rt3090sta: Unknown symbol register_netdevice
[  129.717625] rt3090sta: disagrees about version of symbol filp_open
[  129.717640] rt3090sta: Unknown symbol filp_open
[  129.718330] rt3090sta: disagrees about version of symbol skb_put
[  129.718337] rt3090sta: Unknown symbol skb_put
[  129.718568] rt3090sta: disagrees about version of symbol __netif_schedule
[  129.718574] rt3090sta: Unknown symbol __netif_schedule
[  129.718866] rt3090sta: disagrees about version of symbol unregister_netdev
[  129.718871] rt3090sta: Unknown symbol unregister_netdev
[  129.719516] rt3090sta: disagrees about version of symbol pskb_expand_head
[  129.719522] rt3090sta: Unknown symbol pskb_expand_head
[  129.719535] rt3090sta: disagrees about version of symbol wake_up_process
[  129.719540] rt3090sta: Unknown symbol wake_up_process
[  129.719675] rt3090sta: disagrees about version of symbol eth_type_trans
[  129.719680] rt3090sta: Unknown symbol eth_type_trans
[  129.719932] rt3090sta: disagrees about version of symbol __alloc_skb
[  129.719937] rt3090sta: Unknown symbol __alloc_skb
[  129.720067] rt3090sta: disagrees about version of symbol netif_device_detach
[  129.720072] rt3090sta: Unknown symbol netif_device_detach
[  129.720234] rt3090sta: disagrees about version of symbol netif_device_attach
[  129.720239] rt3090sta: Unknown symbol netif_device_attach
[  129.720370] rt3090sta: disagrees about version of symbol skb_copy_expand
[  129.720375] rt3090sta: Unknown symbol skb_copy_expand
[  129.720818] rt3090sta: disagrees about version of symbol dev_kfree_skb_any
[  129.720824] rt3090sta: Unknown symbol dev_kfree_skb_any
[  129.720953] rt3090sta: disagrees about version of symbol skb_pull
[  129.720958] rt3090sta: Unknown symbol skb_pull
[  129.721319] rt3090sta: disagrees about version of symbol dev_close
[  129.721325] rt3090sta: Unknown symbol dev_close
[  129.721456] rt3090sta: disagrees about version of symbol skb_push
[  129.721461] rt3090sta: Unknown symbol skb_push
[  129.721694] rt3090sta: disagrees about version of symbol wireless_send_event
[  129.721699] rt3090sta: Unknown symbol wireless_send_event
[  129.721833] rt3090sta: disagrees about version of symbol register_netdev
[  129.721842] rt3090sta: Unknown symbol register_netdev
[  129.722118] rt3090sta: disagrees about version of symbol free_netdev
[  129.722124] rt3090sta: Unknown symbol free_netdev
[  129.722585] rt3090sta: disagrees about version of symbol dev_alloc_skb
[  129.722590] rt3090sta: Unknown symbol dev_alloc_skb
[  129.722726] rt3090sta: disagrees about version of symbol alloc_etherdev_mq
[  129.722732] rt3090sta: Unknown symbol alloc_etherdev_mq
[  129.722994] rt3090sta: disagrees about version of symbol netif_rx
[  129.722999] rt3090sta: Unknown symbol netif_rx
[  129.723199] rt3090sta: disagrees about version of symbol skb_trim
[  129.723204] rt3090sta: Unknown symbol skb_trim
[  129.723768] rt3090sta: disagrees about version of symbol filp_close
[  129.723773] rt3090sta: Unknown symbol filp_close
[  129.723908] rt3090sta: disagrees about version of symbol netif_carrier_off
[  129.723913] rt3090sta: Unknown symbol netif_carrier_off
[  129.724077] rt3090sta: disagrees about version of symbol skb_clone
[  129.724082] rt3090sta: Unknown symbol skb_clone
[  129.724215] rt3090sta: disagrees about version of symbol dev_get_by_name
[  129.724221] rt3090sta: Unknown symbol dev_get_by_name
[  129.724357] rt3090sta: disagrees about version of symbol netif_carrier_on
[  129.724363] rt3090sta: Unknown symbol netif_carrier_on
[  129.725298] rt3090sta: disagrees about version of symbol register_netdevice
[  129.725304] rt3090sta: Unknown symbol register_netdevice
[  438.962685] rt3090sta: disagrees about version of symbol cfg80211_scan_done
[  438.962698] rt3090sta: Unknown symbol cfg80211_scan_done
[  438.963765] rt3090sta: disagrees about version of symbol regulatory_hint
[  438.963773] rt3090sta: Unknown symbol regulatory_hint
[  438.964634] rt3090sta: disagrees about version of symbol wiphy_rfkill_set_hw_state
[  438.964640] rt3090sta: Unknown symbol wiphy_rfkill_set_hw_state
[  438.964881] rt3090sta: disagrees about version of symbol wiphy_register
[  438.964886] rt3090sta: Unknown symbol wiphy_register
[  438.965210] rt3090sta: disagrees about version of symbol wiphy_new
[  438.965215] rt3090sta: Unknown symbol wiphy_new
[  438.966544] rt3090sta: disagrees about version of symbol wiphy_rfkill_stop_polling
[  438.966550] rt3090sta: Unknown symbol wiphy_rfkill_stop_polling
[  438.967215] rt3090sta: disagrees about version of symbol cfg80211_connect_result
[  438.967221] rt3090sta: Unknown symbol cfg80211_connect_result
[  438.968093] rt3090sta: disagrees about version of symbol wiphy_unregister
[  438.968099] rt3090sta: Unknown symbol wiphy_unregister
[  438.969602] rt3090sta: disagrees about version of symbol wiphy_rfkill_start_polling
[  438.969608] rt3090sta: Unknown symbol wiphy_rfkill_start_polling
[  438.971172] rt3090sta: disagrees about version of symbol cfg80211_inform_bss_frame
[  438.971177] rt3090sta: Unknown symbol cfg80211_inform_bss_frame
[  438.972129] rt3090sta: disagrees about version of symbol wiphy_free
[  438.972135] rt3090sta: Unknown symbol wiphy_free

```

---

