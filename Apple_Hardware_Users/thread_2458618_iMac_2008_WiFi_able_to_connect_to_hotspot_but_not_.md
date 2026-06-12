---
title: "iMac 2008 WiFi able to connect to hotspot but not router"
date: 2021-02-28
forum: Apple Hardware Users
---

### Post by chinarut2 on 2021-02-28
Hi!  I could use a bit of help in how to troubleshoot a problem we're having connecting our iMac 2008 on Ubuntu 20.04.2 LTS to our router.


[LIST=1]
[*]I verified the WiFi adaptor connects to the router in 10.11.6 (the last OSX supported) 
[*]I verified the Broadcom 802.11 Linux STA proprietary driver for AirPort Extreme is installed. 
[*]I also verified the WiFi adaptor connects to a different network while in Ubuntu (in my case, a hotspot created with my Pixel 3a) 
[/LIST]

I can't figure out how to interpret these events from syslog - if i had to guess, it's unable to acquire a DCHP address from the router?

```

Feb 28 11:34:42 Krungthep NetworkManager[649]: <info>  [1614540882.0518] device (wls4): Activation: starting connection 'R2D2 1' ($UUID)
Feb 28 11:34:42 Krungthep NetworkManager[649]: <info>  [1614540882.0520] audit: op="connection-activate" uuid="$UUID" name="R2D2 1" pid=2701 uid=1001 result="success"
Feb 28 11:34:42 Krungthep NetworkManager[649]: <info>  [1614540882.0522] device (wls4): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Feb 28 11:34:42 Krungthep NetworkManager[649]: <info>  [1614540882.0534] device (wls4): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Feb 28 11:34:42 Krungthep NetworkManager[649]: <info>  [1614540882.0590] device (wls4): Activation: (wifi) access point 'R2D2 1' has security, but secrets are required.
Feb 28 11:34:42 Krungthep NetworkManager[649]: <info>  [1614540882.0590] device (wls4): state change: config -> need-auth (reason 'none', sys-iface-state: 'managed')
Feb 28 11:34:42 Krungthep NetworkManager[649]: <info>  [1614540882.0593] sup-iface[0x55810e28b900,wls4]: wps: type pbc start...
Feb 28 11:34:42 Krungthep NetworkManager[649]: <info>  [1614540882.0623] device (wls4): state change: need-auth -> prepare (reason 'none', sys-iface-state: 'managed')
Feb 28 11:34:42 Krungthep NetworkManager[649]: <info>  [1614540882.0628] device (wls4): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Feb 28 11:34:42 Krungthep NetworkManager[649]: <info>  [1614540882.0715] device (wls4): Activation: (wifi) connection 'R2D2 1' has security, and secrets exist.  No new secrets needed.
Feb 28 11:34:42 Krungthep NetworkManager[649]: <info>  [1614540882.0716] Config: added 'ssid' value 'R2D2'
Feb 28 11:34:42 Krungthep NetworkManager[649]: <info>  [1614540882.0717] Config: added 'scan_ssid' value '1'
Feb 28 11:34:42 Krungthep NetworkManager[649]: <info>  [1614540882.0717] Config: added 'bgscan' value 'simple:30:-70:86400'
Feb 28 11:34:42 Krungthep NetworkManager[649]: <info>  [1614540882.0717] Config: added 'key_mgmt' value 'WPA-PSK WPA-PSK-SHA256'
Feb 28 11:34:42 Krungthep NetworkManager[649]: <info>  [1614540882.0717] Config: added 'psk' value '<hidden>'
Feb 28 11:34:42 Krungthep NetworkManager[649]: <info>  [1614540882.1021] device (wls4): supplicant interface state: disconnected -> scanning
Feb 28 11:34:43 Krungthep wpa_supplicant[691]: wls4: Trying to associate with $MAC (SSID='R2D2' freq=5785 MHz)
Feb 28 11:34:43 Krungthep NetworkManager[649]: <info>  [1614540883.8805] device (wls4): supplicant interface state: scanning -> associating
Feb 28 11:34:43 Krungthep wpa_supplicant[691]: wls4: Associated with $MAC
Feb 28 11:34:43 Krungthep wpa_supplicant[691]: wls4: CTRL-EVENT-SUBNET-STATUS-UPDATE status=0
Feb 28 11:34:43 Krungthep wpa_supplicant[691]: wls4: CTRL-EVENT-REGDOM-CHANGE init=COUNTRY_IE type=COUNTRY alpha2=CN
Feb 28 11:34:43 Krungthep wpa_supplicant[691]: wls4: WPA: Key negotiation completed with $MAC [PTK=CCMP GTK=CCMP]
Feb 28 11:34:43 Krungthep wpa_supplicant[691]: wls4: CTRL-EVENT-CONNECTED - Connection to $MAC completed [id=0 id_str=]
Feb 28 11:34:43 Krungthep wpa_supplicant[691]: bgscan simple: Failed to enable signal strength monitoring
Feb 28 11:34:43 Krungthep NetworkManager[649]: <info>  [1614540883.9854] device (wls4): supplicant interface state: associating -> completed
Feb 28 11:34:43 Krungthep NetworkManager[649]: <info>  [1614540883.9854] device (wls4): Activation: (wifi) Stage 2 of 5 (Device Configure) successful. Connected to wireless network "R2D2"
Feb 28 11:34:43 Krungthep NetworkManager[649]: <info>  [1614540883.9858] device (wls4): state change: config -> ip-config (reason 'none', sys-iface-state: 'managed')
Feb 28 11:34:43 Krungthep NetworkManager[649]: <info>  [1614540883.9866] dhcp4 (wls4): activation: beginning transaction (timeout in 45 seconds)
Feb 28 11:34:43 Krungthep avahi-daemon[640]: Joining mDNS multicast group on interface wls4.IPv6 with address $IPv6.
Feb 28 11:34:43 Krungthep avahi-daemon[640]: New relevant interface wls4.IPv6 for mDNS.
Feb 28 11:34:43 Krungthep avahi-daemon[640]: Registering new address record for $IPv6 on wls4.*.
Feb 28 11:34:46 Krungthep systemd-resolved[589]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Feb 28 11:34:47 Krungthep systemd-resolved[589]: message repeated 2 times: [ Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.]
Feb 28 11:34:50 Krungthep /usr/lib/gdm3/gdm-x-session[1396]: (EE) client bug: timer event9 debounce short: scheduled expiry is in the past (-8ms), your system is too slow
Feb 28 11:35:29 Krungthep NetworkManager[649]: <warn>  [1614540929.3987] dhcp4 (wls4): request timed out
Feb 28 11:35:29 Krungthep NetworkManager[649]: <info>  [1614540929.3989] dhcp4 (wls4): state changed unknown -> timeout
Feb 28 11:35:29 Krungthep NetworkManager[649]: <info>  [1614540929.3992] device (wls4): state change: ip-config -> failed (reason 'ip-config-unavailable', sys-iface-state: 'managed')
Feb 28 11:35:29 Krungthep NetworkManager[649]: <warn>  [1614540929.4081] device (wls4): Activation: failed for connection 'R2D2 1'
Feb 28 11:35:29 Krungthep NetworkManager[649]: <info>  [1614540929.4086] device (wls4): state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')
Feb 28 11:35:29 Krungthep avahi-daemon[640]: Withdrawing address record for $IPv6 on wls4.
Feb 28 11:35:29 Krungthep avahi-daemon[640]: Leaving mDNS multicast group on interface wls4.IPv6 with address $IPv6.
Feb 28 11:35:29 Krungthep avahi-daemon[640]: Interface wls4.IPv6 no longer relevant for mDNS.
Feb 28 11:35:29 Krungthep NetworkManager[649]: <info>  [1614540929.4316] dhcp4 (wls4): canceled DHCP transaction
Feb 28 11:35:29 Krungthep NetworkManager[649]: <info>  [1614540929.4316] dhcp4 (wls4): state changed timeout -> done
Feb 28 11:35:29 Krungthep wpa_supplicant[691]: wls4: CTRL-EVENT-DISCONNECTED bssid=$MAC reason=3 locally_generated=1
Feb 28 11:35:29 Krungthep wpa_supplicant[691]: nl80211: Was expecting local disconnect but got another disconnect event first
Feb 28 11:35:29 Krungthep wpa_supplicant[691]: wls4: CTRL-EVENT-REGDOM-CHANGE init=CORE type=WORLD
Feb 28 11:35:29 Krungthep wpa_supplicant[691]: wls4: Reject scan trigger since one is already pending
Feb 28 11:35:29 Krungthep NetworkManager[649]: <warn>  [1614540929.4601] sup-iface[0x55810e28b900,wls4]: connection disconnected (reason -3)
Feb 28 11:35:29 Krungthep NetworkManager[649]: <info>  [1614540929.4602] device (wls4): supplicant interface state: completed -> disconnected
Feb 28 11:35:30 Krungthep wpa_supplicant[691]: wls4: CTRL-EVENT-REGDOM-CHANGE init=BEACON_HINT type=UNKNOWN
Feb 28 11:35:30 Krungthep NetworkManager[649]: <info>  [1614540930.4038] device (wls4): supplicant interface state: disconnected -> scanning
Feb 28 11:35:31 Krungthep systemd-resolved[589]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Feb 28 11:35:31 Krungthep systemd-resolved[589]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Feb 28 11:35:32 Krungthep wpa_supplicant[691]: wls4: CTRL-EVENT-REGDOM-CHANGE init=BEACON_HINT type=UNKNOWN
Feb 28 11:35:32 Krungthep NetworkManager[649]: <info>  [1614540932.2147] device (wls4): supplicant interface state: scanning -> disconnected
Feb 28 11:35:32 Krungthep NetworkManager[649]: <info>  [1614540932.4020] device (wls4): supplicant interface state: disconnected -> scanning
Feb 28 11:35:34 Krungthep wpa_supplicant[691]: wls4: CTRL-EVENT-REGDOM-CHANGE init=BEACON_HINT type=UNKNOWN
Feb 28 11:35:34 Krungthep NetworkManager[649]: <info>  [1614540934.2766] device (wls4): supplicant interface state: scanning -> disconnected
Feb 28 11:35:36 Krungthep wpa_supplicant[691]: wls4: CTRL-EVENT-REGDOM-CHANGE init=BEACON_HINT type=UNKNOWN
Feb 28 11:35:36 Krungthep NetworkManager[649]: <info>  [1614540936.4076] device (wls4): supplicant interface state: disconnected -> scanning
Feb 28 11:35:37 Krungthep /usr/lib/gdm3/gdm-x-session[1396]: (EE) client bug: timer event9 debounce: scheduled expiry is in the past (-5ms), your system is too slow
Feb 28 11:35:37 Krungthep /usr/lib/gdm3/gdm-x-session[1396]: (EE) client bug: timer event9 debounce short: scheduled expiry is in the past (-18ms), your system is too slow
Feb 28 11:35:38 Krungthep NetworkManager[649]: <info>  [1614540938.1502] device (wls4): supplicant interface state: scanning -> disconnected

```

Next, I tried to assign a static IP:
[IMG]https://i.imgur.com/ObwKpcp.png[/IMG]
EDIT: I took DNS 192.168.0.125 out above just to make sure this isn't the cause.

Even though Ubuntu acknowledges it is connected (and a link speed of 216 Mbps), I can't open up a website like google.com unless I turn wired internet back on (my workaround)

What other steps might I take to troubleshoot this further?

Thanks for any help!

---

### Post by QIII on 2021-02-28
Moved to  Apple Hardware Users.

---

### Post by chinarut2 on 2021-03-11
thanks @QIII for letting me know there is a Apple hardware specific forum.

ok I thought I&#8217;d post some progress after fiddling around with a different machine (2008 MacBook 2,1) and isolating the issue (and a suitable workaround).

What I discovered is Ubuntu 20.04.2 LTS is not fetching the DNS server IP correctly.

If I configure a static 192.168.0.1 IP for my DNS server, the DHCP server is automatically able to assign an IP address.

I discovered this because I noticed my Ethernet connection stopped working today and this is how I fixed it.

It doesn&#8217;t appear to be the hardware as I can reboot the MacBook into both OS X 10.11.6 and Windows 10 and both systems are able to get both an DHCP and DNS IPs from the router automatically on both interfaces (wired and wireless)

I am not in front of my iMac right now and suspect this workaround will work - it is the same behavior.

What would prevent Ubuntu from fetching the DNS IP address automatically?

How might I help troubleshoot and isolate the cause of this further outside of the logs I&#8217;ve attached in my original post?

EDIT: my best guess is it&#8217;s related to the DNS code that implements the workaround for [COLOR=#000000][FONT=&amp]DVE-2018-0001[/FONT][/COLOR]

---

### Post by chinarut2 on 2021-03-12
Hmm - I'm back at my iMac and just setting the a static IP for DNS doesn't fix it like it did on my MacBook.

If anyone has any ideas based on the log file in my original post, please let me know.

Everything works fine using our Ethernet port (including DHCP) so it's something specific to the Ubuntu driver for the WiFi card in this 2008 iMac.

---

