---
title: "D-Link DWL-G520 not working.  please help!"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by insub2 on 2006-08-23
i got a new wireless card today and it wont work.  this is particularly frustrating because the DWL-G520 is supposed to work out of the box with the madwifi driver.

I put it in my box and turned it on.  The device manager recognizes it.  but for ifconfig i just get eth0 and lo  and for iwconfig i get lo, eth0, and sit0. both the device manager and lspci tell me that it is the atheros.

does anybody have any thoughts or advice?

let me know if you need anymore information.

___
EDIT:
SOLUTION:
```
modprobe ath_pci
```
restart computer.
...
i feel dumb.:redface:

---

### Post by SteveHoffmanUK on 2006-08-23
I am a newbie, so you'll have to excuse my non-technical reply and approach, and I may be way off base, but...

I have a D-Link DWL-520+ (which I assume is the same as yours) which, to the best of my recollection, worked out of the box. I never heard of madwifi drivers or ifconfig or iwconfig and worked only in GUI mode, not at the terminal. Here is what I did, for what it's worth:

Installed the card. Duhhh

In Ubuntu, went to System | Administration | Networking
In the Network Settings panel found Wireless Connection / The interface wlan0 is not configured
I clicked on Properties and got the panel Interface Properties
In that panel I:
1. Checked 'Enable this connection'
2. Entered the name (ESSID) of my wireless network
3. Chose hexadecimal as Key type
4. Entered the 26-character WEP key
5. Under Connection Settings, chose DHCP as the Configuration (rest of the entries became dimmed)
6. Pressed OK

Back in the Network Settings panel I also activated Ethernet Connection (clicked on properties) and in the Interface Properties panel:
1. Checked 'Enable this connection'
2. Chose DHCP as the Configuration (rest became dimmed)
3. Pressed OK

When both the Wireless Connection and the Ethernet Connection showed as activated (wlan0 and eth0 respectively) Pressed OK on the Network Settings panel.

I was then online to my wireless network (Netgear 108 Mbps wireless ADSLFirewall Router DG834GT/GTB). It has worked faultlessly ever since.

Don't know if this approach will help you; I only submit it as my experience; maybe there are system differences that make it irrlevant for you, but you might try this approach.

---

### Post by Turgon on 2006-08-23
You could look and see if the linux kernel restrictet package is installed (I belive madwifi is in there). If it aint installed, then you have found the problem:)

---

### Post by insub2 on 2006-08-23
> **Turgon said:**
> You could look and see if the linux kernel restrictet package is installed (I belive madwifi is in there). If it aint installed, then you have found the problem:)

thanks for the reply but i don't know how to do that off hand.  i'll do some poking around and try and figure it out.

---

