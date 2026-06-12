---
title: "Whenever I switch a wifi network, ubuntu freeze MacBookPro11,3"
date: 2015-10-24
forum: Apple Hardware Users
---

### Post by oren2 on 2015-10-24
Hi
Whenever I switch a wifi network, the macbook freeze. It happens every time, it is repeatable.
I have MacBookPro11,3 and using ububtu 14.04 with latest kernel 3.19.0-31-generic
This is the what I see in the log file ( I post to log files, for two times that it happen, I can post more as I can recreate it many times)

```

Oct 22 19:07:44 oren-MacBookPro kernel: [13380.522941] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Oct 22 19:07:44 oren-MacBookPro NetworkManager[785]: <info> (wlan0): supplicant interface state: associating -> disconnected
Oct 22 19:07:44 oren-MacBookPro wpa_supplicant[849]: wlan0: CTRL-EVENT-DISCONNECTED bssid=00:1a:1e:cb:67:80 reason=3 locally_generated=1
Oct 22 19:07:44 oren-MacBookPro kernel: [13380.616508] ------------[ cut here ]------------
Oct 22 19:07:44 oren-MacBookPro kernel: [13380.616531] WARNING: CPU: 7 PID: 7017 at /build/linux-lts-vivid-Nr0FoT/linux-lts-vivid-3.19.0/net/wireless/sme.c:664 __cfg80211_connect_result+0x3bb/0x400 [cfg80211]()
Oct 22 19:07:44 oren-MacBookPro kernel: [13380.616532] Modules linked in: snd_hda_codec_hdmi joydev x86_pkg_temp_thermal intel_powerclamp coretemp applesmc input_polldev snd_hda_codec_cirrus kvm_intel snd_hda_codec_generic kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel snd_hda_intel aes_x86_64 wl(POE) snd_hda_controller bcm5974 lrw snd_hda_codec gf128mul glue_helper snd_hwdep ablk_helper cryptd snd_pcm btusb snd_seq_midi snd_seq_midi_event cfg80211 nvidia(POE) mei_me lpc_ich mei bdc_pci snd_rawmidi thunderbolt snd_seq snd_seq_device sbs snd_timer drm sbshc snd apple_gmux soundcore video apple_bl shpchp mac_hid bnep rfcomm bluetooth parport_pc ppdev lp parport nls_iso8859_1 hid_generic hid_apple uas ahci usbhid usb_storage libahci hid
Oct 22 19:07:44 oren-MacBookPro kernel: [13380.616562] CPU: 7 PID: 7017 Comm: kworker/u16:2 Tainted: P        W  OE  3.19.0-31-generic #36~14.04.1-Ubuntu
Oct 22 19:07:44 oren-MacBookPro kernel: [13380.616564] Hardware name: Apple Inc. MacBookPro11,3/Mac-2BD1B31983FE1663, BIOS MBP112.88Z.0138.B15.1506050548 06/05/2015
Oct 22 19:07:44 oren-MacBookPro kernel: [13380.616569] Workqueue: cfg80211 cfg80211_event_work [cfg80211]
Oct 22 19:07:44 oren-MacBookPro kernel: [13380.616570]  ffffffffc0b5c4f8 ffff88037b053c68 ffffffff817af3fb 0000000000000000
Oct 22 19:07:44 oren-MacBookPro kernel: [13380.616572]  0000000000000000 ffff88037b053ca8 ffffffff81074daa ffff88046aa8c878
Oct 22 19:07:44 oren-MacBookPro kernel: [13380.616574]  0000000000000000 0000000000000000 ffff8802a7f26198 ffff88046aa8c800
Oct 22 19:07:44 oren-MacBookPro kernel: [13380.616576] Call Trace:
Oct 22 19:07:44 oren-MacBookPro kernel: [13380.616582]  [<ffffffff817af3fb>] dump_stack+0x45/0x57
Oct 22 19:07:44 oren-MacBookPro kernel: [13380.616584]  [<ffffffff81074daa>] warn_slowpath_common+0x8a/0xc0
Oct 22 19:07:44 oren-MacBookPro kernel: [13380.616586]  [<ffffffff81074e9a>] warn_slowpath_null+0x1a/0x20
Oct 22 19:07:44 oren-MacBookPro kernel: [13380.616593]  [<ffffffffc0b39adb>] __cfg80211_connect_result+0x3bb/0x400 [cfg80211]
Oct 22 19:07:44 oren-MacBookPro kernel: [13380.616600]  [<ffffffffc0b15073>] cfg80211_process_wdev_events+0x153/0x1d0 [cfg80211]
Oct 22 19:07:44 oren-MacBookPro kernel: [13380.616605]  [<ffffffffc0b15128>] cfg80211_process_rdev_events+0x38/0x70 [cfg80211]
Oct 22 19:07:44 oren-MacBookPro kernel: [13380.616610]  [<ffffffffc0b10022>] cfg80211_event_work+0x22/0x30 [cfg80211]
Oct 22 19:07:44 oren-MacBookPro kernel: [13380.616612]  [<ffffffff8108db8f>] process_one_work+0x14f/0x400
Oct 22 19:07:44 oren-MacBookPro kernel: [13380.616614]  [<ffffffff8108e328>] worker_thread+0x118/0x510
Oct 22 19:07:44 oren-MacBookPro kernel: [13380.616616]  [<ffffffff8108e210>] ? rescuer_thread+0x3d0/0x3d0
Oct 22 19:07:44 oren-MacBookPro kernel: [13380.616618]  [<ffffffff81093822>] kthread+0xd2/0xf0
Oct 22 19:07:44 oren-MacBookPro kernel: [13380.616620]  [<ffffffff81093750>] ? kthread_create_on_node+0x1c0/0x1c0
Oct 22 19:07:44 oren-MacBookPro kernel: [13380.616622]  [<ffffffff817b6d18>] ret_from_fork+0x58/0x90
Oct 22 19:07:44 oren-MacBookPro kernel: [13380.616624]  [<ffffffff81093750>] ? kthread_create_on_node+0x1c0/0x1c0
Oct 22 19:07:44 oren-MacBookPro kernel: [13380.616625] ---[ end trace f4c49c5ec178e02b ]---
Oct 22 19:07:44 oren-MacBookPro NetworkManager[785]: <info> (wlan0): supplicant interface state: disconnected -> associated
Oct 22 19:07:44 oren-MacBookPro NetworkManager[785]: <warn> Connection disconnected (reason -3)
Oct 22 19:07:44 oren-MacBookPro wpa_supplicant[849]: wlan0: CTRL-EVENT-SCAN-STARTED 
Oct 22 19:07:44 oren-MacBookPro NetworkManager[785]: <info> (wlan0): supplicant interface state: associated -> scanning
Oct 22 19:07:54 oren-MacBookPro wpa_supplicant[849]: wlan0: CTRL-EVENT-SCAN-STARTED 
Oct 22 19:07:58 oren-MacBookPro wpa_supplicant[849]: wlan0: CTRL-EVENT-SSID-REENABLED id=0 ssid="David B-Zone"
Oct 22 19:07:58 oren-MacBookPro wpa_supplicant[849]: wlan0: Trying to associate with 00:1a:1e:cb:67:80 (SSID='David B-Zone' freq=2462 MHz)
Oct 22 19:07:58 oren-MacBookPro NetworkManager[785]: <info> (wlan0): supplicant interface state: scanning -> associating
Oct 22 19:08:07 oren-MacBookPro NetworkManager[785]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Oct 22 19:08:07 oren-MacBookPro NetworkManager[785]: <info> (wlan0): device state change: config -> failed (reason 'supplicant-timeout') [50 120 11]
Oct 22 19:08:07 oren-MacBookPro NetworkManager[785]: <info> NetworkManager state is now DISCONNECTED
Oct 22 19:08:07 oren-MacBookPro NetworkManager[785]: <warn> Activation (wlan0) failed for connection 'David B-Zone'
Oct 22 19:08:07 oren-MacBookPro NetworkManager[785]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Oct 22 19:08:07 oren-MacBookPro NetworkManager[785]: <info> (wlan0): deactivating device (reason 'none') [0]
Oct 22 19:08:07 oren-MacBookPro wpa_supplicant[849]: wlan0: CTRL-EVENT-DISCONNECTED bssid=00:1a:1e:cb:67:80 reason=3 locally_generated=1
Oct 22 19:08:07 oren-MacBookPro NetworkManager[785]: <warn> Connection disconnected (reason -3)
Oct 22 19:08:07 oren-MacBookPro NetworkManager[785]: <info> (wlan0): supplicant interface state: associating -> disconnected
Oct 22 19:08:07 oren-MacBookPro wpa_supplicant[849]: wlan0: CTRL-EVENT-SCAN-STARTED 
Oct 22 19:08:07 oren-MacBookPro NetworkManager[785]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Oct 22 19:08:10 oren-MacBookPro NetworkManager[785]: <info> Auto-activating connection 'David B-Zone'.
Oct 22 19:08:10 oren-MacBookPro NetworkManager[785]: <info> Activation (wlan0) starting connection 'David B-Zone'
Oct 22 19:08:10 oren-MacBookPro NetworkManager[785]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Oct 22 19:08:10 oren-MacBookPro NetworkManager[785]: <info> NetworkManager state is now CONNECTING
Oct 22 19:08:10 oren-MacBookPro NetworkManager[785]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Oct 22 19:08:10 oren-MacBookPro NetworkManager[785]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Oct 22 19:08:10 oren-MacBookPro NetworkManager[785]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Oct 22 19:08:10 oren-MacBookPro NetworkManager[785]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Oct 22 19:08:10 oren-MacBookPro NetworkManager[785]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Oct 22 19:08:10 oren-MacBookPro NetworkManager[785]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Oct 22 19:08:10 oren-MacBookPro NetworkManager[785]: <info> Activation (wlan0/wireless): connection 'David B-Zone' requires no security.  No secrets needed.
Oct 22 19:08:10 oren-MacBookPro NetworkManager[785]: <info> Config: added 'ssid' value 'David B-Zone'
Oct 22 19:08:10 oren-MacBookPro NetworkManager[785]: <info> Config: added 'scan_ssid' value '1'
Oct 22 19:08:10 oren-MacBookPro NetworkManager[785]: <info> Config: added 'key_mgmt' value 'NONE'
Oct 22 19:08:10 oren-MacBookPro NetworkManager[785]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Oct 22 19:08:10 oren-MacBookPro NetworkManager[785]: <info> Config: set interface ap_scan to 1
Oct 22 19:08:12 oren-MacBookPro wpa_supplicant[849]: wlan0: Trying to associate with 00:1a:1e:cb:67:80 (SSID='David B-Zone' freq=2462 MHz)
Oct 22 19:08:12 oren-MacBookPro NetworkManager[785]: <info> (wlan0): supplicant interface state: disconnected -> associating
Oct 22 19:08:12 oren-MacBookPro wpa_supplicant[849]: wlan0: Associated with 00:1a:1e:cb:67:80
Oct 22 19:08:12 oren-MacBookPro wpa_supplicant[849]: wlan0: CTRL-EVENT-CONNECTED - Connection to 00:1a:1e:cb:67:80 completed [id=0 id_str=]
Oct 22 19:08:12 oren-MacBookPro NetworkManager[785]: <info> (wlan0): supplicant interface state: associating -> completed
Oct 22 19:08:12 oren-MacBookPro NetworkManager[785]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'David B-Zone'.
Oct 22 19:08:12 oren-MacBookPro NetworkManager[785]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Oct 22 19:08:12 oren-MacBookPro NetworkManager[785]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Oct 22 19:08:12 oren-MacBookPro NetworkManager[785]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Oct 22 19:08:12 oren-MacBookPro NetworkManager[785]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct 22 19:08:12 oren-MacBookPro NetworkManager[785]: <info> dhclient started with pid 10600
Oct 22 19:08:12 oren-MacBookPro NetworkManager[785]: <info> Activation (wlan0) Beginning IP6 addrconf.
Oct 22 19:08:12 oren-MacBookPro avahi-daemon[512]: Withdrawing address record for fe80::3e15:c2ff:fed2:fbc2 on wlan0.
Oct 22 19:08:12 oren-MacBookPro avahi-daemon[512]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::3e15:c2ff:fed2:fbc2.
Oct 22 19:08:12 oren-MacBookPro avahi-daemon[512]: Interface wlan0.IPv6 no longer relevant for mDNS.
Oct 22 19:08:12 oren-MacBookPro NetworkManager[785]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Oct 22 19:08:12 oren-MacBookPro dhclient: Internet Systems Consortium DHCP Client 4.2.4
Oct 22 19:08:12 oren-MacBookPro dhclient: Copyright 2004-2012 Internet Systems Consortium.
Oct 22 19:08:12 oren-MacBookPro dhclient: All rights reserved.
Oct 22 19:08:12 oren-MacBookPro dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct 22 19:08:12 oren-MacBookPro dhclient: 
Oct 22 19:08:12 oren-MacBookPro NetworkManager[785]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Oct 22 19:08:12 oren-MacBookPro dhclient: Listening on LPF/wlan0/3c:15:c2:d2:fb:c2
Oct 22 19:08:12 oren-MacBookPro dhclient: Sending on   LPF/wlan0/3c:15:c2:d2:fb:c2
Oct 22 19:08:12 oren-MacBookPro dhclient: Sending on   Socket/fallback
Oct 22 19:08:12 oren-MacBookPro dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 (xid=0x54b19459)
Oct 22 19:08:14 oren-MacBookPro avahi-daemon[512]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::3e15:c2ff:fed2:fbc2.
Oct 22 19:08:14 oren-MacBookPro avahi-daemon[512]: New relevant interface wlan0.IPv6 for mDNS.
Oct 22 19:08:14 oren-MacBookPro avahi-daemon[512]: Registering new address record for fe80::3e15:c2ff:fed2:fbc2 on wlan0.*.
Oct 22 19:08:15 oren-MacBookPro dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6 (xid=0x54b19459)
Oct 22 19:08:16 oren-MacBookPro dhclient: DHCPREQUEST of 10.60.0.152 on wlan0 to 255.255.255.255 port 67 (xid=0x5994b154)
Oct 22 19:08:16 oren-MacBookPro dhclient: DHCPOFFER of 10.60.0.152 from 10.60.0.1
Oct 22 19:08:16 oren-MacBookPro dhclient: DHCPACK of 10.60.0.152 from 10.60.0.1
Oct 22 19:08:16 oren-MacBookPro dhclient: bound to 10.60.0.152 -- renewal in 1467 seconds.
Oct 22 19:08:16 oren-MacBookPro NetworkManager[785]: <info> (wlan0): DHCPv4 state changed preinit -> bound
Oct 22 19:08:16 oren-MacBookPro NetworkManager[785]: <info>   address 10.60.0.152
Oct 22 19:08:16 oren-MacBookPro NetworkManager[785]: <info>   prefix 23 (255.255.254.0)
Oct 22 19:08:16 oren-MacBookPro NetworkManager[785]: <info>   gateway 10.60.0.1
Oct 22 19:08:16 oren-MacBookPro NetworkManager[785]: <info>   nameserver '10.60.0.1'
Oct 22 19:08:16 oren-MacBookPro NetworkManager[785]: <info>   domain name 'hp.lan'
Oct 22 19:08:16 oren-MacBookPro NetworkManager[785]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Oct 22 19:08:16 oren-MacBookPro NetworkManager[785]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Oct 22 19:08:16 oren-MacBookPro avahi-daemon[512]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.60.0.152.
Oct 22 19:08:16 oren-MacBookPro avahi-daemon[512]: New relevant interface wlan0.IPv4 for mDNS.
Oct 22 19:08:16 oren-MacBookPro avahi-daemon[512]: Registering new address record for 10.60.0.152 on wlan0.IPv4.
Oct 22 19:08:17 oren-MacBookPro NetworkManager[785]: <info> (wlan0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Oct 22 19:08:17 oren-MacBookPro NetworkManager[785]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Oct 22 19:08:17 oren-MacBookPro NetworkManager[785]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Oct 22 19:08:17 oren-MacBookPro NetworkManager[785]: <info> NetworkManager state is now CONNECTED_GLOBAL
Oct 22 19:08:17 oren-MacBookPro NetworkManager[785]: <info> Policy set 'David B-Zone' (wlan0) as default for IPv4 routing and DNS.
Oct 22 19:08:17 oren-MacBookPro NetworkManager[785]: <info> Writing DNS information to /sbin/resolvconf
Oct 22 19:08:17 oren-MacBookPro dnsmasq[1505]: setting upstream servers from DBus
Oct 22 19:08:17 oren-MacBookPro dnsmasq[1505]: using nameserver 10.60.0.1#53
Oct 22 19:08:18 oren-MacBookPro NetworkManager[785]: <info> (wlan0): roamed from BSSID 00:1A:1E:C8:8E:F0 (David B-Zone) to 00:1A:1E:CB:67:80 (David B-Zone)
Oct 22 19:08:18 oren-MacBookPro NetworkManager[785]: <info> Activation (wlan0) successful, device activated.
Oct 22 19:08:18 oren-MacBookPro dbus[458]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Oct 22 19:08:18 oren-MacBookPro dbus[458]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Oct 22 19:08:18 oren-MacBookPro whoopsie[1086]: message repeated 5 times: [ offline]
Oct 22 19:08:18 oren-MacBookPro whoopsie[1086]: online
Oct 22 19:08:24 oren-MacBookPro ntpdate[10685]: adjust time server 91.189.94.4 offset -0.263547 sec
Oct 22 19:08:32 oren-MacBookPro NetworkManager[785]: <info> (wlan0): IP6 addrconf timed out or failed.
Oct 22 19:08:32 oren-MacBookPro NetworkManager[785]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Oct 22 19:08:32 oren-MacBookPro NetworkManager[785]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Oct 22 19:08:32 oren-MacBookPro NetworkManager[785]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Oct 22 19:08:33 oren-MacBookPro wpa_supplicant[849]: wlan0: CTRL-EVENT-SCAN-STARTED 
```


```

Oct 22 15:06:07 oren-MacBookPro wpa_supplicant[875]: wlan0: CTRL-EVENT-CONNECTED - Connection to 00:1a:1e:cb:67:80 completed [id=0 id_str=]
Oct 22 15:06:07 oren-MacBookPro NetworkManager[776]: <info> (wlan0): supplicant interface state: associating -> completed
Oct 22 15:06:07 oren-MacBookPro NetworkManager[776]: <info> (wlan0): roamed from BSSID 00:24:6C:E8:37:80 (David B-Zone) to 00:1A:1E:CB:67:80 (David B-Zone)
Oct 22 15:06:08 oren-MacBookPro avahi-daemon[506]: Withdrawing workstation service for tun0.
Oct 22 15:06:08 oren-MacBookPro NetworkManager[776]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/tun0, iface: tun0)
Oct 22 15:06:45 oren-MacBookPro wpa_supplicant[875]: wlan0: CTRL-EVENT-SCAN-STARTED 
Oct 22 15:09:01 oren-MacBookPro CRON[8694]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Oct 22 15:09:19 oren-MacBookPro dbus[464]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Oct 22 15:09:19 oren-MacBookPro dbus[464]: [system] Successfully activated service 'org.freedesktop.hostname1'
Oct 22 15:09:19 oren-MacBookPro kernel: [12691.912657] systemd-hostnamed[8720]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
Oct 22 15:10:44 oren-MacBookPro kernel: [12777.089633] ------------[ cut here ]------------
Oct 22 15:10:44 oren-MacBookPro kernel: [12777.089653] WARNING: CPU: 2 PID: 662 at /build/linux-lts-vivid-Nr0FoT/linux-lts-vivid-3.19.0/net/wireless/sme.c:800 cfg80211_roamed+0x89/0x90 [cfg80211]()
Oct 22 15:10:44 oren-MacBookPro kernel: [12777.089654] Modules linked in: snd_hda_codec_hdmi joydev applesmc input_polldev x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel wl(POE) snd_hda_codec_cirrus snd_hda_codec_generic aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd snd_hda_intel snd_seq_midi snd_hda_controller cfg80211 snd_seq_midi_event snd_hda_codec btusb snd_rawmidi snd_hwdep nvidia(POE) lpc_ich bdc_pci snd_pcm snd_seq thunderbolt bcm5974 snd_seq_device snd_timer snd mei_me apple_gmux drm mei soundcore sbs shpchp sbshc video apple_bl mac_hid rfcomm bnep bluetooth parport_pc ppdev lp parport nls_iso8859_1 hid_generic hid_apple uas ahci usbhid libahci usb_storage hid
Oct 22 15:10:44 oren-MacBookPro kernel: [12777.089681] CPU: 2 PID: 662 Comm: wl_event_handle Tainted: P           OE  3.19.0-31-generic #36~14.04.1-Ubuntu
Oct 22 15:10:44 oren-MacBookPro kernel: [12777.089682] Hardware name: Apple Inc. MacBookPro11,3/Mac-2BD1B31983FE1663, BIOS MBP112.88Z.0138.B15.1506050548 06/05/2015
Oct 22 15:10:44 oren-MacBookPro kernel: [12777.089683]  ffffffffc0cf44f8 ffff88006a04bda8 ffffffff817af3fb 0000000000000000
Oct 22 15:10:44 oren-MacBookPro kernel: [12777.089685]  0000000000000000 ffff88006a04bde8 ffffffff81074daa ffff880468fd5c78
Oct 22 15:10:44 oren-MacBookPro kernel: [12777.089686]  ffff88046b986000 ffff880408fd1d20 0000000000000045 ffff8803e1369e60
Oct 22 15:10:44 oren-MacBookPro kernel: [12777.089688] Call Trace:
Oct 22 15:10:44 oren-MacBookPro kernel: [12777.089693]  [<ffffffff817af3fb>] dump_stack+0x45/0x57
Oct 22 15:10:44 oren-MacBookPro kernel: [12777.089696]  [<ffffffff81074daa>] warn_slowpath_common+0x8a/0xc0
Oct 22 15:10:44 oren-MacBookPro kernel: [12777.089697]  [<ffffffff81074e9a>] warn_slowpath_null+0x1a/0x20
Oct 22 15:10:44 oren-MacBookPro kernel: [12777.089703]  [<ffffffffc0cd0e09>] cfg80211_roamed+0x89/0x90 [cfg80211]
Oct 22 15:10:44 oren-MacBookPro kernel: [12777.089728]  [<ffffffffc0f9f95b>] wl_notify_roaming_status+0xcb/0x150 [wl]
Oct 22 15:10:44 oren-MacBookPro kernel: [12777.089746]  [<ffffffffc0f9ebfa>] wl_event_handler+0x6a/0x230 [wl]
Oct 22 15:10:44 oren-MacBookPro kernel: [12777.089763]  [<ffffffffc0f9eb90>] ? wl_cfg80211_add_key+0x6a0/0x6a0 [wl]
Oct 22 15:10:44 oren-MacBookPro kernel: [12777.089765]  [<ffffffff81093822>] kthread+0xd2/0xf0
Oct 22 15:10:44 oren-MacBookPro kernel: [12777.089767]  [<ffffffff81093750>] ? kthread_create_on_node+0x1c0/0x1c0
Oct 22 15:10:44 oren-MacBookPro kernel: [12777.089769]  [<ffffffff817b6d18>] ret_from_fork+0x58/0x90
Oct 22 15:10:44 oren-MacBookPro kernel: [12777.089770]  [<ffffffff81093750>] ? kthread_create_on_node+0x1c0/0x1c0
Oct 22 15:10:44 oren-MacBookPro kernel: [12777.089771] ---[ end trace 2ef74c5f7e07ae0e ]---

```

Any help, 
Thanks.

---

