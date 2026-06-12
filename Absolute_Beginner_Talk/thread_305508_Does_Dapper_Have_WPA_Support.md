---
title: "Does Dapper Have WPA Support?"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by metBANS on 2006-11-23
I've just installed Edgy (I'm new to Ubuntu, and Linux in general), and all seems to be working well, except I can't configure it to work with either my card or my router (which has WPA encryption).  I'm assuming its the WPA, because even when I'm wired into my network, I don't even have an option of using a wired connection in the Connection Manager.

So my question is, would Dapper work better with my current situation?

:::EDIT::: I'm using a Dell Latitude C600 Laptop
Linksys Wireless Router
D-Link AirPlus DWL-G650 Wireless Card

---

### Post by AndyCooll on 2006-11-23
Both Dapper and Edgy have WPA support.

I usually just make my wireless card the default, add the following to my /etc/network/interfaces, reboot and there it is:

```
#iface ra0 inet static
address YOUR_IP_ADDRESS
netmask 255.255.255.0
network 192.168.2.0
broadcast 192.168.2.255
gateway 192.168.2.1
pre-up iwconfig ra0 essid YOUR_NETWORK
pre-up iwconfig ra0 mode managed
pre-up iwpriv ra0 set Channel=11
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwpriv ra0 set WPAPSK="YOUR_PASSWORD"
pre-up iwpriv ra0 set TxRate=0
auto ra0
```

Having said that your problem isn't likely to be WPA if you cannot get a connection even when using a wired connection (it should show as eth0 or something similar)

:cool:

---

### Post by metBANS on 2006-11-23
So what do you think my course of action should be so I can connect?

---

### Post by NiklasV on 2006-11-23
Try installing network-manager, it should automatically switch to wireless when the wired isn't connected, and ask you for WPA, WEP, etc.

Install network manager:
sudo apt-get install network-manager-gnome

You may have to remove references to the wireless from /etc/network/interfaces. If it doesn't work properly, you could try that.

If it still doesn't work, post your iwconfig as well as lspci output.

---

### Post by metBANS on 2006-11-23
Excuse my ignorance, and I apologize if this isn't what you wanted.  I am using a different computer to post as well.

Thanks

lspci?
```
lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Sr33l3rsRG00d"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

lspci output?
```
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:03.0 CardBus bridge: Texas Instruments PCI1420
00:03.1 CardBus bridge: Texas Instruments PCI1420
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02)
06:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
```

---

### Post by NiklasV on 2006-11-23
Try configuring your router to not use encryption for the wireless in order to see if it's a problem with WPA or if your card isn't working properly.

---

### Post by metBANS on 2006-11-23
Well, disabled the WPA encryption, and I'm still not getting a connection.  It definitely is not my card, as I could previously connected while I used Windows.

Thank you.

---

### Post by wieman01 on 2006-11-23
If you still need WPA there is a comprehensive Howto for you:

[http://www.ubuntuforums.org/showthread.php?t=202834]("http://www.ubuntuforums.org/showthread.php?t=202834")

If your card still does not connect even though you have turned off wireless security, then it's definitely your card (= Linux driver).

---

### Post by NiklasV on 2006-11-23
I found a thread with a similar problem using the same chipset.
[http://www.ubuntuforums.org/showthread.php?t=304295&page=2&highlight=AR5212+802.11abg](http://www.ubuntuforums.org/showthread.php?t=304295&page=2&highlight=AR5212+802.11abg)

The problem appears to have been resolved by using WEP (though I'm not sure why it would work with WEP, but not unencrpyted.)

So try setting your router to 128 bit WEP and add the following to your /etc/network/interfaces (replace any existing entries concerning ath0)
```

iface ath0 inet dhcp
wireless-essid My_ESSID
wireless-key xxxxxxxxxxxxxxxxxxxxxxx
auto ath0

```
where xxx.... is your WEP code in hex

And if you still can't get it to work, then you could try using the windows drivers with ndiswrapper instead.

Your chipset is supposed to be supported out of the box though.

And if after that it still doesn't work, you could try using Dapper instead.
According to [http://ubuntuforums.org/showthread.php?t=281660](http://ubuntuforums.org/showthread.php?t=281660) your chipset is one of those which appears to have regressed in edgy, though I'm not sure if that's been fixed.

---

