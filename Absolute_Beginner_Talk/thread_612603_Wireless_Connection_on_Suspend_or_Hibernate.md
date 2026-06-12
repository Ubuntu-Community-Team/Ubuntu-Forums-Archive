---
title: "Wireless Connection on Suspend or Hibernate"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by gkjohn on 2007-11-14
'm running Gutsy on a Lenovo 3000 G400 with a Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01) and using the wireless driver installed via the restricted driver management. It works fine except for when I wake from suspend/hibernate. The nm-applet purports that I am connected to the network but I cannot connect to the internet. I have tried:

1. Editing /etc/default/acpi-support to include:
```
# Add services to this list to stop them before suspend and restart them in
# the resume process.
STOP_SERVICES="networking"
but this does not work.
```

2. Invoking: 
```
sudo /etc/init.d/networking restart 
```
and stop and start variants but that does not work either.

3. Restarting X, that does not work.

The only fix is to restart/reboot the computer.

Is there a way around this problem?

Related to Wifi, my laptop has a toggle switch on the side that turns Wifi and Bluetooth on and off. I have tried toggling that on wake but it does not work either. Actually, that switch does not seem to work regardless of a suspend/hibernate. When off, the WiFi icon in nm-applet is still displayed but I cannot surf the net. It does not seem to pass on the state information to nm-applet. Similary, the Fn+F5 that is supposed to tunr WiFi on and off does not work but strangely, Fn+F6 works to toggle Bluetooth.

---

### Post by buellman on 2007-11-14
I have an IBM X31 with nearly the same problems.
If I normal start the X31 the FN+F5-combination does work. After suspend or hibernate the wlan works (lucky me) but the FN+F5-combination doesn't work. Sometimes I have no connection at all after suspend.
Then (maybe interessting for you) I have to unload
```
sudo rmmod ipw2100
```
and the load again
```
sudo modprobe ipw2100
```
the module for my card again but the FN+F5-combination doesn't work again.
When I then reboot the notebook FN+F5 does work again.

I tried the same as you
```
sudo /etc/init.d/networking restart
```
and
```
# Add services to this list to stop them before suspend and restart them in
# the resume process.
STOP_SERVICES="networking"
but this does not work.
```
but that doesn't help.

So I get wireless working after suspend with unloading and reloading the module but that is something that should work out of the box I think.

Greets. Buellman

---

### Post by gkjohn on 2007-11-14
Got it to work using these instructions:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fl](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fl)

Looks like the ndis method works best!

---

