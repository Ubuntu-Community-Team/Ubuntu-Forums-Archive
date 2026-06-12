---
title: "Wifi on Macbook Air 1,1 - BCM4321 (14e4:4328)"
date: 2015-04-05
forum: Apple Hardware Users
---

### Post by Arjun_Govindjee on 2015-04-05
The Broadcom chips have struck again. I've tried the b43 and wl drivers with no luck whatsoever: according to my computer...it's in an alternate reality where Faraday cages are built into WiFi antennae... (or more likely, iwlist wlan0 scan yields "no scan results").

Here is a [summary of my experiences with the b43 drivers]("https://askubuntu.com/questions/605464/cannot-scan-for-wifi-networks-with-bcm4321/").
And [the wl drivers]("http://paste.ubuntu.com/10745751/").

Looking at the wl driver dmesg log, it would appear that there is some kind of shenanigans going on with the chipset name. The wl driver reports trying to use a BCM4328, while as far as I am aware I have a BCM4321 (according to lspci), however the device id is 14e4:4328, so who knows what wl is trying to tell us.p

By the way, huge thanks to chili555 for his advice to other BCM4321 sufferers which has helped me understand what I'm doing in the first place, and thanks to Varunendra for his WiFi debugging script, so I don't have to spend hours copying and pasting various configuration details to code tags.

If anyone has WiFi working on this specific device under Ubuntu 14.10, please do share how :)

---

### Post by chili555 on 2015-04-05
Did you do what I suggested in the other thread? What was the outcome, ideally a bit more specific than "...an alternate reality where Faraday cages are built into WiFi antennae"?

Please post:```
lsmod | grep -e wl -e b43
rfkill list all
iwconfig
```

---

### Post by Arjun_Govindjee on 2015-04-05
Yeah I did, results are linked in the OP, but here they are again: [http://paste.ubuntu.com/10745751/](http://paste.ubuntu.com/10745751/)
(Edit: It is working with these settings)

lsmod
```
wl                   6367694  0
cfg80211              510218  1 wl
```

rfkill list all
```
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

iwconfig
```
eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=200 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
lo        no wireless extensions.

```

---

### Post by Arjun_Govindjee on 2015-04-05
[s]WAIT IT STARTED WORKING.[/s]
I NOTICED BECAUSE THE TX-POWER CHANGED.
WHAT EVEN HAPPENED.
MY COMPUTER WAS SUSPENDED TO RAM (lid closed) AND NOW IT WORKS?

Edit: Also, I updated the kernel (apt-get dist-upgrade), but that didn't help until now...
So for anyone with 3.16.0-23-generic x86_64 upgrade to 3.16.0-33-generic. It might help??

Edit 2: **The wifi only works if I close the lid and reopen (after a reboot that is). Please explain oh wise internets.**

---

### Post by chili555 on 2015-04-06
> **Arjun_Govindjee said:**
> The wifi only works if I close the lid and reopen (after a reboot that is). Please explain oh wise internets.We wish we knew! Let's see if we can narrow down some possible reasons. Please reboot. If the wireless is not working, please run:```
echo "ON BOOT"  >  wifi.txt
lsmod  >>  wifi.txt
echo "----------"  >>  wifi.txt
```Close the lid and reopen. Assuming the wireless is now working, run:```
echo "AFTER SUSPEND"  >>  wifi.txt
lsmod  >>  wifi.txt
```Find the file wifi.txt in your user directory. Post it here and give us the link: [http://paste.ubuntu.com](http://paste.ubuntu.com)

Thanks.

---

### Post by Arjun_Govindjee on 2015-04-08
```
arjun@perseus:~$ lsmod > [file1]("http://paste.ubuntu.com/10769712/")
arjun@perseus:~$ lsmod > file2 #no need to link, obviously the same
arjun@perseus:~$ diff file1 file2
arjun@perseus:~$ 

```

i.e. no results (sorry for not following the instructions exactly, I wasn't in the mood for all that typing/copy+pasting :P)

edit: lspci also shows the same info for the wireless card

---

### Post by chili555 on 2015-04-08
In Network Manager running in both cases?```
sudo service network-manager status
```Any difference here?```
iwconfig
```or here?```
rfkill list all
```

---

### Post by Arjun_Govindjee on 2015-04-18
Sorry its been awhile, now that I have a process to make the wifi work, its merely inconvenient, not causing me murderous thoughts...but still...it should work...

Before suspend:
```
network-manager start/running, process 814

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=200 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

After:
```
network-manager start/running, process 814

wlan0     IEEE 802.11abg  ESSID:"Eichstrasse"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: C8:60:00:94:0B:DE   
          Bit Rate:130 Mb/s   Tx-Power=200 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

Only difference I notice is that the numbers of the devices in rfkill are switched around...not exactly earth-shattering, but maybe a sign of a deeper problem?

PS: If I wake the computer via the power button, instead of the magnetic switch in the lid, the trackpad ceases to function. I'm guessing that these are unrelated problems because the trackpad is connected internally via USB, while the wireless card is PCIe.

---

### Post by chili555 on 2015-04-25
Sorry for the delay in my reply. Sometimes hobby #1 and #2 and #3 conflict.

We've verified that the driver is present and Network Manager is running in both cases. Next, I wonder what's happening or not on boot. Please reboot so that the wireless isn't working and paste:```
dmesg | grep -e wl -e wlan
```Also, does the wireless come to life if you unload and reload the driver?```
sudo modprobe -r wl && sudo modprobe wl
```Or restart NM?```
sudo service network-manager restart
```

---

