---
title: "[SOLVED] Ralink RT73 woes"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by ByKeLaO on 2007-12-16
I finally got gutsy up and running, but I have no wireless internet connection. I ran ifconfig and it lists eth0, eth1 and lo but not wlan0!
I opened up the device manager and it recognised my card. So why doesn't it let me connect to the network?

PS I'm sorry if I seem short-tempered. I've been trying to get ubuntu running for about 10 hours solidly now and its really pissing me off. So much for it "working right out of the box"...:(

---

### Post by ByKeLaO on 2007-12-16
oK, after following these instructions:
[http://ubuntuforums.org/showthread.php?p=3671699#p%20ost3671699](http://ubuntuforums.org/showthread.php?p=3671699#p%20ost3671699)
I managed to list the available networks, but now it won't let me connect. How can I get a log or something to see what's going wrong?

---

### Post by ByKeLaO on 2007-12-16
bump

---

### Post by Gone fishing on 2007-12-16
Can you give a little more detail about the network you are trying to connect to. If it's an ad-hoc network for example you need to manually edit the /etc/network/interfaces file to add add-hoc network. Does your network use WEP etc?

---

### Post by ByKeLaO on 2007-12-16
Its a completely unsecure, unencrypted network. MAC address control is on, but it is set up correctly (and besides I have tested it when it is switched off).

I am trying to connect with a Belkin Wireless G USB Network adapter (with the RT73 chipset).

---

### Post by ByKeLaO on 2007-12-16
What driver am I meant to be using? rt73 or rt73usb?

---

### Post by Gone fishing on 2007-12-16
So it is an ad-hoc network you setup the network manually

administration > system > network on the wireless turn off roaming and setup manually  

then open /etc/network/interfaces as superuser an add the following

wireless-mode ad-hoc

Should work then - and yes I think the ad-hoc option should be added to the gui tool

---

### Post by Gone fishing on 2007-12-16
Use the driver that allowed it to list the networks then modify the interfaces file and all should be well and dandy.

---

### Post by ByKeLaO on 2007-12-16
No, its not ad-hoc. I'm trying to connect to a wireless router that has no encryption or anything. I can see the network in the list, but it won't let me connect to it. It just times out. What's causing it to do that?

---

### Post by ByKeLaO on 2007-12-16
I just found an error in user.log that might be helpful:

Every time I try to connect I get this:
dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason

---

### Post by Gone fishing on 2007-12-16
I found these:

[http://ubuntuforums.org/archive/index.php/t-178619.html](http://ubuntuforums.org/archive/index.php/t-178619.html)
[http://osdir.com/ml/network.networkmanager.devel/2006-06/msg00003.html?rfp=dta](http://osdir.com/ml/network.networkmanager.devel/2006-06/msg00003.html?rfp=dta)

It seems that the problem is the unencrypted network - might be easier to set up a simple WEP encryption

---

### Post by ByKeLaO on 2007-12-16
It didn't work with WEP encryption either.

This patch - [http://hostap.epitest.fi/bugz/show_bug.cgi?id=30](http://hostap.epitest.fi/bugz/show_bug.cgi?id=30)
How do I apply it when I have no internet connection !?!?!

---

### Post by Gone fishing on 2007-12-16
[http://security.ubuntu.com/ubuntu/pool/main/w/wpasupplicant/](http://security.ubuntu.com/ubuntu/pool/main/w/wpasupplicant/)

download the deb file stick on a flash?

---

### Post by ByKeLaO on 2007-12-16
It turns out the "patch" is the same as the version I had already installed. It didn't do anything, and I still can't connect to the network.
Jeez, I've had so many problems with Ubuntu I'm seriously considering using a different distro. or worse, sticking with Vista.
If anyone can shed some light onto the issue, that'd be awesome!

---

### Post by ByKeLaO on 2007-12-30
I managed to fix it. I just blacklisted every ralink driver and used ndiswrapper instead. I might post a tutorial if I get around to it.

---

