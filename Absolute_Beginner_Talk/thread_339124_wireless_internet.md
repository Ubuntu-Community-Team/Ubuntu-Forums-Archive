---
title: "wireless internet"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by linex on 2007-01-15
hi
after  ubuntu boots up, how do i scan for wireless networks that are available? i have a wireless router setup with wep protection, how do connect to this?

---

### Post by oyvindaa on 2007-01-15
With wifi-radar.

In the terminal:

```
sudo apt-get install wifi-radar
```

You can also search for it and install it from Synaptic Package Manager.

Actually, wifi-radar doesn't contain a scan-option, but it finds in-range wireless networks by itself. Try it ;)

---

### Post by teaker1s on 2007-01-15
welcome to the forums, first thing you would need to work out is if your wireless chipset is supported

 in terminal type these commands and paste output so we can see whats happening

[COLOR="Red"]lsusb[/COLOR]

[COLOR="Red"]lspci[/COLOR]



[COLOR="Red"]iwconfig[/COLOR]

---

### Post by linex on 2007-01-15
thanks guys
i'm so glad i'm not being flammed for being a noob:)

---

### Post by sailor2001 on 2007-01-15
kwifi manager (in synaptics) allows scan for networks.......I keep mine on the panel

---

### Post by floke on 2007-01-15
You can also try 'sudo apt-get install network-manager-gnome'

---

### Post by teaker1s on 2007-01-15
make sure that clicking on panel
system
administration
networking

that devices are unconfigured and ethernet cable is unplugged to hand over control of networking to your chosen network manager

---

