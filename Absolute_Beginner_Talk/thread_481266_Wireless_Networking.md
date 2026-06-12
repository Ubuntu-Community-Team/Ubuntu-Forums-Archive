---
title: "Wireless Networking"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by mikeypc2006 on 2007-06-22
How can I get my D-Link DWL-G650+ PCMCIA network card to work on my laptop?  When I put it in, Ubuntu appears to recognise it, but I can't see any obvious ways as to how to connect to a wireless network.

What am I doing wrong?

I've tried both unencrypted and encrypted networks, but I can't connect to either.

---

### Post by matthewboh on 2007-06-22
Can you go into terminal mode (Applications | Accessories |Terminal) and type in ```
lspci | grep Network
``` and ```
cat /etc/network/interfaces
``` post the output and let us know if your trying to connect with NetworkManager?

---

### Post by mikeypc2006 on 2007-06-22
> **matthewboh said:**
> Can you go into terminal mode (Applications | Accessories |Terminal) and type in ```
lspci | grep Network
``` and ```
cat /etc/network/interfaces
``` post the output and let us know if your trying to connect with NetworkManager?
```
lspci | grep Network
```
02:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface

```
cat /etc/network/interfaces
``` 

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

Yes, I am trying to connect with network manager

---

### Post by matthewboh on 2007-06-22
Go into your interfaces file by getting into a terminal session and typing```
sudo gedit /etc/network/interfaces
``` then making it look like this by commenting out everything except the first two lines```
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

``` Save the file, which will put you back into terminal mode and restart NetworkManager by typing ```
kill `pidof NetworkManager`
/etc/init.d/networking restart 
/usr/sbin/NetworkManager
``` and then give it a go

---

### Post by diatribe on 2007-06-22
you could try downloading wicd, it will scan for and automatically connect to your chosen wireless network

---

### Post by shifty_powers on 2007-06-22
Right seriously, don't bother faffing around with the ubuntu drivers for that card, (which iirc uses a rt61 chipset). Got the dwl-g510 pci card, and the ubuntu drivers caused me untold grief.

You will have to blacklist those drivers so that they don't get loaded up on start-up. Also, use ndis wrapper, which you can either get through synaptic or if you are feeling adventurous you can even compile it from source, (and it ain't that hard actually). Ndiswrapper will let you use the windows drivers for that card, hopefully.

Trust me, ndis wrapper and the windows drivers will save you a lot of grief, take it from my own experiences ;)

---

### Post by mikeypc2006 on 2007-06-28
> **matthewboh said:**
> Go into your interfaces file by getting into a terminal session and typing```
sudo gedit /etc/network/interfaces
``` then making it look like this by commenting out everything except the first two lines```
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

``` Save the file, which will put you back into terminal mode and restart NetworkManager by typing ```
kill `pidof NetworkManager`
/etc/init.d/networking restart 
/usr/sbin/NetworkManager
``` and then give it a go

I've done everything except when I come to the last bit I get 'arguments must be process or job IDs' for each line.  What am I doing wrong?

---

### Post by shifty_powers on 2007-06-29
You want to replace 'pidof Network Manager' with the *process id* of network manager. You can find this out by using a program such as htop, which you can find via synaptic or

```
 sudo apt-get install htop
```.

---

