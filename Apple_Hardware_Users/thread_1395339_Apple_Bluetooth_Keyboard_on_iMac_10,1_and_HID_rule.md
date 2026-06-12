---
title: "Apple Bluetooth Keyboard on iMac 10,1 and HID rules"
date: 2010-01-31
forum: Apple Hardware Users
---

### Post by Darrena on 2010-01-31
So my wife has a new iMac that she wants Linux on (She tried MacOS and got annoyed with it, I guess she is just used to Gnome) and I got everything working except now it doesn't detect a bluetooth adapter.

The Bluetooth Keyboard and Magic Mouse work (I built a custom kernel with the Magic Mouse driver) but none of the advanced features work because it seems to be stuck in HID mode.

Does anyone have a UDEV rule that will switch it to HCI mode or any idea on how to do this with Bluez 4.x?

Thanks!

---

### Post by linuxopjemac on 2010-02-01
I have no idea, but I read that the application Blueman can take care of a lot of bluetooth machines.

---

### Post by Darrena on 2010-02-01
> **linuxopjemac said:**
> I have no idea, but I read that the application Blueman can take care of a lot of bluetooth machines.

Unfortunately neither Blueman nor Gnome-Bluetooth see a Bluetooth adapter.   I suspect it is because the adapter is in HID mode.   I see some references to Bluez now starting based on a udev rule so I will take a look at those rules and see they fail to detect the module in this iMac.   If so I will try to get it working and submit a patch to Launchpad.

---

### Post by _mario_ on 2010-02-02
> **Darrena said:**
> Unfortunately neither Blueman nor Gnome-Bluetooth see a Bluetooth adapter. I suspect it is because the adapter is in HID mode. I see some references to Bluez now starting based on a udev rule so I will take a look at those rules and see they fail to detect the module in this iMac. If so I will try to get it working and submit a patch to Launchpad.

did you try?
```
sudo hciconfig hci0 reset
```

ciao,
Mario

---

### Post by Darrena on 2010-02-02
> **_mario_ said:**
> did you try?
```
sudo hciconfig hci0 reset
```

ciao,
Mario

Yep I tried that first but oddly it doesn't see that interface...  Bluez actually doesn't seem to think there is a Bluetooth device present so the udev rules never fire and start the service.

---

### Post by Stratosmacker on 2010-09-05
> **Darrena said:**
> Yep I tried that first but oddly it doesn't see that interface...  Bluez actually doesn't seem to think there is a Bluetooth device present so the udev rules never fire and start the service.

I have this same issue for the same computer. Did you ever find a solution?

---

### Post by Darrena on 2010-09-05
> **Stratosmacker said:**
> I have this same issue for the same computer. Did you ever find a solution?

No I wound up just plugging in a USB Bluetooth dongle I had floating around.

---

