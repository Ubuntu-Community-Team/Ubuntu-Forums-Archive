---
title: "Wifi at startup problem"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by gloscherrybomb on 2007-01-30
Right guys,

I have an issue with my wifi connection that to get it to connect, I have to do sudo iwconfig wlan0 essid xxxxxx. I have to do this everytime I restart the computer, or it doesn't connect to the network. I have set up a script that runs at boot to do this.

Part 2 of the problem is that my wifi card is only on if the orange light on my acer laptop is on, so i have to press that during boot, so that the startup script will run and everything will connect fine.

Is there a way to either:

A: have my wireless light come on automatically at boot like it did on Windows, so the script I wrote will always work and it will connect to the network every time at srtartup.

B: not have to use the script/terminal command at all, so all I need to do to connect to the network is press the red light

C: both

Any help much appreciated!

---

### Post by gloscherrybomb on 2007-01-31
sorry but gotta *BUMP*

---

### Post by jkeyes0 on 2007-01-31
What does your /etc/network/interfaces file look like?

---

### Post by gloscherrybomb on 2007-01-31
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

auto wlan0
iface wlan0 inet dhcp


```

My network is being ran by networkmanager.

---

### Post by jkeyes0 on 2007-01-31
I've never had any luck with Network Manager. However, if you want a connection to be managed by Network Manager, you have to comment it out of your /etc/network/interfaces file (use the command sudo gedit /etc/network/interfaces to edit the file).

---

### Post by gloscherrybomb on 2007-01-31
That doesn't really make snese though because my network manager works fine. That's not my problem.

---

### Post by gloscherrybomb on 2007-02-01
BUMP* Did above instructions now luck. Can I get wireless ligh ton at boot, or can i stop having to enter this terminal command?

---

