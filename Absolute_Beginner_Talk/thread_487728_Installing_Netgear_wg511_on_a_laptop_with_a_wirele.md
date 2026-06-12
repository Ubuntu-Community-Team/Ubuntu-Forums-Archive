---
title: "Installing Netgear wg511 on a laptop with a wireless card allready present."
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by GregoryMA on 2007-06-29
I bought a Netgear wg511 because I got tired of fighting with the bcm4318 wireless card that came installed on my laptop.  How do I go about and get the netgear wg511 working?  My plan was to plug it in and re-install feisty, but will the bcm4318 card mess with that?
Greg

---

### Post by psycho78 on 2007-06-29
Hi, 

I have an WG511**T** (don't know if it has the same chipset, mine has the Atheros): 

lspci -vv
---------------------------------------------------------------------------------------------------
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
        Subsystem: Netgear Unknown device 4b00
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 168 (2500ns min, 7000ns max), Cache Line Size: 128 bytes
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at 5c000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [44] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=2 PME-
---------------------------------------------------------------------------------------------------

and I simply installed linux-restricted-modules and changed /etc/network/interfaces to:

#The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0
        map ath0
# The primary network interface
iface eth0 inet dhcp

**# static wireless LAN configuration**
iface ath0 inet static
address 192.168.101.101
netmask 255.255.255.0
broadcast 192.168.101.255
gateway 192.168.101.1
pre-up /sbin/wpa_supplicant -B -i ath0 -c /etc/wpa_supplicant.conf -D madwifi -w -dd
pre-up /sbin/iwconfig ath0 essid **YourSSID**
auto ath0



**and changed /etc/wpa_supplicant.conf to:**

ctrl_interface=/var/run/wpa_supplicant
eapol_version=1
network={
        ssid="**YourSSID**"
        scan_ssid=1
        priority=5
        proto=WPA
        key_mgmt=WPA-PSK
        pairwise=CCMP TKIP
        group=CCMP TKIP WEP104 WEP40
        ssid="Freezie"
        psk="**YourSharedKey**"
        }


If your other card is already named ath0, simply change the newer card to ath1 everywhere, then you should not mess up anything... in worst case you can roll back the changes you made and should have your old working config... 
It's a good idea to backup /etc/network/interfaces and /etc/wpa_supplicant.conf before....

Hope this helps you a little....

Regards,
Psycho...

---

### Post by GregoryMA on 2007-06-30
Actually that is the card I have I made a mistake and left out the T.  Thanks, I will try this as soon as possible.

---

### Post by GregoryMA on 2007-06-30
It worked! I am writing to you from Ubuntu.  I can't believe how easy this was after putting up with the bcm card for so long.
Thanks alot, Greg.

---

