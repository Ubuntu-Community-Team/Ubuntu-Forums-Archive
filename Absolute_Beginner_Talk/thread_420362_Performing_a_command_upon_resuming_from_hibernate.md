---
title: "Performing a command upon resuming from hibernate"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by orphzirra on 2007-04-23
My goal is to disable my Bluetooth device.  It has a rather annoying blinking blue light and I don't use Bluetooth for anything.  Now, I currently have root's crontab set to perform:

```
sudo hciconfig hci0 down

```

on reboot.  This works great.  However, upon hibernating and resuming, the Bluetooth device turns back on and I'm wondering if there's a way to prevent this and/or a better way to just disable Bluetooth entirely.  Many thanks.

---

### Post by mikeyphi on 2007-04-24
if its desperate!! you could uninstall the bluetooth packages through synaptic.

---

### Post by Austin_KW on 2007-04-24
Or just blacklist the drivers in /etc/modprobe.d/blacklist  so they can't load

---

### Post by orphzirra on 2007-05-01
Fixed! Upon reading the man page for hciconfig I was introduced to hcid.conf (/etc/bluetooth/hcid.conf).  The autoinit option was set to yes; therefore, when my laptop resumed hcid.conf initialized the device.  Quickly setting it to no solved the problem.

---

