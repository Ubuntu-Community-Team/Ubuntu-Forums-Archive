---
title: "Mac mini wifi wpa?"
date: 2006-08-30
forum: Apple PPC Users
---

### Post by AndreasJ on 2006-08-30
Hi!

I just installed xubuntu on my mac mini and I'm now trying to enable wifi. I can detect my wifi but I'm having trouble getting wpa to work. So far I have tried three different approaches and none of them have worked.

1. Installed network-manager and tried to configure xubuntus system->network. WPA is not visible only WEP.

2. Use wpa_supplicant with configuration file in /etc/wpa_supplicant.conf
```
network={
        ssid="my network"
        proto=WPA
        key_mgmt=WPA-PSK
        psk=secret
}
```
Command: sudo wpa_supplicant -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf
Error: ```
Trying to associate with 00:16:b6:b7:63:20 (SSID='my network' freq=2472 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Argument list too long
Association request to the driver failed
Authentication with 00:00:00:00:00:00 timed out.
```

3. Use /etc/network/interfaces
```
iface ath0 inet dhcp
        pre-up ifconfig ath0 up
        pre-up ifconfig ath0 down
        pre-up ifconfig ath0 up
        pre-up ifconfig ath0 down
        pre-up iwconfig ath0 essid "my network"
        pre-up iwconfig ath0 mode Managed
        pre-up iwpriv ath0 set AuthMode=WPAPSK
        pre-up iwpriv ath0 set EncrypType=TKIP
        pre-up iwpriv ath0 set WPAPSK="key in plaintext"
        pre-up ifconfig ath0 up
```
Command: sudo ifup ath0
Error:```
Invalid command : set
Failed to bring up ath0.
```

Conclusion: In the last example it seems that iwpriv doesn't support the set option. I also tried other options with iwpriv and it didn't support any of them. Since none of my effort so far has be successfull I'm guessing the driver doesn't support my card fully.

Misc information: Kernel modules 2.6.15-26-386
Command: lsmod | grep ath```

new_ath_pci            98340  0
new_ath_rate_sample    14080  1 new_ath_pci
new_wlan              204892  5 new_wlan_wep,new_wlan_scan_sta,new_ath_pci,new_ath_rate_sample
new_ath_hal           191312  3 new_ath_pci,new_ath_rate_sample

```

---

### Post by APU on 2006-08-30
Just a short question. Is it a Intel Mac mini? Because otherwise you would use the wrong driver.

If your Mac mini is a PPC you have to use -Dwext instead of Dmadwifi and -ieth1 instead of -iath0

---

### Post by AndreasJ on 2006-08-30
Yes, sorry I forgot to write it's an intel. You can get a hunch though if you look at my running kernel.
```
Kernel modules 2.6.15-26-**386**
```

I think it's the driver but I'm not sure. I'm going to look more closely at the madwifi project tomorrow.

---

### Post by AndreasJ on 2006-08-31
I've got my wifi up and running with wpa encryption. I did the following steps.

1. Downloaded latest version of madwifi(r1705).
2. Installed all the tools one need to compile including kernel headers, g++, gcc and make.
3. Compiled and installed madwifi into the kernel modules.
4. Removed all previously loaded modules related to madwifi.(lsmod | grep new_)
5. Changed directory to /lib/modules/*current-version*/net, then typed: modprobe ath_pci.
6. Now all modules needed for your madwifi card should be loaded. The last step is to enable WPA encryption using: sudo wpa_supplicant -iath0 -D**wext** -c/etc/wpa_supplicant.conf.
Note the change from using the madwifi to the wext driver in wpa_supplicant. According to Jouni Malinen the developer of wpa_supplicant should the madwifi driver only be used with old madwifi versions. Newer versions will use the more generic wext driver.

Thanks
AndreasJ

---

