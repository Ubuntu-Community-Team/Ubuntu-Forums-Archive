---
title: "~##Linksys Wireless-G Notebook Adapter##~~"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by watsgoodg on 2008-03-08
Hey Guys, 

I have a dell laptop with a wireless card (wpc54g) and im not sure how to get it to work.  I know in window s you just install the driver.  Any ideas?  Thanks. 

-J

---

### Post by anewguy on 2008-03-08
A Yahoo! search of:

ubuntu wpc54g

turns up many responses.  I'm posting the link to one of them here:

[http://www.pinoy-compuworld.com/workstations/ubuntu-linux/setup-a-linksys-wpc54g-v3-card-on-ubuntu-linux/]("http://www.pinoy-compuworld.com/workstations/ubuntu-linux/setup-a-linksys-wpc54g-v3-card-on-ubuntu-linux/")

:)

---

### Post by abn91c on 2008-03-08
follow the directions here, the deb file works with my inspiron 1000 and linksys wireless g card just fine

---

### Post by abn91c on 2008-03-08
oops forgot the link:  [http://ubuntuforums.org/showthread.php?t=197102&highlight=compwiz](http://ubuntuforums.org/showthread.php?t=197102&highlight=compwiz)

---

### Post by gubaidullin on 2008-03-11
I've got problems with Linksys WPC54G ver.3.1 PCMCIA Wireless adapter.
It works in managed mode with WPA encryption.
But I cannot get it working in Ad-Hoc mode with WEP Encryption
Here's a part of syslog
```

Mar 10 18:15:45 u7-n1020v-grr kernel: [  120.296000] pccard: CardBus card inserted into slot 0
Mar 10 18:15:45 u7-n1020v-grr kernel: [  120.296000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
Mar 10 18:15:45 u7-n1020v-grr kernel: [  120.296000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNK2] -> GSI 10 (level, low) -> IRQ 10
Mar 10 18:15:45 u7-n1020v-grr kernel: [  120.296000] PCI: Setting latency timer of device 0000:02:00.0 to 64
Mar 10 18:15:46 u7-n1020v-grr NetworkManager: <info>  eth1: Device is fully-supported using driver 'bcm43xx'. 
Mar 10 18:15:46 u7-n1020v-grr NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Mar 10 18:15:46 u7-n1020v-grr NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Mar 10 18:15:46 u7-n1020v-grr NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Mar 10 18:15:46 u7-n1020v-grr NetworkManager: <info>  Deactivating device eth1. 
Mar 10 18:15:56 u7-n1020v-grr NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Mar 10 18:15:56 u7-n1020v-grr dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Mar 10 18:15:56 u7-n1020v-grr NetworkManager: <info>  Will activate connection 'eth1/*'. 
Mar 10 18:15:56 u7-n1020v-grr NetworkManager: <info>  Device eth1 activation scheduled... 
Mar 10 18:15:56 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) started... 
Mar 10 18:15:56 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Mar 10 18:15:56 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Mar 10 18:15:56 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Mar 10 18:15:56 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Mar 10 18:15:56 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Mar 10 18:15:56 u7-n1020v-grr NetworkManager: <info>  Activation (eth1/wireless): access point '*' is encrypted, but NO valid key exists.  New key needed. 
Mar 10 18:15:56 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) New wireless user key requested for network '*'. 
Mar 10 18:15:56 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Mar 10 18:15:56 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) New wireless user key for network '*' received. 
Mar 10 18:15:56 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Mar 10 18:15:56 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Mar 10 18:15:56 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Mar 10 18:15:56 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Mar 10 18:15:56 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Mar 10 18:15:56 u7-n1020v-grr NetworkManager: <info>  Activation (eth1/wireless): access point '*' is encrypted, and a key exists.  No new key needed. 
Mar 10 18:15:57 u7-n1020v-grr NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Mar 10 18:15:57 u7-n1020v-grr NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Mar 10 18:15:57 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant3^I' 
Mar 10 18:15:57 u7-n1020v-grr kernel: [  132.284000] NET: Registered protocol family 17
Mar 10 18:15:57 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:15:57 u7-n1020v-grr NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Mar 10 18:15:57 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'AP_SCAN 2' 
Mar 10 18:15:57 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:15:57 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Mar 10 18:15:57 u7-n1020v-grr NetworkManager: <info>  SUP: response was '0' 
Mar 10 18:15:57 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 2a' 
Mar 10 18:15:57 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:15:57 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 mode 1' 
Mar 10 18:15:57 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:15:57 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Mar 10 18:15:57 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:15:57 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 auth_alg SHARED' 
Mar 10 18:15:57 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:15:57 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Mar 10 18:15:57 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:15:57 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Mar 10 18:15:57 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:15:57 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Mar 10 18:15:57 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:15:57 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Mar 10 18:15:57 u7-n1020v-grr kernel: [  132.428000] ieee80211_crypt: registered algorithm 'WEP'
Mar 10 18:16:39 u7-n1020v-grr NetworkManager: <debug> [1205165799.643947] nm_device_802_11_wireless_get_activation_ap(): Forcing AP '*' 
Mar 10 18:16:39 u7-n1020v-grr NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/eth1 / * 
Mar 10 18:16:39 u7-n1020v-grr NetworkManager: <info>  Deactivating device eth1. 
Mar 10 18:16:39 u7-n1020v-grr NetworkManager: <info>  Activation (eth1): cancelling... 
Mar 10 18:16:39 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) cancellation handler scheduled... 
Mar 10 18:16:39 u7-n1020v-grr NetworkManager: <info>  Activation (eth1): waiting for device to cancel activation. 
Mar 10 18:16:39 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) cancellation handled. 
Mar 10 18:16:39 u7-n1020v-grr NetworkManager: <info>  Activation (eth1): cancelled. 
Mar 10 18:16:39 u7-n1020v-grr dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Mar 10 18:16:39 u7-n1020v-grr NetworkManager: <info>  Device eth1 activation scheduled... 
Mar 10 18:16:39 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) started... 
Mar 10 18:16:39 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Mar 10 18:16:39 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Mar 10 18:16:39 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Mar 10 18:16:39 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Mar 10 18:16:39 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Mar 10 18:16:39 u7-n1020v-grr NetworkManager: <info>  Activation (eth1/wireless): access point '*' is encrypted, but NO valid key exists.  New key needed. 
Mar 10 18:16:39 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) New wireless user key requested for network '*'. 
Mar 10 18:16:39 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Mar 10 18:16:39 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) New wireless user key for network '*' received. 
Mar 10 18:16:39 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Mar 10 18:16:39 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Mar 10 18:16:39 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Mar 10 18:16:39 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Mar 10 18:16:39 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Mar 10 18:16:39 u7-n1020v-grr NetworkManager: <info>  Activation (eth1/wireless): access point '*' is encrypted, and a key exists.  No new key needed. 
Mar 10 18:16:40 u7-n1020v-grr NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Mar 10 18:16:40 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant6^I' 
Mar 10 18:16:41 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:16:41 u7-n1020v-grr NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Mar 10 18:16:41 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'AP_SCAN 2' 
Mar 10 18:16:41 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:16:41 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Mar 10 18:16:41 u7-n1020v-grr NetworkManager: <info>  SUP: response was '0' 
Mar 10 18:16:41 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 2a' 
Mar 10 18:16:41 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:16:41 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 mode 1' 
Mar 10 18:16:41 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:16:41 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Mar 10 18:16:41 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:16:41 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 auth_alg SHARED' 
Mar 10 18:16:41 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:16:41 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Mar 10 18:16:41 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:16:41 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Mar 10 18:16:41 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:16:41 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Mar 10 18:16:41 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:16:41 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Mar 10 18:16:46 u7-n1020v-grr NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Mar 10 18:17:01 u7-n1020v-grr /USR/SBIN/CRON[5933]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 10 18:17:37 u7-n1020v-grr dhclient: isc-dhclient-V3.0.5
Mar 10 18:17:41 u7-n1020v-grr NetworkManager: <info>  Activation (eth1/wireless): association took too long (>60s), failing activation. 
Mar 10 18:17:41 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) failure scheduled... 
Mar 10 18:17:41 u7-n1020v-grr kernel: [  236.024000] SoftMAC: Authentication timed out with 52:70:a3:46:7f:26
Mar 10 18:17:41 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) failed for access point (*) 
Mar 10 18:17:41 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) failed. 
Mar 10 18:17:41 u7-n1020v-grr NetworkManager: <info>  Deactivating device eth1. 
Mar 10 18:17:47 u7-n1020v-grr dhclient: Internet Systems Consortium DHCP Client V3.0.5
Mar 10 18:17:47 u7-n1020v-grr dhclient: Copyright 2004-2006 Internet Systems Consortium.
Mar 10 18:17:47 u7-n1020v-grr dhclient: All rights reserved.
Mar 10 18:17:47 u7-n1020v-grr dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Mar 10 18:17:47 u7-n1020v-grr dhclient: 
Mar 10 18:17:48 u7-n1020v-grr dhclient: Listening on LPF/eth1/00:18:f8:63:9b:83
Mar 10 18:17:48 u7-n1020v-grr dhclient: Sending on   LPF/eth1/00:18:f8:63:9b:83
Mar 10 18:17:48 u7-n1020v-grr dhclient: Sending on   Socket/fallback
Mar 10 18:17:48 u7-n1020v-grr dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Mar 10 18:17:55 u7-n1020v-grr dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Mar 10 18:18:05 u7-n1020v-grr dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Mar 10 18:18:13 u7-n1020v-grr dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Mar 10 18:18:46 u7-n1020v-grr kernel: [  301.660000] SoftMAC: Authentication timed out with 52:70:a3:46:7f:26
Mar 10 18:18:53 u7-n1020v-grr dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134519120
Mar 10 18:18:53 u7-n1020v-grr dhclient: Internet Systems Consortium DHCP Client V3.0.5
Mar 10 18:18:53 u7-n1020v-grr dhclient: Copyright 2004-2006 Internet Systems Consortium.
Mar 10 18:18:53 u7-n1020v-grr dhclient: All rights reserved.
Mar 10 18:18:53 u7-n1020v-grr dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Mar 10 18:18:53 u7-n1020v-grr dhclient: 
Mar 10 18:18:53 u7-n1020v-grr dhclient: Listening on LPF/eth1/00:18:f8:63:9b:83
Mar 10 18:18:53 u7-n1020v-grr dhclient: Sending on   LPF/eth1/00:18:f8:63:9b:83
Mar 10 18:18:53 u7-n1020v-grr dhclient: Listening on LPF/eth0/00:0b:cd:5d:58:e0
Mar 10 18:18:53 u7-n1020v-grr dhclient: Sending on   LPF/eth0/00:0b:cd:5d:58:e0
Mar 10 18:18:53 u7-n1020v-grr dhclient: Sending on   Socket/fallback
Mar 10 18:18:53 u7-n1020v-grr dhclient: Internet Systems Consortium DHCP Client V3.0.5
Mar 10 18:18:53 u7-n1020v-grr dhclient: Copyright 2004-2006 Internet Systems Consortium.
Mar 10 18:18:53 u7-n1020v-grr dhclient: All rights reserved.
Mar 10 18:18:53 u7-n1020v-grr dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Mar 10 18:18:53 u7-n1020v-grr dhclient: 
Mar 10 18:18:54 u7-n1020v-grr dhclient: Listening on LPF/eth1/00:18:f8:63:9b:83
Mar 10 18:18:54 u7-n1020v-grr dhclient: Sending on   LPF/eth1/00:18:f8:63:9b:83
Mar 10 18:18:54 u7-n1020v-grr dhclient: Sending on   Socket/fallback
Mar 10 18:18:54 u7-n1020v-grr dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Mar 10 18:19:01 u7-n1020v-grr dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
Mar 10 18:19:10 u7-n1020v-grr dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
Mar 10 18:19:23 u7-n1020v-grr dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Mar 10 18:19:53 u7-n1020v-grr kernel: [  368.572000] SoftMAC: Authentication timed out with 52:70:a3:46:7f:26
Mar 10 18:20:38 u7-n1020v-grr NetworkManager: <debug> [1205166038.775424] nm_device_802_11_wireless_get_activation_ap(): Forcing AP '*' 
Mar 10 18:20:38 u7-n1020v-grr NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/eth1 / * 
Mar 10 18:20:38 u7-n1020v-grr NetworkManager: <info>  Deactivating device eth1. 
Mar 10 18:20:38 u7-n1020v-grr dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Mar 10 18:20:38 u7-n1020v-grr NetworkManager: <info>  Device eth1 activation scheduled... 
Mar 10 18:20:38 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) started... 
Mar 10 18:20:38 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Mar 10 18:20:38 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Mar 10 18:20:38 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Mar 10 18:20:38 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Mar 10 18:20:38 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Mar 10 18:20:38 u7-n1020v-grr NetworkManager: <info>  Activation (eth1/wireless): access point '*' is encrypted, and a key exists.  No new key needed. 
Mar 10 18:20:39 u7-n1020v-grr NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Mar 10 18:20:39 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant9^I' 
Mar 10 18:20:39 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:20:39 u7-n1020v-grr NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Mar 10 18:20:40 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'AP_SCAN 2' 
Mar 10 18:20:40 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:20:40 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Mar 10 18:20:40 u7-n1020v-grr NetworkManager: <info>  SUP: response was '0' 
Mar 10 18:20:40 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 2a' 
Mar 10 18:20:40 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:20:40 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 mode 1' 
Mar 10 18:20:40 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:20:40 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Mar 10 18:20:40 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:20:40 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 auth_alg SHARED' 
Mar 10 18:20:40 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:20:40 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Mar 10 18:20:40 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:20:40 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Mar 10 18:20:40 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:20:40 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Mar 10 18:20:40 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:20:40 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Mar 10 18:20:45 u7-n1020v-grr NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Mar 10 18:20:46 u7-n1020v-grr NetworkManager: <debug> [1205166046.081719] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 9E:27:B1:46:77:6D to 52:70:A3:46:7F:26 on wireless network '*' 
Mar 10 18:20:46 u7-n1020v-grr NetworkManager: <debug> [1205166046.131699] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network '*' 
Mar 10 18:20:46 u7-n1020v-grr NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Mar 10 18:21:40 u7-n1020v-grr NetworkManager: <info>  Activation (eth1/wireless): association took too long (>60s), failing activation. 
Mar 10 18:21:40 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) failure scheduled... 
Mar 10 18:21:40 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) failed for access point (*) 
Mar 10 18:21:40 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) failed. 
Mar 10 18:21:40 u7-n1020v-grr NetworkManager: <info>  Deactivating device eth1. 
Mar 10 18:21:40 u7-n1020v-grr kernel: [  475.188000] SoftMAC: Authentication timed out with 52:70:a3:46:7f:26
Mar 10 18:22:02 u7-n1020v-grr NetworkManager: <debug> [1205166122.852132] nm_device_802_11_wireless_get_activation_ap(): Forcing AP '*' 
Mar 10 18:22:02 u7-n1020v-grr NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/eth1 / * 
Mar 10 18:22:02 u7-n1020v-grr NetworkManager: <info>  Deactivating device eth1. 
Mar 10 18:22:02 u7-n1020v-grr dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Mar 10 18:22:02 u7-n1020v-grr NetworkManager: <info>  Device eth1 activation scheduled... 
Mar 10 18:22:02 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) started... 
Mar 10 18:22:02 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Mar 10 18:22:02 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Mar 10 18:22:02 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Mar 10 18:22:02 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Mar 10 18:22:02 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Mar 10 18:22:02 u7-n1020v-grr NetworkManager: <info>  Activation (eth1/wireless): access point '*' is encrypted, but NO valid key exists.  New key needed. 
Mar 10 18:22:02 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) New wireless user key requested for network '*'. 
Mar 10 18:22:02 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Mar 10 18:22:02 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) New wireless user key for network '*' received. 
Mar 10 18:22:02 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Mar 10 18:22:02 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Mar 10 18:22:02 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Mar 10 18:22:02 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Mar 10 18:22:02 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Mar 10 18:22:02 u7-n1020v-grr NetworkManager: <info>  Activation (eth1/wireless): access point '*' is encrypted, and a key exists.  No new key needed. 
Mar 10 18:22:04 u7-n1020v-grr NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Mar 10 18:22:04 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant3^I' 
Mar 10 18:22:04 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:22:04 u7-n1020v-grr NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Mar 10 18:22:04 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'AP_SCAN 2' 
Mar 10 18:22:04 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:22:04 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Mar 10 18:22:04 u7-n1020v-grr NetworkManager: <info>  SUP: response was '0' 
Mar 10 18:22:04 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 2a' 
Mar 10 18:22:04 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:22:04 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 mode 1' 
Mar 10 18:22:04 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:22:04 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Mar 10 18:22:04 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:22:04 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 auth_alg SHARED' 
Mar 10 18:22:04 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:22:04 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Mar 10 18:22:04 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:22:04 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Mar 10 18:22:04 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:22:04 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Mar 10 18:22:04 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:22:04 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Mar 10 18:22:06 u7-n1020v-grr NetworkManager: <debug> [1205166126.405661] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 52:70:A3:46:7F:26 to 9E:27:B1:46:77:6D on wireless network '*' 
Mar 10 18:22:06 u7-n1020v-grr NetworkManager: <debug> [1205166126.467080] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network '*' 
Mar 10 18:22:06 u7-n1020v-grr NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Mar 10 18:22:06 u7-n1020v-grr NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Mar 10 18:22:08 u7-n1020v-grr NetworkManager: <debug> [1205166128.405909] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID BE:B3:B0:46:B7:11 to 9E:27:B1:46:77:6D on wireless network '*' 
Mar 10 18:22:08 u7-n1020v-grr NetworkManager: <debug> [1205166128.412039] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network '*' 
Mar 10 18:22:08 u7-n1020v-grr NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Mar 10 18:23:04 u7-n1020v-grr NetworkManager: <info>  Activation (eth1/wireless): association took too long (>60s), failing activation. 
Mar 10 18:23:04 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) failure scheduled... 
Mar 10 18:23:04 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) failed for access point (*) 
Mar 10 18:23:04 u7-n1020v-grr NetworkManager: <info>  Activation (eth1) failed. 
Mar 10 18:23:04 u7-n1020v-grr NetworkManager: <info>  Deactivating device eth1. 
Mar 10 18:23:04 u7-n1020v-grr kernel: [  559.336000] SoftMAC: Authentication timed out with 9e:27:b1:46:77:6d
Mar 10 18:30:20 u7-n1020v-grr kernel: [  995.528000] pccard: card ejected from slot 0

```

The only way I could connect to wireless network was inserting Cisco Aironet 350 PCMCIA - and connection was established at once.
Here's a part of syslog (Cisco Aironet 350)
```

Mar 10 18:30:35 u7-n1020v-grr kernel: [ 1010.376000] pccard: PCMCIA card inserted into slot 0
Mar 10 18:30:35 u7-n1020v-grr kernel: [ 1010.376000] cs: memory probe 0xa0000000-0xa0ffffff: clean.
Mar 10 18:30:35 u7-n1020v-grr kernel: [ 1010.380000] pcmcia: registering new device pcmcia0.0
Mar 10 18:30:35 u7-n1020v-grr kernel: [ 1010.472000] airo(): Probing for PCI adapters
Mar 10 18:30:35 u7-n1020v-grr kernel: [ 1010.476000] airo(): Finished probing for PCI adapters
Mar 10 18:30:37 u7-n1020v-grr kernel: [ 1011.672000] airo(eth1): cmd:111 status:7f11 rsp0:2 rsp1:0 rsp2:0
Mar 10 18:30:37 u7-n1020v-grr kernel: [ 1011.672000] airo(eth1): Doing fast bap_reads
Mar 10 18:30:37 u7-n1020v-grr NetworkManager: <debug> [1205166637.090068] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pcmcia__1__1'). 
Mar 10 18:30:37 u7-n1020v-grr NetworkManager: <debug> [1205166637.112058] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_0d_ed_c3_98_0a'). 
Mar 10 18:30:37 u7-n1020v-grr NetworkManager: <info>  eth2: Device is fully-supported using driver 'airo_cs'. 
Mar 10 18:30:37 u7-n1020v-grr NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Mar 10 18:30:37 u7-n1020v-grr kernel: [ 1011.788000] airo(eth1): WPA unsupported (only firmware versions 5.30.17 and greater support WPA.  Detected 5.02.19)
Mar 10 18:30:37 u7-n1020v-grr kernel: [ 1011.796000] airo(eth1): MAC enabled 0:d:ed:c3:98:a
Mar 10 18:30:37 u7-n1020v-grr kernel: [ 1011.796000] eth1: index 0x05: , Vpp 5.0, irq 3, io 0x0100-0x013f
Mar 10 18:30:37 u7-n1020v-grr NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Mar 10 18:30:37 u7-n1020v-grr NetworkManager: <info>  Now managing wireless (802.11) device 'eth2'. 
Mar 10 18:30:37 u7-n1020v-grr NetworkManager: <info>  Deactivating device eth2. 
Mar 10 18:30:51 u7-n1020v-grr NetworkManager: <debug> [1205166650.934024] nm_device_802_11_wireless_get_activation_ap(): Forcing AP '*' 
Mar 10 18:30:51 u7-n1020v-grr NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/eth2 / * 
Mar 10 18:30:51 u7-n1020v-grr NetworkManager: <info>  Deactivating device eth2. 
Mar 10 18:30:51 u7-n1020v-grr dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth2 for sub-path eth2.dbus.get.reason
Mar 10 18:30:51 u7-n1020v-grr NetworkManager: <info>  Device eth2 activation scheduled... 
Mar 10 18:30:51 u7-n1020v-grr NetworkManager: <info>  Activation (eth2) started... 
Mar 10 18:30:51 u7-n1020v-grr NetworkManager: <info>  Activation (eth2) Stage 1 of 5 (Device Prepare) scheduled... 
Mar 10 18:30:51 u7-n1020v-grr NetworkManager: <info>  Activation (eth2) Stage 1 of 5 (Device Prepare) started... 
Mar 10 18:30:51 u7-n1020v-grr NetworkManager: <info>  Activation (eth2) Stage 2 of 5 (Device Configure) scheduled... 
Mar 10 18:30:51 u7-n1020v-grr NetworkManager: <info>  Activation (eth2) Stage 1 of 5 (Device Prepare) complete. 
Mar 10 18:30:51 u7-n1020v-grr NetworkManager: <info>  Activation (eth2) Stage 2 of 5 (Device Configure) starting... 
Mar 10 18:30:51 u7-n1020v-grr NetworkManager: <info>  Activation (eth2/wireless): access point '*' is encrypted, but NO valid key exists.  New key needed. 
Mar 10 18:30:51 u7-n1020v-grr NetworkManager: <info>  Activation (eth2) New wireless user key requested for network '*'. 
Mar 10 18:30:51 u7-n1020v-grr NetworkManager: <info>  Activation (eth2) Stage 2 of 5 (Device Configure) complete. 
Mar 10 18:30:51 u7-n1020v-grr NetworkManager: <info>  Activation (eth2) New wireless user key for network '*' received. 
Mar 10 18:30:51 u7-n1020v-grr NetworkManager: <info>  Activation (eth2) Stage 1 of 5 (Device Prepare) scheduled... 
Mar 10 18:30:51 u7-n1020v-grr NetworkManager: <info>  Activation (eth2) Stage 1 of 5 (Device Prepare) started... 
Mar 10 18:30:51 u7-n1020v-grr NetworkManager: <info>  Activation (eth2) Stage 2 of 5 (Device Configure) scheduled... 
Mar 10 18:30:51 u7-n1020v-grr NetworkManager: <info>  Activation (eth2) Stage 1 of 5 (Device Prepare) complete. 
Mar 10 18:30:51 u7-n1020v-grr NetworkManager: <info>  Activation (eth2) Stage 2 of 5 (Device Configure) starting... 
Mar 10 18:30:51 u7-n1020v-grr NetworkManager: <info>  Activation (eth2/wireless): access point '*' is encrypted, and a key exists.  No new key needed. 
Mar 10 18:30:52 u7-n1020v-grr NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Mar 10 18:30:52 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth2^I^Iwext^I/var/run/wpa_supplicant4^I' 
Mar 10 18:30:53 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:30:53 u7-n1020v-grr NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Mar 10 18:30:53 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'AP_SCAN 2' 
Mar 10 18:30:53 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:30:53 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Mar 10 18:30:53 u7-n1020v-grr NetworkManager: <info>  SUP: response was '0' 
Mar 10 18:30:53 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 2a' 
Mar 10 18:30:53 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:30:53 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 mode 1' 
Mar 10 18:30:53 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:30:53 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Mar 10 18:30:53 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:30:53 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 auth_alg SHARED' 
Mar 10 18:30:53 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:30:53 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Mar 10 18:30:53 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:30:53 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Mar 10 18:30:53 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:30:53 u7-n1020v-grr NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Mar 10 18:30:53 u7-n1020v-grr NetworkManager: <info>  SUP: response was 'OK' 
Mar 10 18:30:53 u7-n1020v-grr NetworkManager: <info>  Activation (eth2) Stage 2 of 5 (Device Configure) complete. 
Mar 10 18:30:54 u7-n1020v-grr kernel: [ 1029.152000] airo(eth2): cmd:1 status:7f01 rsp0:8c rsp1:ff11 rsp2:b
Mar 10 18:30:54 u7-n1020v-grr kernel: [ 1029.152000] airo(eth2): cmd:2 status:7f02 rsp0:0 rsp1:ff11 rsp2:b
Mar 10 18:30:54 u7-n1020v-grr NetworkManager: <info>  Activation (eth2/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point '*'. 
Mar 10 18:30:54 u7-n1020v-grr NetworkManager: <info>  Activation (eth2) Stage 3 of 5 (IP Configure Start) scheduled. 
Mar 10 18:30:54 u7-n1020v-grr NetworkManager: <info>  Activation (eth2) Stage 3 of 5 (IP Configure Start) started... 
Mar 10 18:30:55 u7-n1020v-grr NetworkManager: <info>  Activation (eth2) Beginning DHCP transaction. 
Mar 10 18:30:55 u7-n1020v-grr NetworkManager: <info>  Activation (eth2) Stage 3 of 5 (IP Configure Start) complete. 
Mar 10 18:30:55 u7-n1020v-grr NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth2 
Mar 10 18:30:55 u7-n1020v-grr dhclient: wifi0: unknown hardware address type 801
Mar 10 18:30:56 u7-n1020v-grr NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth2 
Mar 10 18:30:56 u7-n1020v-grr dhclient: wifi0: unknown hardware address type 801
Mar 10 18:30:56 u7-n1020v-grr dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 8
Mar 10 18:31:04 u7-n1020v-grr dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 8
Mar 10 18:31:04 u7-n1020v-grr dhclient: DHCPOFFER from 192.168.0.1
Mar 10 18:31:04 u7-n1020v-grr dhclient: DHCPREQUEST on eth2 to 255.255.255.255 port 67
Mar 10 18:31:05 u7-n1020v-grr dhclient: DHCPACK from 192.168.0.1
Mar 10 18:31:05 u7-n1020v-grr avahi-daemon[4995]: Joining mDNS multicast group on interface eth2.IPv4 with address 192.168.0.225.
Mar 10 18:31:05 u7-n1020v-grr avahi-daemon[4995]: New relevant interface eth2.IPv4 for mDNS.
Mar 10 18:31:05 u7-n1020v-grr avahi-daemon[4995]: Registering new address record for 192.168.0.225 on eth2.IPv4.
Mar 10 18:31:05 u7-n1020v-grr NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth2 
Mar 10 18:31:05 u7-n1020v-grr NetworkManager: <info>  Activation (eth2) Stage 4 of 5 (IP Configure Get) scheduled... 
Mar 10 18:31:05 u7-n1020v-grr NetworkManager: <info>  Activation (eth2) Stage 4 of 5 (IP Configure Get) started... 
Mar 10 18:31:05 u7-n1020v-grr dhclient: bound to 192.168.0.225 -- renewal in 285 seconds.
Mar 10 18:31:05 u7-n1020v-grr dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth2 for sub-path eth2.dbus.get.host_name
Mar 10 18:31:05 u7-n1020v-grr dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth2 for sub-path eth2.dbus.get.nis_domain
Mar 10 18:31:05 u7-n1020v-grr dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth2 for sub-path eth2.dbus.get.nis_servers
Mar 10 18:31:05 u7-n1020v-grr NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Mar 10 18:31:05 u7-n1020v-grr NetworkManager: <info>    address 192.168.0.225 
Mar 10 18:31:05 u7-n1020v-grr NetworkManager: <info>    netmask 255.255.255.0 
Mar 10 18:31:05 u7-n1020v-grr NetworkManager: <info>    broadcast 192.168.0.255 
Mar 10 18:31:05 u7-n1020v-grr NetworkManager: <info>    gateway 192.168.0.1 
Mar 10 18:31:05 u7-n1020v-grr NetworkManager: <info>    nameserver 192.168.0.1 
Mar 10 18:31:05 u7-n1020v-grr NetworkManager: <info>    domain name 'mshome.net' 
Mar 10 18:31:05 u7-n1020v-grr NetworkManager: <info>  Activation (eth2) Stage 5 of 5 (IP Configure Commit) scheduled... 
Mar 10 18:31:05 u7-n1020v-grr NetworkManager: <info>  Activation (eth2) Stage 4 of 5 (IP Configure Get) complete. 
Mar 10 18:31:05 u7-n1020v-grr NetworkManager: <info>  Activation (eth2) Stage 5 of 5 (IP Configure Commit) started... 
Mar 10 18:31:05 u7-n1020v-grr avahi-daemon[4995]: Withdrawing address record for 192.168.0.225 on eth2.
Mar 10 18:31:05 u7-n1020v-grr avahi-daemon[4995]: Leaving mDNS multicast group on interface eth2.IPv4 with address 192.168.0.225.
Mar 10 18:31:05 u7-n1020v-grr avahi-daemon[4995]: Interface eth2.IPv4 no longer relevant for mDNS.
Mar 10 18:31:05 u7-n1020v-grr avahi-daemon[4995]: Joining mDNS multicast group on interface eth2.IPv4 with address 192.168.0.225.
Mar 10 18:31:05 u7-n1020v-grr avahi-daemon[4995]: New relevant interface eth2.IPv4 for mDNS.
Mar 10 18:31:05 u7-n1020v-grr avahi-daemon[4995]: Registering new address record for 192.168.0.225 on eth2.IPv4.
Mar 10 18:31:06 u7-n1020v-grr NetworkManager: <info>  Clearing nscd hosts cache. 
Mar 10 18:31:06 u7-n1020v-grr NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Mar 10 18:31:06 u7-n1020v-grr NetworkManager: <info>  Activation (eth2) successful, device activated. 
Mar 10 18:31:06 u7-n1020v-grr NetworkManager: <info>  Activation (eth2) Finish handler scheduled. 
Mar 10 18:31:06 u7-n1020v-grr NetworkManager: <info>  Activation (eth2) Stage 5 of 5 (IP Configure Commit) complete. 
Mar 10 18:31:06 u7-n1020v-grr NetworkManager: <debug> [1205166666.851312] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network '*' 
Mar 10 18:31:07 u7-n1020v-grr kernel: [ 1041.752000] NET: Registered protocol family 10
Mar 10 18:31:07 u7-n1020v-grr kernel: [ 1041.752000] lo: Disabled Privacy Extensions
Mar 10 18:31:07 u7-n1020v-grr kernel: [ 1041.752000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar 10 18:31:07 u7-n1020v-grr ntpdate[8270]: adjust time server 91.189.94.4 offset -0.277629 sec
Mar 10 18:31:08 u7-n1020v-grr avahi-daemon[4995]: Registering new address record for fe80::20d:edff:fec3:980a on eth2.*.
Mar 10 18:31:17 u7-n1020v-grr kernel: [ 1052.100000] eth2: no IPv6 routers present
Mar 10 18:35:50 u7-n1020v-grr dhclient: DHCPREQUEST on eth2 to 192.168.0.1 port 67
Mar 10 18:35:50 u7-n1020v-grr dhclient: DHCPACK from 192.168.0.1
Mar 10 18:35:50 u7-n1020v-grr NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth2 
Mar 10 18:35:50 u7-n1020v-grr dhclient: bound to 192.168.0.225 -- renewal in 286 seconds.

```

Any help is appreciated.

---

