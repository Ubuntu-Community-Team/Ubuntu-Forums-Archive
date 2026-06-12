---
title: "Setting up wireless WG511T in DSL"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by huzzak on 2008-02-12
Okay, so this is a plea for help.

I am trying to get Damn Small Linux running on my nine year old laptop that I am turning into a digital photo frame. I have a NetGear WG511T wireless pci card that seems to be recognized by the system, but I can't figure out how to configure it so that it will connect to my router. It is listed as ath0 when I type iwconfig. I need to set it up so that it will connect using WPA. Can anyone suggest what I ought to do?

I got madwifi installed and wpa_supplicant is configured I think. Here is the output if someone could help me decipher it and figure out maybe where I am going wrong. Thanks!

Results of this command:
sudo wpa_supplicant -dd -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf

Is as follows:

```
Initializing interface 'ath0' conf '/etc/wpa_supplicant.conf' driver 'madwifi'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Line: 1 - start of a new network block
ssid - hexdump_ascii(len=8):
     4c 75 74 65 73 20 31 31                           Lutes 11        
PSK - hexdump(len=32): [REMOVED]
key_mgmt: 0x2
proto: 0x1
Priority group 0
   id=0 ssid='Lutes 11'
Initializing interface (2) 'ath0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Own MAC address: 00:18:4d:80:d4:af
wpa_driver_madwifi_set_wpa: enabled=1
wpa_driver_madwifi_del_key: keyidx=0
wpa_driver_madwifi_del_key: keyidx=1
wpa_driver_madwifi_del_key: keyidx=2
wpa_driver_madwifi_del_key: keyidx=3
wpa_driver_madwifi_set_countermeasures: enabled=0
wpa_driver_madwifi_set_drop_unencrypted: enabled=1
Setting scan request: 0 sec 100000 usec
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK, IFLA_IFNAME: Interface 'wifi0' added
RTM_NEWLINK, IFLA_IFNAME: Interface 'ath0' added
RTM_NEWLINK, IFLA_IFNAME: Interface 'ath0' added
Starting AP scan (broadcast SSID)
Wireless event: cmd=0x8b1a len=12
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Wireless event: cmd=0x8b19 len=12
Received 3833 bytes of scan results (15 BSSes)
Scan results: 15
Selecting BSS from priority group 0
0: 00:16:b6:de:54:fc ssid='Mike Lloyd' wpa_ie_len=26 rsn_ie_len=0
   skip - SSID mismatch
1: 00:17:3f:44:d8:92 ssid='Lutes 11' wpa_ie_len=24 rsn_ie_len=0
   selected
Trying to associate with 00:17:3f:44:d8:92 (SSID='Lutes 11' freq=2462 MHz)
Cancelling scan request
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Own WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_madwifi_set_drop_unencrypted: enabled=1
wpa_driver_madwifi_associate
Association request to the driver failed
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
Wireless event: cmd=0x8b1a len=21
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:17:3f:44:d8:92
Association event - clear replay counter
Associated to a new BSS: BSSID=00:17:3f:44:d8:92
No keys have been configured - skip key clearing
Associated with 00:17:3f:44:d8:92
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: txStart
WPA: drop TX EAPOL in non-IEEE 802.1X mode (type=1 len=0)
EAPOL: SUPP_BE entering state IDLE
EAP: EAP entering state INITIALIZE
EAP: EAP entering state IDLE
Setting authentication timeout: 10 sec 0 usec
RX EAPOL from 00:17:3f:44:d8:92
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 12 f0 3a d4 e8 06 66 7b 22 9e c3 b7 15 76 28 45 ad 82 79 7d e9 29 29 55 d8 da 75 44 50 59 05 7c e5 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 6b 28 e2 f2 2a e7 02 52 00 00
Setting authentication timeout: 10 sec 0 usec
EAPOL: Ignoring WPA EAPOL-Key frame in EAPOL state machines
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 12 f0 3a d4 e8 06 66 7b 22 9e c3 b7 15 76 28 45 ad 82 79 7d e9 29 29 55 d8 da 75 44 50 59 05 7c e5 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 6b 28 e2 f2 2a e7 02 52 00 00
WPA: RX message 1 of 4-Way Handshake from 00:17:3f:44:d8:92 (ver=1)
WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Renewed SNonce - hexdump(len=32): e4 14 bf af 71 96 32 7b 08 ff 3d b8 5d 52 f5 54 c6 b8 e3 ed 2a e0 11 c5 b2 72 e9 24 64 50 50 7f
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: EAPOL-Key MIC - hexdump(len=16): 0e 5e 84 f6 37 8c 9e 77 3d ac 50 84 06 2b 3b b6
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key 2/4 - hexdump(len=137): 00 17 3f 44 d8 92 00 18 4d 80 d4 af 88 8e 01 03 00 77 fe 01 09 00 20 00 00 00 00 00 00 00 12 e4 14 bf af 71 96 32 7b 08 ff 3d b8 5d 52 f5 54 c6 b8 e3 ed 2a e0 11 c5 b2 72 e9 24 64 50 50 7f 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 0e 5e 84 f6 37 8c 9e 77 3d ac 50 84 06 2b 3b b6 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
RX EAPOL from 00:17:3f:44:d8:92
RX EAPOL - hexdump(len=123): 01 03 00 77 fe 01 c9 00 20 00 00 00 00 00 00 00 13 f0 3a d4 e8 06 66 7b 22 9e c3 b7 15 76 28 45 ad 82 79 7d e9 29 29 55 d8 da 75 44 50 59 05 7c e5 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 a1 2b c9 1d a6 31 a2 4f fa 45 1c b5 8c ee 0e ec 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
EAPOL: Ignoring WPA EAPOL-Key frame in EAPOL state machines
IEEE 802.1X RX: version=1 type=3 length=119
  EAPOL-Key type=254
WPA: RX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 c9 00 20 00 00 00 00 00 00 00 13 f0 3a d4 e8 06 66 7b 22 9e c3 b7 15 76 28 45 ad 82 79 7d e9 29 29 55 d8 da 75 44 50 59 05 7c e5 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 a1 2b c9 1d a6 31 a2 4f fa 45 1c b5 8c ee 0e ec 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: RX message 3 of 4-Way Handshake from 00:17:3f:44:d8:92 (ver=1)
WPA: IE KeyData - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 4/4
WPA: TX EAPOL-Key 4/4 - hexdump(len=113): 00 17 3f 44 d8 92 00 18 4d 80 d4 af 88 8e 01 03 00 5f fe 01 09 00 20 00 00 00 00 00 00 00 13 e4 14 bf af 71 96 32 7b 08 ff 3d b8 5d 52 f5 54 c6 b8 e3 ed 2a e0 11 c5 b2 72 e9 24 64 50 50 7f 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 eb 10 8d 3d 20 3e fc 0f 31 ed b6 01 49 a4 ae f3 00 00
WPA: Installing PTK to the driver.
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_madwifi_set_key: alg=TKIP key_idx=0 set_tx=1 seq_len=6 key_len=32
RX EAPOL from 00:17:3f:44:d8:92
RX EAPOL - hexdump(len=131): 01 03 00 7f fe 03 91 00 20 00 00 00 00 00 00 00 14 35 27 ab 37 5f 76 d8 76 78 39 43 22 40 01 7f 2c d1 ae 7d b4 b0 6f 88 aa f0 cf 54 66 5c 48 b5 c6 b3 5c 68 ce 01 29 17 bf 2b 2a 44 2f 70 8b 24 39 01 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 e3 b1 a4 d0 d1 5a ba ec ff 0f 2b 95 56 ba 66 53 00 20 41 5b b2 48 70 38 6b 7c 8b 28 0a a8 75 2c 5f d1 df bc db ff 17 29 87 fa 41 0b fb 88 d6 67 f9 be
EAPOL: Ignoring WPA EAPOL-Key frame in EAPOL state machines
IEEE 802.1X RX: version=1 type=3 length=127
  EAPOL-Key type=254
WPA: RX EAPOL-Key - hexdump(len=131): 01 03 00 7f fe 03 91 00 20 00 00 00 00 00 00 00 14 35 27 ab 37 5f 76 d8 76 78 39 43 22 40 01 7f 2c d1 ae 7d b4 b0 6f 88 aa f0 cf 54 66 5c 48 b5 c6 b3 5c 68 ce 01 29 17 bf 2b 2a 44 2f 70 8b 24 39 01 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 e3 b1 a4 d0 d1 5a ba ec ff 0f 2b 95 56 ba 66 53 00 20 41 5b b2 48 70 38 6b 7c 8b 28 0a a8 75 2c 5f d1 df bc db ff 17 29 87 fa 41 0b fb 88 d6 67 f9 be
WPA: RX message 1 of Group Key Handshake from 00:17:3f:44:d8:92 (ver=1)
WPA: Group Key - hexdump(len=32): [REMOVED]
WPA: Installing GTK to the driver (keyidx=1 tx=0).
WPA: RSC - hexdump(len=6): 01 00 00 00 00 00
wpa_driver_madwifi_set_key: alg=TKIP key_idx=1 set_tx=0 seq_len=6 key_len=32
WPA: Sending EAPOL-Key 2/2
WPA: TX EAPOL-Key 2/2 - hexdump(len=113): 00 17 3f 44 d8 92 00 18 4d 80 d4 af 88 8e 01 03 00 5f fe 03 11 00 20 00 00 00 00 00 00 00 14 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 8b 8e 5b a6 bd ae 66 7e 03 bd c2 5a 95 3b 75 bc 00 00
WPA: Key negotiation completed with 00:17:3f:44:d8:92 [PTK=TKIP GTK=TKIP]
Cancelling authentication timeout
EAPOL: External notification - portValid=1
EAPOL: External notification - EAP success=1
EAPOL: SUPP_PAE entering state AUTHENTICATING
EAPOL: SUPP_BE entering state SUCCESS
EAPOL: SUPP_PAE entering state AUTHENTICATED
EAPOL: SUPP_BE entering state IDLE
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=29 idleWhile=59
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=28 idleWhile=58
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=27 idleWhile=57
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=26 idleWhile=56
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=25 idleWhile=55
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=24 idleWhile=54
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=23 idleWhile=53
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=22 idleWhile=52
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=21 idleWhile=51
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=20 idleWhile=50
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=19 idleWhile=49
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=18 idleWhile=48
Signal 2 received - terminating
wpa_driver_madwifi_deauthenticate
wpa_driver_madwifi_del_key: keyidx=0
wpa_driver_madwifi_del_key: keyidx=1
wpa_driver_madwifi_del_key: keyidx=2
wpa_driver_madwifi_del_key: keyidx=3
wpa_driver_madwifi_del_key: keyidx=0
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portValid=0
wpa_driver_madwifi_set_wpa: enabled=0
wpa_driver_madwifi_set_drop_unencrypted: enabled=0
wpa_driver_madwifi_set_countermeasures: enabled=0

```

---

### Post by cwfloyd on 2008-02-14
I do not know how much help this will be to you, but here it goes.
On my home Lan, I have 3 desktops (wired) and 2 laptops (wireless).
I am using DSL thru a DLINK DIR-615 wireless router that gave me immense fits!
Ubuntu 7.10 and xpsp2 are the OS (soon to be all Linux I hope!) in use.
The wired desktop running Ubuntu would get kicked offline as soon as I enabled the MAC address filter on the router.
I updated to the latest router firmware, entered the IP and MAC address of all the computers as per the instructions, and triple-checked all my settings.
I can only enable WPS2 encryption and network SSID invisibility.
Is there a way for you to check your router settings?
Is there a way for you to check your ip & mac address of your wireless card?
I wonder if there is not some security setting that is blocking you somehow.
With all the different hardware and software out there, I have about given up on windows & buggy windows software - even the manufacturer's service techs were of little use to me - had to find a way to fix from the help of the online community.
I wish you the best of luck and let us know how you make out.
Chris

---

### Post by huzzak on 2008-04-07
I ended up installing Puppy Linux.  It handles wireless much more easily than either Fluxbuntu or DSL.  It was very easy to set up.  If you are doing something that requires a lightweight distro, check out Puppy Linux.  There was a little bit of work getting some of the other programs installed that I needed, but google searches provided.

Good luck.

---

