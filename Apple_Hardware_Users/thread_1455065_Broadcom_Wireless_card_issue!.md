---
title: "Broadcom Wireless card issue?!?"
date: 2010-04-15
forum: Apple Hardware Users
---

### Post by kwiksand on 2010-04-15
Hi guys, 

I seem to be have issues periodically connecting to wireless networks with WPA.  It'll work one minute, and then I switch my macbook back on after a period and it refuses to connect again.  It's happened on and off on three different networks now.

An example of /var/log/syslog:
```
Apr 15 17:57:27 macbookpro NetworkManager: <info>  Activation (eth1/wireless): association took too long.
Apr 15 17:57:27 macbookpro NetworkManager: <info>  (eth1): device state change: 5 -> 6 (reason 0)
Apr 15 17:57:27 macbookpro NetworkManager: <info>  Activation (eth1/wireless): asking for new secrets
Apr 15 17:57:27 macbookpro NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Apr 15 17:57:27 macbookpro NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Apr 15 17:57:27 macbookpro NetworkManager: <info>  (eth1): device state change: 6 -> 4 (reason 0)
Apr 15 17:57:27 macbookpro NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Apr 15 17:57:27 macbookpro NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Apr 15 17:57:27 macbookpro NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Apr 15 17:57:27 macbookpro NetworkManager: <info>  (eth1): device state change: 4 -> 5 (reason 0)
Apr 15 17:57:27 macbookpro NetworkManager: <info>  Activation (eth1/wireless): connection 'Auto QuidcoLon' has security, and secrets exist.  No new secrets needed.
Apr 15 17:57:27 macbookpro NetworkManager: <info>  Config: added 'ssid' value 'QuidcoLon'
Apr 15 17:57:27 macbookpro NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Apr 15 17:57:27 macbookpro NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Apr 15 17:57:27 macbookpro NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Apr 15 17:57:27 macbookpro NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Apr 15 17:57:27 macbookpro NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Apr 15 17:57:27 macbookpro NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Apr 15 17:57:27 macbookpro NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> disconnected
Apr 15 17:57:27 macbookpro NetworkManager: <info>  Config: set interface ap_scan to 1
Apr 15 17:57:27 macbookpro NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Apr 15 17:57:42 macbookpro NetworkManager: <info>  eth1: link timed out.
Apr 15 17:58:27 macbookpro NetworkManager: <info>  Activation (eth1/wireless): association took too long.
Apr 15 17:58:27 macbookpro NetworkManager: <info>  (eth1): device state change: 5 -> 9 (reason 7)
Apr 15 17:58:27 macbookpro NetworkManager: <info>  Activation (eth1) failed for access point (QuidcoLon)
Apr 15 17:58:27 macbookpro NetworkManager: <info>  Marking connection 'Auto QuidcoLon' invalid.
Apr 15 17:58:27 macbookpro NetworkManager: <info>  Activation (eth1) failed.
Apr 15 17:58:27 macbookpro NetworkManager: <info>  (eth1): device state change: 9 -> 3 (reason 0)
Apr 15 17:58:27 macbookpro NetworkManager: <info>  (eth1): deactivating device (reason: 0).
Apr 15 17:58:27 macbookpro NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Apr 15 17:58:29 macbookpro wpa_supplicant[949]: WPA: No SSID info found (msg 1 of 4).
Apr 15 17:58:29 macbookpro wpa_supplicant[949]: No network configuration found for the current AP
Apr 15 17:58:29 macbookpro wpa_supplicant[949]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys

```

Can anyone recommend a possible fix, or maybe its a driver issue??

---

### Post by linuxopjemac on 2010-04-16
you could try wicd

---

### Post by kwiksand on 2010-04-16
Yes, I'll try that today, cheers!

---

### Post by faust99 on 2010-06-19
Same problem here-any ideas about how to fix it?

---

