---
title: "Bluetooth issue on a Latitude D630"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by mebu99 on 2008-03-23
Hello
I am trying add a bluetooth headset to my laptop.  It looks like the driver is installed correctly; however, when I browse and attempt to add the device I receive the enclosed error.  Any suggestions?

---

### Post by linuxwizard on 2008-03-23
On this page > [https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup) > look over Devices & Troubleshooting  see if it will help.

---

### Post by mebu99 on 2008-03-23
I went through the process of 
```
sudo apt-get install bluez-btsco
```
and 
```
sudo modprobe snd-bt-sco
```
I also edited /etc/bluetooth/hcid.conf  with the MAC address of my bluetooth headset.

I am still having issues, and have enclosed the error I am receiving.

---

### Post by mebu99 on 2008-03-24
^bump^

---

