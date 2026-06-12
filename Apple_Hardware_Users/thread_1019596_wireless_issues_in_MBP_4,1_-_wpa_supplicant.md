---
title: "wireless issues in MBP 4,1 - wpa_supplicant"
date: 2008-12-23
forum: Apple Hardware Users
---

### Post by lat2005 on 2008-12-23
My MBP 4,1 has triple boot:
Mac OS X
Windows XP
Ubuntu Intrepid 8.10

I enabled the wireless driver (Broadcom), but I haven't been able to use wpa_supplicant despite configuring it correctly.
I need it because nm-applet (GNOME Network Manager) doesn't work for all the networks I need to connect to.

The error I get is:
ioctl[SIOCSIWMODE]: Device or resource busy

Does anyone know how do I get control and enable wpa_supplicant to work? I tried killing nm0-applet and Network Manager but it doesn't help.

Should I use the BCM driver from the Mac OS X cd? I used this in the past and it worked, but using the driver already given seems better.

Thank you

---

### Post by hajk on 2008-12-24
From my own installation notes on MBP 4,1 using Broadcom wl driver (note: eth1 is the wireless interface!):> 
The ubiquitous network-manager programme can handle my wireless (and wired) connections, which is useful on
the road as it remembers the configurations of wireless APs it has once been connected to. It is a bit slow 
getting connected, so I usually prefer letting wpa_supplicant in roaming mode handle my known wireless connections.
This requires the following stanza in /etc/network/interfaces```

auto eth1
iface eth1 inet manual
    wpa-driver wext
    wpa-roam /etc/wpa_supplicant/wpa_supplicant.conf
iface default inet dhcp
```where the "auto" line protects it from network-manager. Then edit /etc/wpa_supplicant/wpa_supplicant.conf as follows```

ctrl_interface=/var/run/wpa_supplicant
network={
        ssid="MyWPA2ProtectedNetwork"
        psk="MySecretPassPhrase"
}
network={
        ssid="myWorkNetwork"
        scan_ssid=1
        key_mgmt=IEEE8021X
        eap=TTLS
        anonymous_identity="anonymous@mywork.com"
        phase2="auth=PAP"
        identity="myID@mywork.com"
        password="myWorkPassword"
        ca_cert="/usr/share/ca-certificates/WORKnet.com/WORKnet-PCA-Root-CA.pem"
}
network={
        ssid="myHotSpotProvider"
        scan_ssid=1
        key_mgmt=NONE
}
```where I've used some phantasy data (and where I always switch to VPN when logged in at a HotSpot).

The eth1 wireless interface can still be handled by network-manager once the "auto" line in /etc/network/interfaces
is commented out. Note that the interface is handled by wpa_action after it has been brought up as indicated above.
There should be enough info here to adapt to your own setup.

Have fun!

---

