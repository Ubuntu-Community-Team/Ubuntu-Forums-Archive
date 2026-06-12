---
title: "wpa_supplicant fails to authenticate"
date: 2007-09-12
forum: Apple Intel Users
---

### Post by mr.gizm0 on 2007-09-12
Hi, first an explanation, I have installed gentoo-current on my macbook, and I'm having some difficulties getting wpa_supllicant to work, I posted on the ubuntu forum because I've seen the excellant support provided to apple macbook/macbook pro users on here.

The problem is that wpa_supplicant is unable to authenticate. Below are the listings for my conf file and some command's I have run on my laptop to show you the output, I'd appreciate any help big or small, even if it is not related to gentoo (I didn't expect that anyway).

I have tried to connect to 2 completely seperate routers and have had the same problems. The router called burk is at my girlfriends house and sam is my router. So I only be posting information regard "sam", just incase you were wondering where "burk" was.

I'm using the following
**wpa_supplicant v0.5.8**
**Linux Kernel 2.6.22.1 with mactel patches** 
**madwifi-ng drivers- madwifi-ng-r2706-20070911 **
I obtained the driver from [http://snapshots.madwifi.org/madwifi-ng-current.tar.gz](http://snapshots.madwifi.org/madwifi-ng-current.tar.gz)

Thanks for your time, patients and for reading my threads, I look forward to your suggestions.

```

[b]
Router iinformation
router name: sam
manufacturer: belkin
Allowed client type: WPA
Authentication: Preshared key
Encryption technique: AES
[/b]

```

Here is my conf
```

cat /etc/wpa_supplicant/wpa_supplicant.conf
# This is a network block that connects to any unsecured access point.
# We give it a low priority so any defined blocks are preferred.

ctrl_interface=/var/run/wpa_supplicant
#eapol_version=1
ap_scan=1
#fast_reauth=1

network={
ssid="burk"
scan_ssid=1
proto=RSN WPA
key_mgmt=WPA-PSK
pairwise=CCMP
psk="PSKKEYFORBURKGOESHERE"
priority=4
}

network={
ssid="sam"
scan_ssid=1
proto=WPA
key_mgmt=WPA-PSK
pairwise=CCMP
psk="PSKKEYFORSAMGOESHERE"
priority=1
}

```


iwlist ath0 scanning: (scan done from home) To proove that the router is detected.
```


ath0      Scan completed :
          Cell 01 - Address: 00:11:50:91:57:73
                    ESSID:"sam"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=43/70  Signal level=-52 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

```

 wpa_supplicant  -Dmadwifi -iath0 -c/etc/wpa_supplicant/wpa_supplicant.conf: (from home)
```

Trying to associate with 00:11:50:91:57:73 (SSID='sam' freq=2462 MHz)
Associated with 00:11:50:91:57:73
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys

```

Attempting to connect to sam which uses wpa
```

priority=1 (0x1)
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 4
   id=0 ssid='burk'
Priority group 1
   id=1 ssid='sam'
Initializing interface (2) 'ath0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=22 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:1b:63:00:e2:62
wpa_driver_madwifi_del_key: keyidx=0
wpa_driver_madwifi_del_key: keyidx=1
wpa_driver_madwifi_del_key: keyidx=2
wpa_driver_madwifi_del_key: keyidx=3
wpa_driver_madwifi_set_countermeasures: enabled=0
wpa_driver_madwifi_set_drop_unencrypted: enabled=1
Setting scan request: 0 sec 100000 usec
Added interface ath0
RTM_NEWLINK: operstate=0 ifi_flags=0x1002 ()
Wireless event: cmd=0x8b06 len=8
Ignore event for foreign ifindex 3
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ath0' added
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=4):
     62 75 72 6b                                       burk
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 4
Try to find WPA-enabled AP
Try to find non-WPA AP
Selecting BSS from priority group 1
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable AP found.
Setting scan request: 0 sec 0 usec
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=3):
     73 61 6d                                          sam
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b1a len=11
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b19 len=8
Received 218 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 4
Try to find WPA-enabled AP
0: 00:11:50:91:57:73 ssid='sam' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
Try to find non-WPA AP
0: 00:11:50:91:57:73 ssid='sam' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
Selecting BSS from priority group 1
Try to find WPA-enabled AP
0: 00:11:50:91:57:73 ssid='sam' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
   selected WPA AP 00:11:50:91:57:73 ssid='sam'
Try to find non-WPA AP
Trying to associate with 00:11:50:91:57:73 (SSID='sam' freq=2462 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 16 pairwise 16 key_mgmt 2 proto 1
WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02
WPA: clearing AP RSN IE
WPA: using GTK CCMP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_madwifi_set_drop_unencrypted: enabled=1
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_madwifi_associate
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b1a len=11
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:11:50:91:57:73
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:11:50:91:57:73
No keys have been configured - skip key clearing
Associated with 00:11:50:91:57:73
WPA: Association event - clear replay counter
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ath0' added
EAPOL: startWhen --> 0
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: txStart
WPA: drop TX EAPOL in non-IEEE 802.1X mode (type=1 len=0)
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Setting scan request: 0 sec 100000 usec
Added BSSID 00:11:50:91:57:73 into blacklist
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_madwifi_del_key: keyidx=0
wpa_driver_madwifi_del_key: keyidx=1
wpa_driver_madwifi_del_key: keyidx=2
wpa_driver_madwifi_del_key: keyidx=3
wpa_driver_madwifi_del_key: keyidx=0
State: ASSOCIATED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ath0' added
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b1a len=8
Authentication with 00:00:00:00:00:00 timed out.
Added BSSID 00:00:00:00:00:00 into blacklist
No keys have been configured - skip key clearing
State: SCANNING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=4):
     62 75 72 6b                                       burk
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b1a len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b19 len=8
Received 218 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 4
Try to find WPA-enabled AP
0: 00:11:50:91:57:73 ssid='sam' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
Try to find non-WPA AP
0: 00:11:50:91:57:73 ssid='sam' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
Selecting BSS from priority group 1
Try to find WPA-enabled AP
0: 00:11:50:91:57:73 ssid='sam' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
   selected WPA AP 00:11:50:91:57:73 ssid='sam'
Try to find non-WPA AP
Trying to associate with 00:11:50:91:57:73 (SSID='sam' freq=2462 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 16 pairwise 16 key_mgmt 2 proto 1
WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02
WPA: clearing AP RSN IE
WPA: using GTK CCMP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_madwifi_set_drop_unencrypted: enabled=1
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_madwifi_associate
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b1a len=11
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:11:50:91:57:73
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:11:50:91:57:73
No keys have been configured - skip key clearing
Associated with 00:11:50:91:57:73
WPA: Association event - clear replay counter
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ath0' added
EAPOL: startWhen --> 0
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: txStart
WPA: drop TX EAPOL in non-IEEE 802.1X mode (type=1 len=0)
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface ath0
State: ASSOCIATED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_madwifi_deauthenticate
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAPOL: External notification - portValid=0
wpa_driver_madwifi_set_drop_unencrypted: enabled=0
wpa_driver_madwifi_set_countermeasures: enabled=0
No keys have been configured - skip key clearing
Removed BSSID 00:00:00:00:00:00 from blacklist (clear)
Removed BSSID 00:11:50:91:57:73 from blacklist (clear)
Cancelling scan request
Cancelling authentication timeout

```


Attempting to connect to "burk" which uses wpa2
```

Configuration file '/etc/wpa_supplicant/wpa_supplicant.conf' -> '/etc/wpa_supplicant/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
eapol_version=1
ap_scan=1
fast_reauth=1
Line: 9 - start of a new network block
ssid - hexdump_ascii(len=4):
     62 75 72 6b                                       burk            
key_mgmt: 0x2
proto: 0x1
pairwise: 0x18
group: 0x18
PSK (ASCII passphrase) - hexdump_ascii(len=9): [REMOVED]
priority=1 (0x1)
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 1
   id=0 ssid='burk'
Initializing interface (2) 'ath0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=22 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:1b:63:00:e2:62
wpa_driver_madwifi_del_key: keyidx=0
wpa_driver_madwifi_del_key: keyidx=1
wpa_driver_madwifi_del_key: keyidx=2
wpa_driver_madwifi_del_key: keyidx=3
wpa_driver_madwifi_set_countermeasures: enabled=0
wpa_driver_madwifi_set_drop_unencrypted: enabled=1
Setting scan request: 0 sec 100000 usec
Added interface ath0
RTM_NEWLINK: operstate=0 ifi_flags=0x1002 ()
Wireless event: cmd=0x8b06 len=8
Ignore event for foreign ifindex 3
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ath0' added
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 1
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable AP found.
Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b1a len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b19 len=8
Received 516 bytes of scan results (2 BSSes)
Scan results: 2
Selecting BSS from priority group 1
Try to find WPA-enabled AP
0: 00:11:50:85:20:46 ssid='burk' wpa_ie_len=24 rsn_ie_len=22 caps=0x11
   selected based on WPA IE
   selected WPA AP 00:11:50:85:20:46 ssid='burk'
Try to find non-WPA AP
Trying to associate with 00:11:50:85:20:46 (SSID='burk' freq=2462 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 16 pairwise 16 key_mgmt 2 proto 1
WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02
WPA: set AP RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 01 00
WPA: using GTK CCMP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_madwifi_set_drop_unencrypted: enabled=1
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_madwifi_associate
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RSN: added PMKSA cache candidate 00:11:50:85:20:46 prio 1000
RSN: processing PMKSA candidate list
RSN: not in suitable state for new pre-authentication
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b1a len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:11:50:85:20:46
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:11:50:85:20:46
No keys have been configured - skip key clearing
Associated with 00:11:50:85:20:46
WPA: Association event - clear replay counter
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ath0' added
EAPOL: startWhen --> 0
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: txStart
WPA: drop TX EAPOL in non-IEEE 802.1X mode (type=1 len=0)
Authentication with 00:11:50:85:20:46 timed out.
Added BSSID 00:11:50:85:20:46 into blacklist
wpa_driver_madwifi_disassociate
No keys have been configured - skip key clearing
State: ASSOCIATED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Added BSSID 00:00:00:00:00:00 into blacklist
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_madwifi_del_key: keyidx=0
wpa_driver_madwifi_del_key: keyidx=1
wpa_driver_madwifi_del_key: keyidx=2
wpa_driver_madwifi_del_key: keyidx=3
wpa_driver_madwifi_del_key: keyidx=0
State: SCANNING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8c02 len=95
WEXT: Custom wireless event: 'STA-TRAFFIC-STAT
mac=00:11:50:85:20:46
rx_packets=0
rx_bytes=0
tx_packets=0
tx_bytes=0
'
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
BSSID 00:00:00:00:00:00 blacklist count incremented to 2
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_madwifi_del_key: keyidx=0
wpa_driver_madwifi_del_key: keyidx=1
wpa_driver_madwifi_del_key: keyidx=2
wpa_driver_madwifi_del_key: keyidx=3
wpa_driver_madwifi_del_key: keyidx=0
State: DISCONNECTED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ath0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b1a len=8
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface ath0
State: DISCONNECTED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_madwifi_set_drop_unencrypted: enabled=0
wpa_driver_madwifi_set_countermeasures: enabled=0
No keys have been configured - skip key clearing
Removed BSSID 00:00:00:00:00:00 from blacklist (clear)
Removed BSSID 00:11:50:85:20:46 from blacklist (clear)
Cancelling scan request
Cancelling authentication timeout

```

---

### Post by cyberdork33 on 2007-09-12
burk:
```

Authentication with 00:11:50:85:20:46 timed out.
```I would assume this means that you have a configuration error in wpa_supplicant. I never used gentoo with WPA2 so I don't know what to do from there.

on sam, it looks like it connected, saw a 00:00:00... AP and then disconnected because of it. I have no idea why.

There are a couple of gentoo users here, maybe they can help more.

From what i see online, it looks like your config is OK, but you might just try simplifying it a bit for debugging... Try this (remove / comment the other AP for now.):

```
network={
ssid="burk"
proto=RSN
key_mgmt=WPA-PSK
psk="PSKKEYFORBURKGOESHERE"
}
```

Also, you can pre-generate the encryption key for your AP by using the wpa_passphrase command, then it does not have to calculate it everytime the supplicant starts.
```
wpa_passphrase burk PSKKEYFORBURKGOESHERE
```

---

