---
title: "WPA Problem - iBook G4 / Airport Extreme"
date: 2006-08-05
forum: Apple PPC Users
---

### Post by moofbong on 2006-08-05
Hey - 

Just installed Ubuntu on my iBook yesterday and I managed to get NetworkManager installed and working properly for unencrypted wifi, but when I try to use WPA, the card seems to cut in and out and never gets a DHCP lease.

I get the following messages repeatedly in /var/log/messages:

```
Aug  4 20:49:28 pegasus kernel: [ 2954.573961] SoftMAC: Open Authentication completed with 00:0c:41:f2:9d:f0
Aug  4 20:49:32 pegasus kernel: [ 2958.595810] SoftMAC: Open Authentication completed with 00:0c:41:f2:9d:f0
Aug  4 20:49:36 pegasus kernel: [ 2962.617804] SoftMAC: Open Authentication completed with 00:0c:41:f2:9d:f0
Aug  4 20:49:40 pegasus kernel: [ 2966.640006] SoftMAC: Open Authentication completed with 00:0c:41:f2:9d:f0
Aug  4 20:49:44 pegasus kernel: [ 2970.662389] SoftMAC: Open Authentication completed with 00:0c:41:f2:9d:f0
Aug  4 20:49:48 pegasus kernel: [ 2974.684100] SoftMAC: Open Authentication completed with 00:0c:41:f2:9d:f0
Aug  4 20:49:52 pegasus kernel: [ 2978.705887] SoftMAC: Open Authentication completed with 00:0c:41:f2:9d:f0
Aug  4 20:49:56 pegasus kernel: [ 2982.727995] SoftMAC: Open Authentication completed with 00:0c:41:f2:9d:f0
Aug  4 20:50:01 pegasus kernel: [ 2986.749878] SoftMAC: Open Authentication completed with 00:0c:41:f2:9d:f0
```

Has anyone had luck getting WPA to work reliably on a G4 iBook?  Is there some way of getting additional debug output from NetworkManager or the kernel driver?  Is there something obvious I'm missing?

Thanks,
moofbong

---

### Post by APU on 2006-08-06
I also tried NetworkManager as well as Wifi Radar to connect to an WPA secured Wireless Network but could not get it to work too. It seems that both applications still have problems when using WPA so I had to take the manual path and configure everything in the networking config files. Now i can connect to the wireless network by issuing "sudo ifup eth1" in the therminal and stop the wireless card by using "sudo ifdown eth1". I have also prepared several /etc/network/interfaces files which I can use to have different network setups in different locations (what NetworkManager should normally do)

You can find hints on how to configure everything from the Terminal at various places on the net. I don´t really have a good english source ready since I used instructions written in german but I can give you a short intro on how to configure everything.

You need to have the /etc/wpa_supplicant.conf file set up with your wireless network info:

```

#/etc/wpa_supplicant/wpa_supplicant.conf
ctrl_interface=/var/run/wpa_supplicant
network={
        ssid="YOUR SSID"
        proto=WPA
        scan_ssid=1
        key_mgmt=WPA-PSK
        psk=YOUR_VERY_SECRET_KEY
}

```
You can get the secret key using wpa key by using "wpa_passphrase YOUR_SSID YOUR_SECRET_WPA_PASSWORD" from the Terminal. SSID is the Name of your wireless network


After you have set up the wpa_supplicant.conf file you have to configure the network interfaces file to use wpa_supplicant when connecting to your WPA secured wireless Network.

```

# /etc/network/interfaces

# This is the loopback device - DO NOT ALTER ANYTHING!
auto lo
iface lo inet loopback



# This is your Ethernet port - configure as needed
# if you uncomment the line starting with "auto" it
# will be activated on system startup. You can always
# activate it by using "sudo ifup eth0" and turning it
# of again by using "sudo ifdown eth0"
# if you use "dhcp" instead of "static" you can delete
# all manual address configuration and get your network
# adress from a dhcp server in the network

#auto eth0
iface eth0 inet static
address 192.168.55.91
netmask 255.255.255.0
gateway 192.168.55.11



# This is your wireless network card (Airport Extreme)
# It will be active after every system startup unless you
# comment out the "auto eth1" line just like in the Ethernet
# section above. You can also use dhcp instead of static network
# address configuration here I suppose but did not test it yet.

auto eth1
iface eth1 inet static
address 192.168.55.90
netmask 255.255.255.0
gateway 192.168.55.11
post-up wpa_supplicant -ieth1 -Dwext -c/etc/wpa_supplicant/wpa_supplicant.conf -Bw
#post-up sleep 5
post-down killall wpa_supplicant
post-down rm -r /var/run/wpa_supplicant/


# Other neworks - not available, not important and not
# active anyway.

#auto eth2
iface eth2 inet dhcp

#auto ath0
iface ath0 inet dhcp

#auto wlan0
iface wlan0 inet dhcp

```

Good Luck!
APU

---

### Post by rasec on 2006-08-06
APU, I have an updated version of libnm-util0 which fixes network managers problem with wpa. To install it, you first have to extract it with gunzip, then you might have to force install it with dpkg. There is only one problem with that package, the ubuntu updater will view it as being outdate so each time you update your system you are going to have to ignore the update to libnm-util0 or just reinstall the package.

Also, there is a work around the network manager problem. If you get the encripted password from wpa_passphrase and you enter that in as your password for network manager you will be able to connect to your network. I believe the syntax for wpa_passphrase is:

```
wpa_passphrase AP "passphrase"
```

where AP is the name of your access point, and passphrase.

If my fix works, can you go over to launchpad.net and look for a libnm-util0 bug report and acknowledge that there is a problem to libnm-util0 confirm that my fix works. Thanks.

---

### Post by rasec on 2006-08-06
moofbong, network manager spits out a lot of debug info, maybe even too much for normal usage. Look at /var/log/syslog. You might want to grep it for NetworkManager or something like that, or just cat the file after you try to connect to your network.

---

### Post by moofbong on 2006-08-06
I tried using this new package and it still seems to do the exact same thing as before. :-/


> **rasec said:**
> APU, I have an updated version of libnm-util0 which fixes network managers problem with wpa. To install it, you first have to extract it with gunzip, then you might have to force install it with dpkg. There is only one problem with that package, the ubuntu updater will view it as being outdate so each time you update your system you are going to have to ignore the update to libnm-util0 or just reinstall the package.

Also, there is a work around the network manager problem. If you get the encripted password from wpa_passphrase and you enter that in as your password for network manager you will be able to connect to your network. I believe the syntax for wpa_passphrase is:

```
wpa_passphrase AP "passphrase"
```

where AP is the name of your access point, and passphrase.

If my fix works, can you go over to launchpad.net and look for a libnm-util0 bug report and acknowledge that there is a problem to libnm-util0 confirm that my fix works. Thanks.

---

### Post by moofbong on 2006-08-06
You're not kidding about the debug output...  It looks like "WPA: 4-Way Handshake failed - pre-shared key may be incorrect" is of some interest, however I am 100% sure that the password is correct.

After that, everything falls apart and it seems to get into a loop trying to connect to MAC address 00:00:00:00:00:00.

I suspect that all this debug output is a little too much, but here goes anyways:

```
Aug  6 20:21:39 pegasus NetworkManager: <information>^ISWITCH: found better connection 'eth0' than current connection 'eth1'. 
Aug  6 20:21:39 pegasus NetworkManager: <information>^IWill activate connection 'eth0/Moof'. 
Aug  6 20:21:39 pegasus NetworkManager: <information>^IDevice eth0 activation scheduled... 
Aug  6 20:21:39 pegasus NetworkManager: <information>^IDeactivating device eth1. 
Aug  6 20:21:40 pegasus NetworkManager: <information>^IActivation (eth0) started... 
Aug  6 20:21:40 pegasus NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Aug  6 20:21:40 pegasus NetworkManager: <information>^Imatch 
Aug  6 20:21:40 pegasus NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Aug  6 20:21:40 pegasus NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Aug  6 20:21:40 pegasus NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Aug  6 20:21:40 pegasus NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Aug  6 20:21:40 pegasus NetworkManager: <information>^IActivation (eth0/wireless): access point 'Moof' is encrypted, but NO valid key exists.  New key needed. 
Aug  6 20:21:40 pegasus NetworkManager: <information>^IActivation (eth0) New wireless user key requested for network 'Moof'. 
Aug  6 20:21:40 pegasus NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Aug  6 20:21:40 pegasus NetworkManager: <information>^Imatch 
Aug  6 20:21:49 pegasus NetworkManager: <information>^IActivation (eth0) New wireless user key for network 'Moof' received. 
Aug  6 20:21:49 pegasus NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Aug  6 20:21:49 pegasus NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Aug  6 20:21:49 pegasus NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Aug  6 20:21:49 pegasus NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Aug  6 20:21:49 pegasus NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Aug  6 20:21:49 pegasus NetworkManager: <information>^IActivation (eth0/wireless): access point 'Moof' is encrypted, and a key exists.  No new key needed. 
Aug  6 20:21:50 pegasus NetworkManager: <information>^ISUP: sending command 'INTERFACE_ADD eth0^I^Iwext^I/var/run/wpa_supplicant^I' 
Aug  6 20:21:50 pegasus NetworkManager: <information>^ISUP: response was 'OK' 
Aug  6 20:21:50 pegasus NetworkManager: <information>^ISUP: sending command 'AP_SCAN 1' 
Aug  6 20:21:50 pegasus NetworkManager: <information>^ISUP: response was 'OK' 
Aug  6 20:21:50 pegasus NetworkManager: <information>^ISUP: sending command 'ADD_NETWORK' 
Aug  6 20:21:50 pegasus NetworkManager: <information>^ISUP: response was '0' 
Aug  6 20:21:50 pegasus NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 ssid 4d6f6f66' 
Aug  6 20:21:50 pegasus NetworkManager: <information>^ISUP: response was 'OK' 
Aug  6 20:21:50 pegasus NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 proto WPA' 
Aug  6 20:21:50 pegasus NetworkManager: <information>^ISUP: response was 'OK' 
Aug  6 20:21:50 pegasus NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
Aug  6 20:21:50 pegasus NetworkManager: <information>^ISUP: response was 'OK' 
Aug  6 20:21:50 pegasus NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 psk <key>' 
Aug  6 20:21:50 pegasus NetworkManager: <information>^ISUP: response was 'OK' 
Aug  6 20:21:50 pegasus NetworkManager: <information>^ISUP: sending command 'ENABLE_NETWORK 0' 
Aug  6 20:21:50 pegasus NetworkManager: <information>^ISUP: response was 'OK' 
Aug  6 20:21:50 pegasus NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): Global control interface '/var/run/wpa_supplicant-global' 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): RX global ctrl_iface - hexdump_ascii(len=49): 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874):      49 4e 54 45 52 46 41 43 45 5f 41 44 44 20 65 74   INTERFACE_ADD et 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874):      68 30 09 09 77 65 78 74 09 2f 76 61 72 2f 72 75   h0__wext_/var/ru 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874):      6e 2f 77 70 61 5f 73 75 70 70 6c 69 63 61 6e 74   n/wpa_supplicant 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874):      09                                                _                
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): CTRL_IFACE GLOBAL INTERFACE_ADD 'eth0^I^Iwext^I/var/run/wpa_supplicant^I' 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): Initializing interface 'eth0' conf 'N/A' driver 'wext' ctrl_interface '/var/run/wpa_supplicant' 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): Initializing interface (2) 'eth0' 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): EAPOL: SUPP_PAE entering state DISCONNECTED 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): EAPOL: KEY_RX entering state NO_KEY_RECEIVE 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): EAPOL: SUPP_BE entering state INITIALIZE 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): EAP: EAP entering state DISABLED 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): EAPOL: External notification - portEnabled=0 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): EAPOL: External notification - portValid=0 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): SIOCGIWRANGE: WE(compiled)=19 WE(source)=18 enc_capa=0xf 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874):   capabilities: key_mgmt 0xf enc 0xf 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): Own MAC address: 00:0a:95:f4:f7:c6 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): wpa_driver_wext_set_wpa 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): =0 key_idx=0 set_tx=0 seq_len=0 key_len=0 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): wpa_driver_wext_set_countermeasures 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): wpa_driver_wext_set_drop_unencrypted 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): Setting scan request: 0 sec 100000 usec 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): Added interface eth0 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): Wireless event: cmd=0x8b06 len=8 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): RX ctrl_iface - hexdump_ascii(len=9): 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874):      41 50 5f 53 43 41 4e 20 31                        AP_SCAN 1        
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): RX ctrl_iface - hexdump_ascii(len=11): 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874):      41 44 44 5f 4e 45 54 57 4f 52 4b                  ADD_NETWORK      
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): CTRL_IFACE: ADD_NETWORK 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): RX ctrl_iface - hexdump_ascii(len=27): 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874):      53 45 54 5f 4e 45 54 57 4f 52 4b 20 30 20 73 73   SET_NETWORK 0 ss 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874):      69 64 20 34 64 36 66 36 66 36 36                  id 4d6f6f66      
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): CTRL_IFACE: SET_NETWORK id=0 name='ssid' value='4d6f6f66' 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): ssid - hexdump_ascii(len=4): 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874):      4d 6f 6f 66                                       Moof             
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): exdump_ascii(len=23): 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874):      53 45 54 5f 4e 45 54 57 4f 52 4b 20 30 20 70 72   SET_NETWORK 0 pr 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874):      6f 74 6f 20 57 50 41                              oto WPA          
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): CTRL_IFACE: SET_NETWORK id=0 name='proto' value='WPA' 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): proto: 0x1 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): RX ctrl_iface - hexdump_ascii(len=30): 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874):      53 45 54 5f 4e 45 54 57 4f 52 4b 20 30 20 6b 65   SET_NETWORK 0 ke 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874):      79 5f 6d 67 6d 74 20 57 50 41 2d 50 53 4b         y_mgmt WPA-PSK   
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): CTRL_IFACE: SET_NETWORK id=0 name='key_mgmt' value='WPA-PSK' 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): key_mgmt: 0x2 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): RX ctrl_iface - hexdump_ascii(len=82): [REMOVED] 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): CTRL_IFACE: SET_NETWORK id=0 name='psk' value='f933797efef108ea509bbae2ea9a72f4ce9ed66efdda87a3196f7c9924cf7ef5' 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): PSK - hexdump(len=32): [REMOVED] 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): RX ctrl_iface - hexdump_ascii(len=16): 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874):      45 4e 41 42 4c 45 5f 4e 45 54 57 4f 52 4b 20 30   ENABLE_NETWORK 0 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): CTRL_IFACE: ENABLE_NETWORK id=0 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): Setting scan request: 0 sec 0 usec 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): State: DISCONNECTED -> SCANNING 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): Starting AP scan (broadcast SSID) 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): RX ctrl_iface - hexdump_ascii(len=6): 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): TACH           
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): CTRL_IFACE monitor attached - hexdump(len=42): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 30 33 38 2d 31 00 00 00 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): Wireless event: cmd=0x8b19 len=8 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): Received 219 bytes of scan results (1 BSSes) 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): Scan results: 1 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): Selecting BSS from priority group 0 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): 0: 00:0c:41:f2:9d:f0 ssid='Moof' wpa_ie_len=24 rsn_ie_len=0 caps=0x11 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874):    selected based on WPA IE 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): Trying to associate with 00:0c:41:f2:9d:f0 (SSID='Moof' freq=0 MHz) 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): CTRL_IFACE monitor send - hexdump(len=42): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 30 33 38 2d 31 00 00 00 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): Cancelling scan request 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): WPA: clearing own WPA/RSN IE 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): Automatic auth_alg selection: 0x1 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): WPA: using IEEE 802.11i/D3.0 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): WPA: clearing AP RSN IE 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): WPA: using GTK TKIP 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): WPA: using PTK TKIP 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): PA-PSK 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): No keys have been configured - skip key clearing 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): wpa_driver_wext_set_drop_unencrypted 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): State: SCANNING -> ASSOCIATING 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): wpa_driver_wext_associate 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): Setting authentication timeout: 10 sec 0 usec 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): EAPOL: External notification - EAP success=0 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): EAPOL: External notification - EAP fail=0 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): EAPOL: External notification - portControl=Auto 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): Wireless event: cmd=0x8b06 len=8 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): Wireless event: cmd=0x8b1a len=13 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): Wireless event: cmd=0x8c02 len=21 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): Custom wireless event: 'authenticated' 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): Wireless event: cmd=0x8b15 len=20 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): Wireless event: new AP: 00:0c:41:f2:9d:f0 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): State: ASSOCIATING -> ASSOCIATED 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): Associated to a new BSS: BSSID=00:0c:41:f2:9d:f0 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): No keys have been configured - skip key clearing 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): Associated with 00:0c:41:f2:9d:f0 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): CTRL_IFACE monitor send - hexdump(len=42): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 30 33 38 2d 31 00 00 00 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): - clear replay counter 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): EAPOL: External notification - portEnabled=0 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): EAPOL: External notification - portValid=0 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): EAPOL: External notification - EAP success=0 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): EAPOL: External notification - portEnabled=1 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): EAPOL: SUPP_PAE entering state CONNECTING 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): EAPOL: SUPP_BE entering state IDLE 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): Setting authentication timeout: 10 sec 0 usec 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): RTM_NEWLINK, IFLA_IFNAME: Interface 'eth0' added 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): RX EAPOL from 00:0c:41:f2:9d:f0 
Aug  6 20:21:50 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 00 b5 c2 0c a4 0a de d4 7c cb fd 77 ab 4a 8e 16 c0 e5 a6 71 97 0c 5d 1a 95 30 ff 30 8c c3 c5 ff ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): Setting authentication timeout: 10 sec 0 usec 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): IEEE 802.1X RX: version=1 type=3 length=95 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874):   EAPOL-Key type=254 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874):  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): State: ASSOCIATED -> 4WAY_HANDSHAKE 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): WPA: RX message 1 of 4-Way Handshake from 00:0c:41:f2:9d:f0 (ver=1) 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): WPA: Renewed SNonce - hexdump(len=32): 32 d2 29 67 3e d8 8d 10 84 f1 5d 38 ea 4d 5f 54 ee a7 00 2c 10 5d 97 35 e1 ec 3f e6 d3 32 e3 4d 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): WPA: PMK - hexdump(len=32): [REMOVED] 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): WPA: PTK - hexdump(len=64): [REMOVED] 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): WPA: Sending EAPOL-Key 2/4 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): WPA: TX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 09 00 20 00 00 00 00 00 00 00 00 32 d2 29 67 3e d8 8d 10 84 f1 5d 38 ea 4d 5f 54 ee a7 00 2c 10 5d 97 35 e1 ec 3f e6 d3 32 e3 4d 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 c6 72 ba e0 24 1b 21 ff 24 2b 35 73 f6 d7 98 af 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874):  from 00:0c:41:f2:9d:f0 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 00 b5 c2 0c a4 0a de d4 7c cb fd 77 ab 4a 8e 16 c0 e5 a6 71 97 0c 5d 1a 95 30 ff 30 8c c3 c5 ff ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): IEEE 802.1X RX: version=1 type=3 length=95 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874):   EAPOL-Key type=254 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 00 b5 c2 0c a4 0a de d4 7c cb fd 77 ab 4a 8e 16 c0 e5 a6 71 97 0c 5d 1a 95 30 ff 30 8c c3 c5 ff ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): WPA: RX message 1 of 4-Way Handshake from 00:0c:41:f2:9d:f0 (ver=1) 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): WPA: PMK - hexdump(len=32): [REMOVED] 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): ump(len=64): [REMOVED] 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): WPA: Sending EAPOL-Key 2/4 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): WPA: TX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 09 00 20 00 00 00 00 00 00 00 00 32 d2 29 67 3e d8 8d 10 84 f1 5d 38 ea 4d 5f 54 ee a7 00 2c 10 5d 97 35 e1 ec 3f e6 d3 32 e3 4d 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 c6 72 ba e0 24 1b 21 ff 24 2b 35 73 f6 d7 98 af 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): RX EAPOL from 00:0c:41:f2:9d:f0 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 00 b5 c2 0c a4 0a de d4 7c cb fd 77 ab 4a 8e 16 c0 e5 a6 71 97 0c 5d 1a 95 30 ff 30 8c c3 c5 ff ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): IEEE 802.1X RX: version=1 type=3 length=95 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874):   EAPOL-Key type=254 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): 97 0c 5d 1a 95 30 ff 30 8c c3 c5 ff ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): WPA: RX message 1 of 4-Way Handshake from 00:0c:41:f2:9d:f0 (ver=1) 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): WPA: PMK - hexdump(len=32): [REMOVED] 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): WPA: PTK - hexdump(len=64): [REMOVED] 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): WPA: Sending EAPOL-Key 2/4 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): WPA: TX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 09 00 20 00 00 00 00 00 00 00 00 32 d2 29 67 3e d8 8d 10 84 f1 5d 38 ea 4d 5f 54 ee a7 00 2c 10 5d 97 35 e1 ec 3f e6 d3 32 e3 4d 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 c6 72 ba e0 24 1b 21 ff 24 2b 35 73 f6 d7 98 af 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): Wireless event: cmd=0x8b19 len=8 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): Received 219 bytes of scan results (1 BSSes) 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): Scan results: 1 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): ng BSS from priority group 0 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): 0: 00:0c:41:f2:9d:f0 ssid='Moof' wpa_ie_len=24 rsn_ie_len=0 caps=0x11 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874):    selected based on WPA IE 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): Already associated with the selected AP. 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): Wireless event: cmd=0x8b15 len=20 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): Wireless event: new AP: 00:00:00:00:00:00 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): WPA: 4-Way Handshake failed - pre-shared key may be incorrect 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): CTRL_IFACE monitor send - hexdump(len=42): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 30 33 38 2d 31 00 00 00 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): Setting scan request: 0 sec 100000 usec 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): Added BSSID 00:0c:41:f2:9d:f0 into blacklist 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): State: 4WAY_HANDSHAKE -> DISCONNECTED 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): EAPOL: External notification - portEnabled=0 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): EAPOL: SUPP_PAE entering state DISCONNECTED 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): EAPOL: SUPP_BE entering state INITIALIZE 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): EAPOL: External notification - portValid=0 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): EAPOL: External notification - EAP success=0 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874):  38 2d 31 00 00 00 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): Wireless event: cmd=0x8b15 len=20 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): Wireless event: new AP: 00:00:00:00:00:00 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): Added BSSID 00:00:00:00:00:00 into blacklist 
Aug  6 20:21:51 pegasus NetworkManager: <information>^Iwpa_supplicant(4874): State: DISCONNECTED -> DISCONNECTED 

```

---

### Post by moofbong on 2006-08-06
It looks like I lied.  Maybe I wasn't *quite* 100% sure that I had the right password.  I think your new library worked.  What, exactly, did you change in it?  I'd be happy to contact the maintainers and vote for incorporating the fix.

Thanks,
moofbong

---

### Post by rasec on 2006-08-06
I had to recompile it with the WORDS_BIGENDIAN flag. I already contacted the debian maintainer and they forwarded the fix to the network manager devs, but I don't know if they are going to backport the fix to the current version of libnm-util. Here is a link to my bug report at launchpad: [https://launchpad.net/distros/ubuntu/+source/network-manager/+bug/52922](https://launchpad.net/distros/ubuntu/+source/network-manager/+bug/52922)

One thing I forgot to mention about my fix, you might need to restart you computer to get network manager to use the updated library.

---

### Post by moofbong on 2006-08-06
I guess that would help on PPC, eh? ;)  Hopefully they backport it, it's just a compile flag...

> **rasec said:**
> I had to recompile it with the WORDS_BIGENDIAN flag. I already contacted the debian maintainer and they forwarded the fix to the network manager devs, but I don't know if they are going to backport the fix to the current version of libnm-util. Here is a link to my bug report at launchpad: [https://launchpad.net/distros/ubuntu/+source/network-manager/+bug/52922](https://launchpad.net/distros/ubuntu/+source/network-manager/+bug/52922)

One thing I forgot to mention about my fix, you might need to restart you computer to get network manager to use the updated library.

---

### Post by sma1 on 2006-11-08
> **rasec said:**
> 
Also, there is a work around the network manager problem. If you get the encrypted password from wpa_passphrase and you enter that in as your password for network manager you will be able to connect to your network. I believe the syntax for wpa_passphrase is:

```
wpa_passphrase AP "passphrase"
```

where AP is the name of your access point, and passphrase.


Thanks! This workaround works for me under Edgy Eft on a 15" Al Powerbook.  If you already entered a password for your WPA protected network, you can change it by using the "Keyring Manager" under the "System / Administration" Menu.

The encrypted password is the long string of numbers output by wpa_password after psk=

```
sma1@powerbook:~$ wpa_passphrase YOUR_AP YourPassword
network={
    ssid="YOUR_AP"
    #psk="YourPassword"
    psk=29fb43809890e704d26f71f082f0e37663660a3c3f87b39130605e8669cce368
}
```

I hope the appropriate patch makes it into an update soon, I had been fighting with this for a long time.

---

### Post by tjr on 2006-11-15
This (text files, library) does not work on my G4 ibook running stock Ubuntu Dapper installed from the DVD (version 6.06.1 LTS to be exact).

Those of you reporting success, would you please specify your exact version numbers of Ubuntu and all the relevant tools, everything you changed manually?

---

