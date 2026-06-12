---
title: "Wireless Connection"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by S15_88 on 2007-06-11
Can Ubuntu connect to a WPA encrypted connection? or only WEP?

---

### Post by steeleyuk on 2007-06-11
That usually depends on whether the wireless card driver supports WPA. What wireless card do you have?

---

### Post by plinydogg on 2007-06-11
Yes, Ubuntu can connect to a WPA connection, but sometimes additional configuation is needed.

---

### Post by plinydogg on 2007-06-11
steeleyuk is right of course: your wireless card must also support WPA...

---

### Post by S15_88 on 2007-06-11
it's a new intel Next-Gen, and i've updated the driver for it but i'm having huge difficulties getting it to work!

---

### Post by S15_88 on 2007-06-11
when u say additional configuration, wat exactly do u have in mind? cause before the system wasn't even recognizing that it was there then when it was able to do that i couldn't see any connections then i couldn't connect to any and now i'm back at square one where it refuses to be recognized! and nothing i've done before is working!  I am a very happy Ubuntu user but this just has me stumped!

---

### Post by hkahwaji on 2007-06-11
Also, you will need to install wpa-supplicant and then configure your card to connect to a WPA-PSK protected wireless network. If you choose to do this from the command line. Here are the steps:

sudo apt-get install wpasupplicant 

On your computer, edit the interfaces file in the /etc/network directory to add the following:

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid <your_wireless_network_ssid>
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk <your-hex-key>

Note: Here is the description of the values that are passed:
Wlan0: is the logical interface for your wireless card
Dhcp: setting the DHCP protocol
wpa-driver: that is Linux wireless extensions (generic)
wpa-ssid: Your wireless network SSID
wpa-ap-scan: Values can be either 1 or 2. Set to 1 if you are broadcasting the SSID or 2 if you are not broadcasting the SSID
wpa-proto: WPA if you have WPA(1) set up at your AP or RSN if you have WPA(2) set up at AP
wpa-pairwise: TKIP if wpa-proto is WPA and CCMP if you have wpa-proto set to RSN
wpa-group: TKIP if wpa-proto is WPA and CCMP if you have wpa-proto set to RSN
wpa-key-mgmt: WPA-PSK  (Authentication via pre-shared key)
or 
"WPA-EAP" = Authentication via enterprise authentication server.

Note: You will need to pass the a hex key for wpa-psk, to obtain the hex equivalent to the passphrase that you set up at the AP. Open a terminal and run the following command:

	wpa_passphrase <your-wireless-essid> <your-passphrase>

You should get an output equivalent to this:

network={
        ssid="linksys-n"
        #psk="test1234"
        psk=7270ebe2783ca7af537cc1a618e6306169a8aa1f142c1877f766d1a4a6da6cbd

The psk value is your hex key. Copy and paste that to the wpa-psk key value.

Save the file and restart your networking services using the following command:

	sudo /etc/init.d/networking restart

You now should be able to obtain an IP address



FYI: Some information listed here are listed in the tutorial that Weiman liste

---

### Post by p_quarles on 2007-06-11
[COLOR=Black]What have you done so far? There is a tutorial on setting this up under the Networking section of the forums. Have you tried those techniques?

Anyway, I don't have much experience with this, but I need to learn quick, as my new laptop will be here any day now. 
[/COLOR]

---

