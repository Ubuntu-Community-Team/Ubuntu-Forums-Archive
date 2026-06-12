---
title: "Network Manager and Wired Connection"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by kiplingw on 2006-09-14
Everytime I boot, Network Manager asks for my keyring password which is annoying. It needs to do this in order to access my WPA passphrase for wireless. Is there any way to have it done automatically?

If I have a wired connection available, shouldn't Network Manager automatically detect this and grab an IP? Everytime I boot, I have to manually dhclient eth0 to get an IP with it.

Kip

---

### Post by linuxusr50 on 2006-09-14
Check /etc/network/interfaces file.  Make sure you have an entry that looks something like this.

> auto eth0

iface eth0 inet dhcp

If not, do the following:
```
sudo gedit /etc/network/interfaces
```
and add those lines.

---

### Post by kiplingw on 2006-09-14
Thank you. It worked.

My understanding was that /etc/networking/interfaces was supposed to be all commented out to ensure that NetworkManager was able to exercise its soverignty over all adaptors?

Kip

---

### Post by fragos on 2006-09-15
I just brought Broadcom WiFi up on an Acer Laptop.  I had real problems with gnome-network-manager and replaced it with wifi-radar which worked better for me.  If you have nm-gnome in the startup tab of sessions, disable it as well.

---

### Post by kiplingw on 2006-09-15
Why would one wish to disable nm-gnome?

Kip

---

