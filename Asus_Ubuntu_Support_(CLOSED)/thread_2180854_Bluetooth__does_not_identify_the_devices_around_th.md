---
title: "Bluetooth  does not identify the devices around the computer. ubuntu 12.04"
date: 2013-10-14
forum: Asus Ubuntu Support (CLOSED)
---

### Post by jhon3 on 2013-10-14
Excuse me, the  bluetooth does not work, does not identify the devices around the  computer. I would appreciate you to help me.


Note that initially had both windows and ubuntu to use the bluetooth  should start Windows and activate bluetooth, reboot with ubuntu and  already served, but to restart ubuntu or suspension no longer served. I  thought doing the installation from scratch and installing ubuntu only  would work, but no.


When installing ubuntu ran the bluetooth, but when installing the wifi  driver wifi works but the bluetooth does not identify the  devices and keeps looking.

when i start ubuntu show this
[IMG]http://k42.kn3.net/9/C/7/9/0/F/8EC.jpg[/IMG]

Thanks for the advice you can give me. greetings.

rfkill show this

jhon@Minjhon2:~$ sudo rfkill list
0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

---

### Post by tgalati4 on 2013-10-15
What is the hardware?  Laptop or desktop?  Is Bluetooth built in?

I'm going to assume that this is an Asus laptop.  So what is the output of:

```
lsusb
```

Boot into BIOS and check the bluetooth settings--make sure that it is powered on.  Also check the BIOS Power Management settings and turn the Bluetooth power saving mode off.

Look through *lsmod* and post any bt*** related entries.

---

