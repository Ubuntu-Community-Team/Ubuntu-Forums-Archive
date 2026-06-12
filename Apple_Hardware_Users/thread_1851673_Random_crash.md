---
title: "Random crash"
date: 2011-09-28
forum: Apple Hardware Users
---

### Post by idealistic on 2011-09-28
Hi,

I use ubuntu 11,04 on my macbook 2,1 (getting old now !) for a long time now and never had such a problem.

The computer randomly either crashes and leaves a black screen with what appears to be the system log displayed, or freezes and I can't move the mouse or use the keyboard any more. all i can do in either case is to press the power button and wait till it goes off to light it on again.

Here's a copy of what get displayed :

```
Pasokon kernel: [  327.546211] cfg80211: Disabling freq 5745 MHz
Sep 28 23:41:51 Pasokon kernel: [  327.546215] cfg80211: Disabling freq 5765 MHz
Sep 28 23:41:51 Pasokon kernel: [  327.546219] cfg80211: Disabling freq 5785 MHz
Sep 28 23:41:51 Pasokon kernel: [  327.546222] cfg80211: Disabling freq 5805 MHz
Sep 28 23:41:51 Pasokon kernel: [  327.546226] cfg80211: Disabling freq 5825 MHz
Sep 28 23:41:51 Pasokon kernel: [  327.546237] cfg80211: World regulatory domain updated:
Sep 28 23:41:51 Pasokon kernel: [  327.546240] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Sep 28 23:41:51 Pasokon kernel: [  327.546247] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 28 23:41:51 Pasokon kernel: [  327.546253] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Sep 28 23:41:51 Pasokon kernel: [  327.546259] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Sep 28 23:41:51 Pasokon kernel: [  327.546265] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 28 23:41:51 Pasokon kernel: [  327.546270] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 28 23:41:52 Pasokon NetworkManager[817]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Sep 28 23:41:54 Pasokon wpa_supplicant[884]: Trying to associate with 8a:8b:c5:d4:a6:7a (SSID='FreeWifi' freq=2462 MHz)
Sep 28 23:41:54 Pasokon NetworkManager[817]: <info> (wlan0): supplicant connection state:  scanning -> associating
Sep 28 23:41:54 Pasokon kernel: [  330.590675] wlan0: authenticate with 8a:8b:c5:d4:a6:7a (try 1)
Sep 28 23:41:54 Pasokon kernel: [  330.596024] wlan0: authenticated
Sep 28 23:41:54 Pasokon kernel: [  330.601105] wlan0: associate with 8a:8b:c5:d4:a6:7a (try 1)
Sep 28 23:41:54 Pasokon kernel: [  330.610006] wlan0: RX AssocResp from 8a:8b:c5:d4:a6:7a (capab=0x401 status=0 aid=2)
Sep 28 23:41:54 Pasokon kernel: [  330.610010] wlan0: associated
Sep 28 23:41:54 Pasokon wpa_supplicant[884]: Associated with 8a:8b:c5:d4:a6:7a
Sep 28 23:41:54 Pasokon wpa_supplicant[884]: CTRL-EVENT-CONNECTED - Connection to 8a:8b:c5:d4:a6:7a completed (reauth) [id=0 id_str=]
Sep 28 23:41:54 Pasokon NetworkManager[817]: <info> (wlan0): supplicant connection state:  associating -> associated
Sep 28 23:41:54 Pasokon NetworkManager[817]: <info> (wlan0): supplicant connection state:  associated -> completed
Sep 28 23:42:07 Pasokon dhclient: DHCPREQUEST of 78.251.183.141 on wlan0 to 78.251.255.254 port 67
Sep 28 23:42:07 Pasokon dhclient: DHCPACK of 78.251.183.141 from 78.251.255.254
Sep 28 23:42:07 Pasokon dhclient: bound to 78.251.183.141 -- renewal in 64 seconds.
Sep 28 23:42:57 Pasokon wpa_supplicant[884]: CTRL-EVENT-DISCONNECTED bssid=8a:8b:c5:d4:a6:7a reason=0
Sep 28 23:42:57 Pasokon kernel: [  393.023686] cfg80211: All devices are disconnected, going to restore regulatory settings
Sep 28 23:42:57 Pasokon kernel: [  393.023698] cfg80211: Restoring regulatory settings
Sep 28 23:42:57 Pasokon kernel: [  393.023706] cfg80211: Calling CRDA to update world regulatory domain
Sep 28 23:42:57 Pasokon NetworkManager[817]: <info> (wlan0): supplicant connection state:  completed -> disconnected
Sep 28 23:42:57 Pasokon kernel: [  393.032912] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Sep 28 23:42:57 Pasokon kernel: [  393.032921] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 28 23:42:57 Pasokon kernel: [  393.032927] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Sep 28 23:42:57 Pasokon kernel: [  393.032933] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 28 23:42:57 Pasokon kernel: [  393.032938] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Sep 28 23:42:57 Pasokon kernel: [  393.032944] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 28 23:42:57 Pasokon kernel: [  393.032948] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Sep 28 23:42:57 Pasokon kernel: [  393.032954] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 28 23:42:57 Pasokon kernel: [  393.032959] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Sep 28 23:42:57 Pasokon kernel: [  393.032965] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 28 23:42:57 Pasokon kernel: [  393.032970] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Sep 28 23:42:57 Pasokon kernel: [  393.032976] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 28 23:42:57 Pasokon kernel: [  393.032981] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Sep 28 23:42:57 Pasokon kernel: [  393.032986] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 28 23:42:57 Pasokon kernel: [  393.032991] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Sep 28 23:42:57 Pasokon kernel: [  393.032997] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 28 23:42:57 Pasokon kernel: [  393.033002] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Sep 28 23:42:57 Pasokon kernel: [  393.033008] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 28 23:42:57 Pasokon kernel: [  393.033013] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Sep 28 23:42:57 Pasokon kernel: [  393.033019] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 28 23:42:57 Pasokon kernel: [  393.033024] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Sep 28 23:42:57 Pasokon kernel: [  393.033030] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 28 23:42:57 Pasokon kernel: [  393.033035] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Sep 28 23:42:57 Pasokon kernel: [  393.033041] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 28 23:42:57 Pasokon kernel: [  393.033046] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Sep 28 23:42:57 Pasokon kernel: [  393.033052] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 28 23:42:57 Pasokon kernel: [  393.033057] cfg80211: Disabling freq 2484 MHz
Sep 28 23:42:57 Pasokon kernel: [  393.033062] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
Sep 28 23:42:57 Pasokon kernel: [  393.033067] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 28 23:42:57 Pasokon kernel: [  393.033073] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
Sep 28 23:42:57 Pasokon kernel: [  393.033078] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 28 23:42:57 Pasokon kernel: [  393.033083] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
Sep 28 23:42:57 Pasokon kernel: [  393.033089] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 28 23:42:57 Pasokon kernel: [  393.033094] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
Sep 28 23:42:57 Pasokon kernel: [  393.033100] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 28 23:42:57 Pasokon kernel: [  393.033105] cfg80211: Updating information on frequency 5260 MHz for a 20 MHz width channel with regulatory rule:
Sep 28 23:42:57 Pasokon kernel: [  393.033111] cfg80211: 5250000 KHz - 5330000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 28 23:42:57 Pasokon kernel: [  393.033116] cfg80211: Updating information on frequency 5280 MHz for a 20 MHz width channel with regulatory rule:
Sep 28 23:42:57 Pasokon kernel: [  393.033122] cfg80211: 5250000 KHz - 5330000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 28 23:42:57 Pasokon kernel: [  393.033127] cfg80211: Updating information on frequency 5300 MHz for a 20 MHz width channel with regulatory rule:
Sep 28 23:42:57 Pasokon kernel: [  393.033133] cfg80211: 5250000 KHz - 5330000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 28 23:42:57 Pasokon kernel: [  393.033138] cfg80211: Updating information on frequency 5320 MHz for a 20 MHz width channel with regulatory rule:
Sep 28 23:42:57 Pasokon kernel: [  393.033144] cfg80211: 5250000 KHz - 5330000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 28 23:42:57 Pasokon kernel: [  393.033149] cfg80211: Updating information on frequency 5500 MHz for a 20 MHz width channel with regulatory rule:
Sep 28 23:42:57 Pasokon kernel: [  393.033155] cfg80211: 5490000 KHz - 5710000 KHz @  KHz), (N/A mBi, 2700 mBm)
Sep 28 23:42:57 Pasokon kernel: [  393.033160] cfg80211: Updating information on frequency 5520 MHz for a 20 MHz width channel with regulatory rule:
Sep 28 23:42:57 Pasokon kernel: [  393.033166] cfg80211: 5490000 KHz - 5710000 KHz @  KHz), (N/A mBi, 2700 mBm)
Sep 28 23:42:57 Pasokon kernel: [  393.033171] cfg80211: Updating information on frequency 5540 MHz for a 20 MHz width channel with regulatory rule:
Sep 28 23:42:57 Pasokon kernel: [  393.033177] cfg80211: 5490000 KHz - 5710000 KHz @  KHz), (N/A mBi, 2700 mBm)
Sep 28 23:42:57 Pasokon kernel: [  393.033182] cfg80211: Updating information on frequency 5560 MHz for a 20 MHz width channel with regulatory rule:
Sep 28 23:42:57 Pasokon kernel: [  393.033188] cfg80211: 5490000 KHz - 5710000 KHz @  KHz), (N/A mBi, 2700 mBm)
Sep 28 23:42:57 Pasokon kernel: [  393.033193] cfg80211: Updating information on frequency 5580 MHz for a 20 MHz width channel with regulatory rule:
Sep 28 23:42:57 Pasokon kernel: [  393.033199] cfg80211: 5490000 KHz - 5710000 KHz @  KHz), (N/A mBi, 2700 mBm)
Sep 28 23:42:57 Pasokon kernel: [  393.033204] cfg80211: Updating information on frequency 5600 MHz for a 20 MHz width channel with regulatory rule:
Sep 28 23:42:57 Pasokon kernel: [  393.033209] cfg80211: 5490000 KHz - 5710000 KHz @  KHz), (N/A mBi, 2700 mBm)
Sep 28 23:42:57 Pasokon kernel: [  393.033214] cfg80211: Updating information on frequency 5620 MHz for a 20 MHz width channel with regulatory rule:
Sep 28 23:42:57 Pasokon kernel: [  393.033220] cfg80211: 5490000 KHz - 5710000 KHz @  KHz), (N/A mBi, 2700 mBm)
Sep 28 23:42:57 Pasokon kernel: [  393.033225] cfg80211: Updating information on frequency 5640 MHz for a 20 MHz width channel with regulatory rule:
Sep 28 23:42:57 Pasokon kernel: [  393.033231] cfg80211: 5490000 KHz - 5710000 KHz @  KHz), (N/A mBi, 2700 mBm)
Sep 28 23:42:57 Pasokon kernel: [  393.033236] cfg80211: Updating information on frequency 5660 MHz for a 20 MHz width channel with regulatory rule:
Sep 28 23:42:57 Pasokon kernel: [  393.033243] cfg80211: 5490000 KHz - 5710000 KHz @  KHz), (N/A mBi, 2700 mBm)
Sep 28 23:42:57 Pasokon kernel: [  393.033247] cfg80211: Updating information on frequency 5680 MHz for a 20 MHz width channel with regulatory rule:
Sep 28 23:42:57 Pasokon kernel: [  393.033253] cfg80211: 5490000 KHz - 5710000 KHz @  KHz), (N/A mBi, 2700 mBm)
Sep 28 23:42:57 Pasokon kernel: [  393.033258] cfg80211: Updating information on frequency 5700 MHz for a 20 MHz width channel with regulatory rule:
Sep 28 23:42:57 Pasokon kernel: [  393.033264] cfg80211: 5490000 KHz - 5710000 KHz @  KHz), (N/A mBi, 2700 mBm)
Sep 28 23:42:57 Pasokon kernel: [  393.033268] cfg80211: Disabling freq 5745 MHz
Sep 28 23:42:57 Pasokon kernel: [  393.033272] cfg80211: Disabling freq 5765 MHz
Sep 28 23:42:57 Pasokon kernel: [  393.033276] cfg80211: Disabling freq 5785 MHz
Sep 28 23:42:57 Pasokon kernel: [  393.033279] cfg80211: Disabling freq 5805 MHz
Sep 28 23:42:57 Pasokon kernel: [  393.033283] cfg80211: Disabling freq 5825 MHz
Sep 28 23:42:57 Pasokon kernel: [  393.033293] cfg80211: World regulatory domain updated:
Sep 28 23:42:57 Pasokon kernel: [  393.033297] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Sep 28 23:42:57 Pasokon kernel: [  393.033304] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 28 23:42:57 Pasokon kernel: [  393.033310] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Sep 28 23:42:57 Pasokon kernel: [  393.033315] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Sep 28 23:42:57 Pasokon kernel: [  393.033321] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 28 23:42:57 Pasokon kernel: [  393.033327] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 28 23:42:57 Pasokon NetworkManager[817]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Sep 28 23:43:00 Pasokon wpa_supplicant[884]: Trying to associate with 8a:8b:c5:d4:a6:7a (SSID='FreeWifi' freq=2462 MHz)
Sep 28 23:43:00 Pasokon NetworkManager[817]: <info> (wlan0): supplicant connection state:  scanning -> associating
Sep 28 23:43:00 Pasokon kernel: [  396.074146] wlan0: authenticate with 8a:8b:c5:d4:a6:7a (try 1)
Sep 28 23:43:00 Pasokon kernel: [  396.076176] wlan0: authenticated
Sep 28 23:43:00 Pasokon kernel: [  396.076195] wlan0: associate with 8a:8b:c5:d4:a6:7a (try 1)
Sep 28 23:43:00 Pasokon wpa_supplicant[884]: Associated with 8a:8b:c5:d4:a6:7a
Sep 28 23:43:00 Pasokon wpa_supplicant[884]: CTRL-EVENT-CONNECTED - Connection to 8a:8b:c5:d4:a6:7a completed (reauth) [id=0 id_str=]
Sep 28 23:43:00 Pasokon kernel: [  396.085323] wlan0: RX AssocResp from 8a:8b:c5:d4:a6:7a (capab=0x401 status=0 aid=2)
Sep 28 23:43:00 Pasokon kernel: [  396.085327] wlan0: associated
Sep 28 23:43:00 Pasokon NetworkManager[817]: <info> (wlan0): supplicant connection state:  associating -> associated
Sep 28 23:43:00 Pasokon NetworkManager[817]: <info> (wlan0): supplicant connection state:  associated -> completed
Sep 28 23:43:11 Pasokon dhclient: DHCPREQUEST of 78.251.183.141 on wlan0 to 78.251.255.254 port 67
Sep 28 23:43:11 Pasokon dhclient: DHCPACK of 78.251.183.141 from 78.251.255.254
Sep 28 23:43:11 Pasokon dhclient: bound to 78.251.183.141 -- renewal in 58 seconds.
Sep 28 23:44:09 Pasokon dhclient: DHCPREQUEST of 78.251.183.141 on wlan0 to 78.251.255.254 port 67
Sep 28 23:44:09 Pasokon dhclient: DHCPACK of 78.251.183.141 from 78.251.255.254
Sep 28 23:44:09 Pasokon dhclient: bound to 78.251.183.141 -- renewal in 52 seconds.
Sep 28 23:44:30 Pasokon kernel: [  486.028024] CE: hpet increased min_delta_ns to 20113 nsec
Sep 28 23:45:01 Pasokon dhclient: DHCPREQUEST of 78.251.183.141 on wlan0 to 78.251.255.254 port 67
Sep 28 23:45:01 Pasokon dhclient: DHCPACK of 78.251.183.141 from 78.251.255.254
Sep 28 23:45:01 Pasokon dhclient: bound to 78.251.183.141 -- renewal in 57 seconds.
Sep 28 23:45:58 Pasokon dhclient: DHCPREQUEST of 78.251.183.141 on wlan0 to 78.251.255.254 port 67
Sep 28 23:45:58 Pasokon dhclient: DHCPACK of 78.251.183.141 from 78.251.255.254
Sep 28 23:45:58 Pasokon dhclient: bound to 78.251.183.141 -- renewal in 60 seconds.
Sep 28 23:46:27 Pasokon kernel: [  603.338089] ath: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x42000020 DMADBG_7=0x00006040
Sep 28 23:46:27 Pasokon kernel: [  603.338098] ath: Could not stop RX, we could be confusing the DMA engine when we start RX up
Sep 28 23:46:58 Pasokon dhclient: DHCPREQUEST of 78.251.183.141 on wlan0 to 78.251.255.254 port 67
Sep 28 23:46:58 Pasokon dhclient: DHCPACK of 78.251.183.141 from 78.251.255.254
Sep 28 23:46:58 Pasokon dhclient: bound to 78.251.183.141 -- renewal in 60 seconds.
```

It's pretty much always the same message

Do you guys have any idea ?

Thanks

---

