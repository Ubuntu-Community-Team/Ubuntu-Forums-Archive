---
title: "macbook air can not activate wifi connection"
date: 2015-06-20
forum: Apple Hardware Users
---

### Post by ValentynPrumers on 2015-06-20
Hi,

For the past couple of days i have been struggling getting the wireless card of my macbookair1,1 to work. After trying several drivers
i found one that works: b43-firmware-installer. When i load the module and i click on the network icon i see all the available wifi networks.

Booyeah fist pump, right? Wrong :P when i try to connect to one it takes a minute and then nothing happens. When i check the syslog (see
below) it seems  the connection cant be activated. Any suggestions how to fix this?

I tried networks with passwords (i get a password prompt and the authentication goes fine, but then it hangs ) and without. Below an attempt to
connect to a network without password.

```

Jan  1 01:01:56 frankp-MacBookAir NetworkManager[841]: <info> (wlan0) supports 4 scan SSIDs
Jan  1 01:01:56 frankp-MacBookAir NetworkManager[841]: <info> (wlan0): supplicant interface state: starting -> ready
Jan  1 01:01:56 frankp-MacBookAir NetworkManager[841]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jan  1 01:01:56 frankp-MacBookAir NetworkManager[841]: <warn> Trying to remove a non-existant call id.
Jan  1 01:01:56 frankp-MacBookAir NetworkManager[841]: <info> (wlan0): supplicant interface state: ready -> disconnected
Jan  1 01:01:56 frankp-MacBookAir NetworkManager[841]: <info> (wlan0) supports 4 scan SSIDs
Jan  1 01:02:06 frankp-MacBookAir NetworkManager[841]: <info> (wlan0): supplicant interface state: disconnected -> inactive
Jan  1 01:02:08 frankp-MacBookAir blueman-mechanism: Exiting 
Jan  1 01:02:22 frankp-MacBookAir NetworkManager[841]: <info> Activation (wlan0) starting connection 'linksys'
Jan  1 01:02:22 frankp-MacBookAir NetworkManager[841]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jan  1 01:02:22 frankp-MacBookAir NetworkManager[841]: <info> NetworkManager state is now CONNECTING
Jan  1 01:02:22 frankp-MacBookAir NetworkManager[841]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan  1 01:02:22 frankp-MacBookAir NetworkManager[841]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan  1 01:02:22 frankp-MacBookAir NetworkManager[841]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan  1 01:02:22 frankp-MacBookAir NetworkManager[841]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan  1 01:02:22 frankp-MacBookAir NetworkManager[841]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan  1 01:02:22 frankp-MacBookAir NetworkManager[841]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jan  1 01:02:22 frankp-MacBookAir NetworkManager[841]: <info> Activation (wlan0/wireless): connection 'linksys' requires no security.  No secrets needed.
Jan  1 01:02:22 frankp-MacBookAir NetworkManager[841]: <info> Config: added 'ssid' value 'linksys'
Jan  1 01:02:22 frankp-MacBookAir NetworkManager[841]: <info> Config: added 'scan_ssid' value '1'
Jan  1 01:02:22 frankp-MacBookAir NetworkManager[841]: <info> Config: added 'bssid' value '00:12:17:dc:fc:03'
Jan  1 01:02:22 frankp-MacBookAir NetworkManager[841]: <info> Config: added 'key_mgmt' value 'NONE'
Jan  1 01:02:22 frankp-MacBookAir NetworkManager[841]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan  1 01:02:22 frankp-MacBookAir NetworkManager[841]: <info> Config: set interface ap_scan to 1
Jan  1 01:01:51 frankp-MacBookAir wpa_supplicant[1014]: message repeated 3 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan  1 01:02:29 frankp-MacBookAir wpa_supplicant[1014]: wlan0: SME: Trying to authenticate with 00:12:17:dc:fc:03 (SSID='linksys' freq=2462 MHz)
Jan  1 01:02:29 frankp-MacBookAir kernel: [  130.013859] wlan0: authenticate with 00:12:17:dc:fc:03
Jan  1 01:02:29 frankp-MacBookAir NetworkManager[841]: <info> (wlan0): supplicant interface state: inactive -> authenticating
Jan  1 01:02:29 frankp-MacBookAir kernel: [  130.024668] wlan0: send auth to 00:12:17:dc:fc:03 (try 1/3)
Jan  1 01:02:29 frankp-MacBookAir kernel: [  130.026704] wlan0: authenticated
Jan  1 01:02:34 frankp-MacBookAir kernel: [  135.029993] wlan0: aborting authentication with 00:12:17:dc:fc:03 by local choice (Reason: 3=DEAUTH_LEAVING)
Jan  1 01:02:34 frankp-MacBookAir NetworkManager[841]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Jan  1 01:02:35 frankp-MacBookAir NetworkManager[841]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jan  1 01:02:45 frankp-MacBookAir kernel: [  145.146881] wlan0: authenticate with 00:12:17:dc:fc:03
Jan  1 01:02:45 frankp-MacBookAir NetworkManager[841]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jan  1 01:02:45 frankp-MacBookAir kernel: [  145.152553] wlan0: send auth to 00:12:17:dc:fc:03 (try 1/3)
Jan  1 01:02:45 frankp-MacBookAir kernel: [  145.155625] wlan0: authenticated
Jan  1 01:02:47 frankp-MacBookAir NetworkManager[841]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Jan  1 01:02:47 frankp-MacBookAir NetworkManager[841]: <info> (wlan0): device state change: config -> failed (reason 'SSID not found') [50 120 53]
Jan  1 01:02:47 frankp-MacBookAir NetworkManager[841]: <info> NetworkManager state is now DISCONNECTED
Jan  1 01:02:47 frankp-MacBookAir NetworkManager[841]: <warn> Activation (wlan0) failed for connection 'linksys'
Jan  1 01:02:45 frankp-MacBookAir wpa_supplicant[1014]: wlan0: SME: Trying to authenticate with 00:12:17:dc:fc:03 (SSID='linksys' freq=2462 MHz)
Jan  1 01:02:47 frankp-MacBookAir wpa_supplicant[1014]: wlan0: CTRL-EVENT-DISCONNECTED bssid=00:12:17:dc:fc:03 reason=3 locally_generated=1
Jan  1 01:02:47 frankp-MacBookAir kernel: [  148.004770] wlan0: aborting authentication with 00:12:17:dc:fc:03 by local choice (Reason: 3=DEAUTH_LEAVING)
Jan  1 01:02:47 frankp-MacBookAir NetworkManager[841]: <warn> Connection disconnected (reason -3)
Jan  1 01:02:47 frankp-MacBookAir NetworkManager[841]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Jan  1 01:02:47 frankp-MacBookAir NetworkManager[841]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jan  1 01:02:47 frankp-MacBookAir NetworkManager[841]: <info> (wlan0): deactivating device (reason 'none') [0]
Jan  1 01:02:50 frankp-MacBookAir wpa_supplicant[1014]: wlan0: Reject scan trigger since one is already pending



```

---

### Post by mfox on 2015-06-20
I'm no expert on this, but one thing you might try is to use different network software other than NetworkManager. I'm thinking of either KNetworkManager (KDE) or WICD. I seem to recall having different results with different network managers when I first tried Ubuntu on an older Mac.  Also, although I never installed a distro on my 2013 MacBook Air, I got a network connection with Elementary running as a live disk when I couldn't with Ubuntu or openSUSE. This is probably because Elementary loads the necessary Broadcom driver, but it may also be the network manager or firmware that distro uses.

---

