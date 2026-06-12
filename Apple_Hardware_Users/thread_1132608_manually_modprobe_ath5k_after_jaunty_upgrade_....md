---
title: "manually modprobe ath5k after jaunty upgrade ..."
date: 2009-04-22
forum: Apple Hardware Users
---

### Post by anando on 2009-04-22
Hi guys

I had a working Intrepid on my Macbook pro (1,1) - when the curiosity got the better of me. I upgraded to jaunty RC and my laptop sort of works. An annoying thing is that, in order to make my wireless card work, after every boot I need to 'sudo modprobe ath5k'. And then the wireless card works. I wonder if this has to do with legacy blacklists. For example, 

> anando-laptop >> pwd
/etc/modprobe.d
anando-laptop >> 
anando-laptop >> grep ath5k *
blacklist-ath_pci.conf:# which ath5k cannot recover. To prevent this condition, stop
blacklist-ath_pci.conf:blacklist ath5k

Should I remove the blacklist ath5k line ? 

Please advise.

- Anand.

---

### Post by cyberdork33 on 2009-04-22
Here is my blacklist-ath_pci.conf

```
# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
blacklist ath_pci
```

Did you choose the driver in System > Administration > Hardware Drivers

---

### Post by anando on 2009-04-23
Hi cyberdork

Yes indeed I was trying out the madwifi driver (ath_pci) in System->Administration->Hardware which may have blacklisted my ath5k module.

So the update is, 
* ath_pci wireless driver (the madwifi driver) did not work well for me
* I edited the file /etc/modprobe.d/blacklist-ath_pci.conf and hashed out the line which said 'blacklist ath5k' and put instead 'blacklist ath_pci'
* Now my ath5k works at every boot.

The curious thing about ath5k is that it works well for WEP and WPA2 at home but when I try it on WPA2 Enterprise (at work), it loses the connection every 2 minutes or so and porompts me for the password. I wonder if others have noted anything similar.

Regs,
Anand.



> **cyberdork33 said:**
> Here is my blacklist-ath_pci.conf

```
# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
blacklist ath_pci
```Did you choose the driver in System > Administration > Hardware Drivers

---

### Post by mbasic on 2009-04-26
I am new in linux world and need help with wireless card. I have recently installed this new jauntu version of Ubutnu and am trying to make w card working. I have Netgears WPN511 card and linux recognizes chipset as Atheros AR5001+. For weeks I have been trying to make this card working in previuos ubuntu release, unfortunately with no luck. I have tried everything I could find on Internet but nothing helped. The last thing that I tried I downloaded madwifi drivers and then finally led diode was blinking on my card. Running iwconfig ath) gave me a list of all networks in neighborhood so I think that I was on right path. But network manager always said "wireless is disabled".
So I installed ubuntu for 1 millionth time and now waiting someone to help me.
Currently:
 
lshw gives:
*-network
     description: Wireless interface
     product: Atheros AR5001X+
     ....
 
- Network Tools names this card as wlan0
 
Please help me configure this card.
Thanks

---

### Post by anando on 2009-04-27
[http://ubuntuforums.org/showthread.php?t=1024108](http://ubuntuforums.org/showthread.php?t=1024108)

> **mbasic said:**
> I am new in linux world and need help with wireless card. I have recently installed this new jauntu version of Ubutnu and am trying to make w card working. I have Netgears WPN511 card and linux recognizes chipset as Atheros AR5001+. For weeks I have been trying to make this card working in previuos ubuntu release, unfortunately with no luck. I have tried everything I could find on Internet but nothing helped. The last thing that I tried I downloaded madwifi drivers and then finally led diode was blinking on my card. Running iwconfig ath) gave me a list of all networks in neighborhood so I think that I was on right path. But network manager always said "wireless is disabled".
So I installed ubuntu for 1 millionth time and now waiting someone to help me.
Currently:
 
lshw gives:
*-network
     description: Wireless interface
     product: Atheros AR5001X+
     ....
 
- Network Tools names this card as wlan0
 
Please help me configure this card.
Thanks

---

### Post by Ryuhayabusa on 2009-05-14
> **anando said:**
> Hi cyberdork

The curious thing about ath5k is that it works well for WEP and WPA2 at home but when I try it on WPA2 Enterprise (at work), it loses the connection every 2 minutes or so and porompts me for the password. I wonder if others have noted anything similar.


I can WPA at home but have been unable to at university WPA2 PEAP TKIP MSCHAPV2.

I have tried ath5k in jaunty 2.6.28. 
(I can't even get it to work with ath_hal, but that may be another problem)

---

