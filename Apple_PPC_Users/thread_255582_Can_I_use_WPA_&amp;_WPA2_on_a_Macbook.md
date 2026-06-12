---
title: "Can I use WPA &amp; WPA2 on a Macbook?"
date: 2006-09-11
forum: Apple PPC Users
---

### Post by Tofu on 2006-09-11
I've installed Ubuntu Dapper on a Macbook, and it's looking good, well, except for Wi-Fi. It doesn't seem to work with WPA and WPA2 security.

I read [on another website]("http://desrt.mcmaster.ca/macbook.xhtml") something about recompiling 'wpasupplicant', but I don't know what that is, and I've never compiled software before.

Has anyone had success with secure wireless? Are there any easy-to-understand instructions on getting WPA / WPA2 to work on a Macbook.

Thanks.

---

### Post by stmiller on 2006-09-11
Install gnome-network-manager.

---

### Post by Tofu on 2006-09-14
> **stmiller said:**
> Install gnome-network-manager.

I opened the Synaptic Package Manager. I found the "Network Manager - Gnome" listed, so I installed it.

When I open the System -> Network control panel, I can see my wireless network (SSID) on the list.

Still can't seem to connect to it. The network is using WPA2 encryption.

---

### Post by Tofu on 2006-09-16
(Bump)

Has anyone succeeded in using WPA Wi-Fi with a Macbook?

How did you achieve it?

Did you use gnome-network-manager or something else?

---

### Post by jfmbp on 2006-09-16
WPA-PSK work for me on Macbook Pro: 2.6.15-26-686 #1 SMP PREEMPT Thu Aug 3 03:13:28 UTC 2006 i686 GNU/Linux

with network-manager-gnome 0.6.2-0ubuntu7

router : USR 8054

To achieve, I had to remove all wifi related entries in /etc/network/interfaces

PS: I do not use the last kernel update (2.6.15-26.47) but the  2.6.15-26.46 because it breaks a lot of things for me (sound, speedstep_centrino, ...).
Not sure it doesn't broke some wifi stuff too ...

---

### Post by stmiller on 2006-09-16
Gnome network manager should make a little applet at the top right of the screen.

You just select the access point from the applet, and connect. 

> When I open the System -> Network control panel, I can see my wireless network (SSID) on the list.

DON'T use this. The gnome-network-manager handles everything. 

Search the forums please. This is all over the ubuntu forums.

---

### Post by Tofu on 2006-09-18
> **jfmbp said:**
> To achieve, I had to remove all wifi related entries in /etc/network/interfaces
I just had a look at this document called **/etc/network/interfaces**.
Here is its contents:

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
wireless-essid MyNetwork
wireless-key s:password

auto wlan0
iface wlan0 inet dhcp
```

I'm not sure what I can change in this to make WPA work. I'm no Linux expert     :(

> **stmiller said:**
> Gnome network manager should make a little applet at the top right of the screen.

You just select the access point from the applet, and connect.
I've now got a little icon in the top right of screen. It looks like 2 monitors. I assume this is the Gnome Network Manager. When I click on it it just says "wired network".


> **stmiller said:**
> Search the forums please. This is all over the ubuntu forums.
Apologies. I searched for some time using the terms "Macbook" and "WPA" and didn't find anything useful.

---

### Post by stmiller on 2006-09-18
Lots of threads:

[http://ubuntuforums.org/search.php?searchid=8258890](http://ubuntuforums.org/search.php?searchid=8258890)

In fact, there is a sticky thread at the top.

"HOWTO: NetworkManager with WPA 1&2 Support"

Though it is a little dated. No need to compile wpa_supplicant, as it's in the apt-get repos.

--------------

The network-manager makes it's own config files on the fly. So for it to work, you have to have nothing in any config files. 

Remove all lines from /etc/network/interfaces except this one:

auto lo
iface lo inet loopback



And make sure you install wpa-supplicant packages for WPA. 


Then it *should* just work.

---

### Post by geodude on 2006-09-21
I've installed Ubuntu on my 17" Powerbook (G4, Airport Extreme). I've installed the Gnome Network Manager. I select "Connect to Other Wireless Network..." and enter my settings. I have a WPA Personal setup. The little arrows spin for awhile and then I just get the red exclamation point showing failure.

I found the wpa-supplicant package in the Synaptic manager and it was already installed. I even selected it for reinstall.

dmesg shows "bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.

lsmod | grep bcm43 shows:
bcm43xx    136524 0
ieee80211softmac    33658  1 bcm43xx
ieee80211    39784  1 bcm43xx,ieee80211softmac

I'm stuck now. What do I do next?

Thanks for any help.

BTW, the link given ([http://ubuntuforums.org/search.php?searchid=8258890](http://ubuntuforums.org/search.php?searchid=8258890)) leads to a page that says "Sorry - no matches. Please try some different terms."

---

