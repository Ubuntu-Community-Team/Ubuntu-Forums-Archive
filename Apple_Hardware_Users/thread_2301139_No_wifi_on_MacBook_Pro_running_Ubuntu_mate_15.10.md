---
title: "No wifi on MacBook Pro running Ubuntu mate 15.10"
date: 2015-10-31
forum: Apple Hardware Users
---

### Post by dellboy56 on 2015-10-31
Hi I'm really having trouble with this problem I'm had a lot of distos I have or have used support my MacBook Pro 2010 wifi card now I don't know about Ubuntu but Ubuntu mate doesn't support this either my things a bcm4322 and I don't know why this isn't working for I'm got the requirements for my Mac to run mate but this just doesn't want to use the wifi which is really frustrating what do I do please help ps I have no Ethernet aswell so I need help urgently

---

### Post by Rapacity on 2015-11-02
Well, have you tried following this?

[http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)

I'm using regular 14.04 and also have a BCM4322 broadcom wireless adapter. I used the firmware-b43-installer. It works I just have to run these commands to get it working.

```
sudo modprobe -r b43 ssb 
sudo modprobe ssb 
sudo modprobe b43 
sudo killall wpa_supplicant
sudo rfkill unblock all
```

I hope that will get you started.

---

