---
title: "Unable to blacklist WiFi BCM 4318"
date: 2006-07-23
forum: Absolute Beginner Talk
---

### Post by the7thlover on 2006-07-23
Hi 

Newbie and first post. trying to blacklist BCM4318 inuit wireless card on my laptop (compaq v2000) followed all the directions, of blacklisting in the blacklist files, but after rebooting i still see the eth1 wireless card in the networking and device manager.

Thanks

---

### Post by jjstwerff on 2006-07-23
Can you show the current contents of the file:

```
/etc/modprobe.d/blacklist
```

It should be:

```
blacklist bcm43xx
```

instead of just:

```
bcm43xx
```

By the way you know about the forum entry? :

[http://www.ubuntuforums.org/showthread.php?t=190177](http://www.ubuntuforums.org/showthread.php?t=190177)

On the other hand... are you sure that eth1 is connected to the wireless card or is it some other device...

---

### Post by the7thlover on 2006-07-24
Thanks for replying

-----start copy blacklist----

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

#blacklisting bcm4318
blacklist bcm43xx

-----end copy blacklist-----

Yes, i am aware of the other post, and i have followed all the instructions. However after a reboot I still see the eth1 (internal card) on the device manager and Network list (though disabled). I have even gone ahead and installed ndiswrapper, however it still did not work do i have uninstalled ndiswrapper for right now. Hardware has been checked and and it is confirmed bcm 4318. Using a compaq presario v2000.

Thanks in advance for your help.

---

### Post by Jagot on 2006-07-24
This works for me:

```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo rmmod bcm43xx
```

---

### Post by the7thlover on 2006-07-24
that did not work. It is still showing up in the device manager and networking. 

this is the device as reported by device manager
BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller

---

