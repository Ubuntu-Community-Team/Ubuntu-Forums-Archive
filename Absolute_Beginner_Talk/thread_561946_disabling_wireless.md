---
title: "disabling wireless"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by Protagonistics on 2007-09-28
When I turn on my system, my networking automatically searches for a wireless network by default. I want to use my wired connection as default. How do I set it so that wireless is disabled by default and not enabled? There SHOULD be a GUI way to do this, but I don't know/remember what it is. thanks!

---

### Post by justleen on 2007-09-28
dont know the gui way :)
/etc/networking/

youind the config files for the eth there, open the relevant one, and change it so it says "on boot= no"
(or auto=no)

---

### Post by Protagonistics on 2007-09-28
I'm not sure what "relevant one" means. In etc there are two networking folders: Network or Network Manager. 
Under etc/network/ I have the following folders:
etc/network/if-down.d
etc/network/if-post-down.d
etc/network/if-pre-up.d
etc/network/if-up.d
as well as a file called interfaces which has the following inside:

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

auto wlan0
iface wlan0 inet dhcp


Not sure what is being referred to inside etc/networking-- but thank you for helping, I hope you can specify what to do?

---

### Post by justleen on 2007-09-28
do you kn ow which one your wireless device is? on my system its eth1

you can just remove the line "auto eth1" in the networking file, and it wont start it at boot.

---

### Post by Protagonistics on 2007-09-28
I commented out eth1 as well as ath0 and wlan0 but nothing seems to be changing.

---

