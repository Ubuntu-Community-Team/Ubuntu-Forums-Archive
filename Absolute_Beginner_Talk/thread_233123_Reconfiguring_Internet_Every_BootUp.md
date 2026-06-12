---
title: "Reconfiguring Internet Every BootUp"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by SonicChao on 2006-08-09
Every time I boot up Ubuntu, I have to reconfigure my DirecWay box, by going to:

```
System --> Administration --> Networking
```

going to the DNS tab and typing in the following numbers (in DNS servers)

192.168.0.1
67.142.132.12

On the next reboot, it forgot everything. And DNS is blank again. ](*,)

---

### Post by SonicChao on 2006-08-10
*bump* I hope someone knows something...:-(

---

### Post by TFX360 on 2006-08-10
Edit /etc/network/interfaces

```
sudo gedit /etc/network/interfaces
```

Add under your active connection:

dns-nameservers 67.142.132.12

Let me know if it works!

---

### Post by SonicChao on 2006-08-10
I can't thank you enough for that.

(for future reference though, the correct command is

```

gksu gedit /etc/network/interfaces

```)

Thanks for helping! :D

---

### Post by TFX360 on 2006-08-10
Of course it should be. I only use vi and nano. People here mostly use gedit.


Glad to help,


Kind regards,


TFX

---

### Post by drtvasudevan on 2006-08-11
> **TFX360 said:**
> Edit /etc/network/interfaces

```
sudo gedit /etc/network/interfaces
```

Add under your active connection:

dns-nameservers 67.142.132.12

Let me know if it works!

i had similar problem.
editing to dns-nameservers 192.168.1.1
now puts me on the net straight off.
but still the domain name remains blank.

this is how it looks in my file:
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 192.168.1.1

can i have a look at a normally working entry?

---

### Post by SonicChao on 2006-08-11
Er...I can show you what mine looks like:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1
dns-nameservers 67.142.132.12

iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

But I can't help other then that. :(

---

### Post by TFX360 on 2006-08-11
Back to basic...

Your router should be the one that automatiacally route dns. With your router this doesn't seem to work. It could also be Ubuntu because I had the problem but only at one or three boot ups.

Try not your router IP but the official DNS server from you ISP (Internet Sercive Provider).


Kind regards,


TFX.

---

### Post by drtvasudevan on 2006-08-11
> **TFX360 said:**
> Back to basic...

Your router should be the one that automatiacally route dns. With your router this doesn't seem to work. It could also be Ubuntu because I had the problem but only at one or three boot ups.

Try not your router IP but the official DNS server from you ISP (Internet Sercive Provider).
TFX.

my router is one that automatically redirects and that is 192.168.1.1
the problem was with updates and so i gave up DHCP and chose static ip.
and the settings is what my ISP gave which works in win98.
all my resettings of the network was probably not being writen to the file and so every time i had to reset.
now i can connect to net.
but upgrades are still a problem.

thanks
previously

---

