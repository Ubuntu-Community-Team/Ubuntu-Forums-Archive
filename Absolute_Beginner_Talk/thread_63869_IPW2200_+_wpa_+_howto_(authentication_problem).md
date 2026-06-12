---
title: "IPW2200 + wpa + howto (authentication problem)"
date: 2005-09-09
forum: Absolute Beginner Talk
---

### Post by Mint Sauce on 2005-09-09
First post so hullo all :D.

I only installed kubuntu yesterday (first linux install) and i've followed the howto to get my wlan setup, messed with all the configs that might help me connect, but according to kwifi my pc authenicates and then drops, over and over.root@SHUI:~/Downloads/ipw2200fw# dmesg | grep ipw
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
ipw2200: failed to send CARD_DISABLE command
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
root@SHUI:~/Downloads/ipw2200fw# I have no idea what to do so has anyone got any suggestions. Tried search but i can't find anything specific to my problem. Thanks.

If you need any log, errors or whatever please tell me the command to obtain it (cus i sux0r at linux :D..... atm anywho)

.:EDIT:.
[THIS](http://ipw2200.sourceforge.net/faq.php#qa_1_1) would suggest that i need [THIS](http://rfswitch.sourceforge.net/)? My laptop has a switch to change wlan status (turn it on/off), is this needed?  :? The switch works too btw!

.:edit2:.
iwconfig show various out puts depending on whether it's just dropped, or just autenticated (never stable tho). Anyhoo i just got this output

```
eth1      IEEE 802.11g  ESSID:"Willorie"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:11:F5:54:0B:59
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=90/100  Signal level=-39 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:18   Missed beacon:6
```

The encyption key:off is what i'm worried about. 

wpa_supplicant.conf:
```
ctrl_interface=/var/run/wpa_supplicant
ap_scan=2

network={
       ssid="Willorie"
       scan_ssid=1
       proto=WPA
       key_mgmt=WPA-PSK
       pairwise=TKIP
       psk="J7DHEN58KN"
}
```

Also the encoding when this file is saved is set to utf8, is that correct?

Thanks.

.:edit3:.

dmesg grep | ipw:

```
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
ipw2200: failed to send CARD_DISABLE command
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
```

This wasn't happening before. Sorry this post is getting long, but i really need to get this working, any ideas? TIA.

---

